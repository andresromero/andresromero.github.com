---
layout: post
title: People you might know
---

The idea here is to explain how to use *MapReduce* to process a social network a propose friendship recommendations according to the number of mutual friends.

This problem appeared recently in a homework for the Stanford computer science course CS246. 

The required dataset can be downloaded [here](http://snap.stanford.edu/class/cs246-data/hw1q1.zip). This input file contains the adjacency list of a graph of about 50,000 nodes.  All lines obey the following format:

`<USER><TAB><Friends>`

Where `<USER>` is a unique integer ID which corresponds to a unique user and `<FRIENDS>` is a comma separated list of unique ID's corresponding to the friends of the user with the unique ID `<USER>`. Friendships are mutual, if $$A$$ is friend with $$B$$, then $$B$$ is also friend with $$A$$.

The idea here is to develop an algorithm such that for each user $$U$$, the algorithm recommends $$N=10$$ users who are not already friends with $$U$$, but have the most common number of mutual friends with him/her. The algorithm should give one line per user in the following format:

`<USER><TAB><Recommendations>`,

where `<USER>` is a unique ID correponding to a user and `<Recommendations>` is a comma separated list of unique ID's corresponding to the algorithm's recommendations of people that `<USER>` might know, ordered in decreasing number of mutual friends.

Using *MapReduce* this problem can be easily solved using the following procedure:

## The mapping part

* For each line in the file the algorithm gets the `<USER>` ID and the list of friends.

* All the pair combinations of friends are calculated and printed at the output one by one. We also print every pair formed by each friend and the `<USER>` ID. To avoid ambiguities, 
pair tuples are ordered in increasing order. An additional field **friendFlag** is appended at the end. For all tuples formed by `<USER>` and one of its friends **friendFlag**$$=1$$, for the rest of the tuples (formed by the two element combinations of `<USER>`'s friends list) this value is zero.

To exemplify this solution, it is a good idea to test it first for an small adjacency list example:

{% highlight bash%}
0    2,3,4
1    3
2    0,4
3    0,1,4
4    0,2,3
{% endhighlight %}

The following Python script (`map_friends_rec.py`) implements the mapping part:

{% highlight python%}
#!/usr/bin/env python2
# map_friends_rec.py

#Map task for the Friend recommendation problem

import itertools
import sys

# input comes from STDIN (standard input)
for line in sys.stdin:
    # remove leading and trailing whitespace
    line = line.strip()
    line = line.split("\t")
    key = int(line[0])
    if len(line)>1:
        friends = line[1]
        if friends!='':
            friends = line[1].split(",")
            friends = sorted(map(int,friends))
            for friend in friends:
                pair = tuple(sorted([key,friend]))
                pair = ','.join(map(str,pair))
                print pair,"\t",1
            for pair in itertools.combinations(friends,2):
                pair = ','.join(map(str,pair))
                print pair,"\t",0
{% endhighlight %}

This script is called using the proposed test as:
{% highlight bash%}
cat test | ./map_friends_rec.py
{% endhighlight %}

which produces the following output:
{% highlight bash%}
0,2     1
0,3     1
0,4     1
2,3     0
2,4     0
3,4     0
1,3     1
0,2     1
2,4     1
0,4     0
0,3     1
1,3     1
3,4     1
0,1     0
0,4     0
1,4     0
0,4     1
2,4     1
3,4     1
0,2     0
0,3     0
2,3     0
{% endhighlight %}


## The reducer part

At this part what we want is to group all the repeated keys an increment a counter that indicates the number of mutual friends each pair of people haves. Initially we are going to suppose that people doesn't know each other, but we are going to recover the **friendFlag** to know if a connection between two people already exists in the graph.

Iterating line by line we are going to recover the *key* (formed by a pair of individuals) `(k1,k2)` and the value of **friendFlag**. Once we have both keys, we append them to a dictionary `users` using the defined `addPair` function which is called twice (interchanging the order of the keys `k1`$$\leftrightarrow$$`k2`). What this function does is to append the key `k1` to the dictionary if it doesn't exist. A different dictionary is created at `users[k1]`, this dictionary holds all the recommendations (and their counters) for user `k1`. In other words, each term inside the `users` dictionary maps to a different dictionary that holds the recommendations for each one of the users. The key `k2` is used inside these individual dictionaries to help recognizing the number of mutual friends between users `k1` and `k2`. Two values are stored inside the dictionary entry `users[k1][k2]`, the first one is the **counter** and the second one is a boolean flag indicating if both users are already friends. If **friendFlag**$$=1$$ the counter inside `users[k1][k2]` is not incremented.

The complete Python code for the reducer is the following:

{% highlight python%}
#!/usr/bin/env python2

#Reduce task for the Friend recommendation problem

import itertools
import sys

n_rec = 10

def addPair(users,k1,k2,friendFlag):
    if friendFlag==1:
        friendFlag = True
    else:
        friendFlag = False

    if k1 not in users:
        users[k1] = {}
        users[k1][k2] = [1,False]
    else:
        if k2 in users[k1]:
            users[k1][k2][0] += 1            
        else:
            users[k1][k2] = [1,False]
    if friendFlag==True:
        users[k1][k2][0] -= 1
        users[k1][k2][1] = True



# input comes from STDIN (standard input)
users = {}

for line in sys.stdin:
    # remove leading and trailing whitespace
    line = line.strip()
    line = line.split("\t")
    key = tuple(map(int,line[0].strip().split(",")))
    friendFlag = int(line[1])
    k1,k2 = key
    addPair(users,k1,k2,friendFlag)
    addPair(users,k2,k1,friendFlag)

for k1 in users.keys():
    recommendations = []
    for k2 in users[k1].keys():
        n,flag = users[k1][k2]
        if flag==False:
            recommendations.append((k2,n))
    recommendations = sorted(recommendations,key=lambda x: x[0])
    recommendations = sorted(recommendations,key=lambda x: x[1])
    if len(recommendations)>0:
        recommendations = list(map(str,zip(*recommendations)[0]))
        print k1,"\t",','.join(recommendations[:n_rec])
{% endhighlight %}

And to test it we use the following command
{% highlight bash%}
cat test | ./map_friends_rec.py | ./reduce_friends_rec.py
{% endhighlight %}

producing

{% highlight bash%}
0     1
1     0,4
2     3
3     2
4     1
{% endhighlight %}

This means that user $$0$$ gets the recommendation to add user number $$1$$, user number $$1$$ gets the recommendation to join users $$0$$ and $$4$$ and so on.


## Map and collect

On a real Hadoop implementation, the input file would be distributed within the computing nodes. The output of the mapping program should be collected before transmission to reduce the overload on the network. The function used for this purpose would be very similar to the function used at the reducer.

## Results for the homework dataset

Using the homework dataset, and the user keys IDs 924,8941,8942,9019,9020,9021,9022,9990,9992 and 9993 the friend recommendations would be:

{% highlight bash%}
924      439,2409,6995,11860,15416,43748,45881
8941     8940,8943,8944
8942     8940,8943,8944,8939
9019     317,9023,9022
9020     317,9023,9016,9017,9022,9021
9021     317,9023,9016,9017,9022,9020
9022     317,9016,9017,9023,9019,9020,9021
9990     13134,13478,13877,34299,34485,34642,37941
9992     9991,35667,9987,9989
9993     13134,13478,13877,34299,34485,34642,37941,9991
{% endhighlight %}

