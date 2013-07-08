---
layout: post
title: Gaussian Color Spaces
---
Image formation implies physical measurements over the spectral, spatial and time dimensions. Gaussian color models are a new theory of color measurement, they are an extension of the Gaussian derivative framework (scale-space theory) to the spatio-spectral domain. One of the most important achievements in scale-space theory is the remark that Gaussian shapes prevent the creation of extra details on higher scale images (i.e. lower resolution). Gaussians offer a general probe for spatio-spectral differential quotients. Let $$E(\lambda)$$ be the spectral energy distribution of light, it is a function of $$\lambda$$, which denotes the wavelength. Let now $$G(\lambda_0,\sigma_\lambda)$$ be a Gaussian kernel of spectral scale $$\sigma_\lambda$$ and positioned at $$\lambda_0$$. The spectral energy distribution $$E(\lambda)$$ may be approximate by the Taylor expansion at $$\lambda_0$$

$$
\begin{equation}
    E(\lambda) = E^{\lambda_0} + \lambda E_\lambda^{\lambda_0} + \frac{1}{2} \lambda^2 E_{\lambda \lambda}^{\lambda_0} + \cdots
\end{equation}
$$

Assuming measurements of the spectral energy distribution are made with a weighted integration over the spectrum we have

$$
\begin{equation}
    E^{\sigma_\lambda} = E^{\lambda_0,\sigma_\lambda} + \lambda E_\lambda^{\lambda_0,\sigma_\lambda} + \frac{1}{2} \lambda^2 E_{\lambda \lambda}^{\lambda_0,\sigma_\lambda} + \cdots
\end{equation}
$$

where $$E^{\lambda_0,\sigma_\lambda} = \int E(\lambda) G(\lambda;\lambda_0,\sigma_\lambda)d\lambda$$ measures the spectral intensity. Gaussian color models measure the the coefficients $$E^{\lambda_0,\sigma_\lambda}$$,$$E_\lambda^{\lambda_0,\sigma_\lambda}$$ and $$E_{\lambda \lambda}^{\lambda_0,\sigma_\lambda}$$ in the Taylor expansion of the Gaussian weighted spectral energy distribution at $$\lambda_0$$ with the spectral aperture (scale) $$\sigma_\lambda$$.

Spatial information can be introduced to the model yielding a Taylor expansion at wavelength $$\lambda_0$$ and coordinates $$\textbf{x}=(x,y)$$. The result of this is the exploration of an energy density volume in a spatio-spectral space

$$\begin{equation}
    E(\lambda,\textbf{x}) = E + \left(\begin{array}{c} \textbf{x} \\ \lambda \end{array} \right)^T \left[ \begin{array}{c} E_\textbf{x} \\ E_\lambda \end{array} \right] + \frac{1}{2} \left(\begin{array}{c} \textbf{x} \\ \lambda \end{array} \right)^T \left[ \begin{array}{cc} E_\textbf{xx} & E_{\textbf{x}\lambda} \\ E_{\lambda \textbf{x}} & E_{\lambda \lambda} \end{array} \right] \left(\begin{array}{c} \textbf{x} \\ \lambda \end{array} \right) + \cdots,
\end{equation}
$$

where $$E_{\lambda^m \textbf{x}^n}(\lambda,\textbf{x}) = E(\lambda,\textbf{x}) * G_{\lambda^m,\textbf{x}^n}(\lambda,\textbf{x};\sigma_\lambda,\sigma_\textbf{x})$$ is the $$m$$-th differentiation with respect to $$\lambda$$ (spectral differentiation) and the $$n$$-th with respect to $$\textbf{x}$$ (spatial differentiation).

<!--  \begin{figure}[tb]
    \begin{center}
        \includegraphics[height=0.20\textheight]{./figures/gaussianColorsModels.pdf}
    \end{center}
    \caption{Gaussian color model spectral derivative responses $$E,E_\lambda$$ and $$E_{\lambda \lambda}$$.}
    \label{fig:gaussianColorModels}
\end{figure} -->

It is safe to assume that camera sensitivities approximate Gaussian functions around the red, green, and blue areas of the visible spectrum. An approximation of the Gaussian color model is given by the opponent color spaces. Here, the brightness or intensity channel $$I = R+G+B$$ can be regarded as a Gaussian-weighted spectral response, the yellow-blue channel $$YB=R+G-2B$$ approximates the first-order spectral derivative because it results from comparing one half of the spectrum (around the blue color) with the other half (around yellow), the red-green channel $$RG=R-2G+B$$ can be interpreted as a second-order derivative which compares the center of the spectrum with the extremes (in the visual bandwidth). The responses of the $$E,E_\lambda$$ and $$E_{\lambda \lambda}$$ responses are shown in Figure~\ref{fig:gaussianColorModels}. The opponent color interpretation of the Gaussian color model is then expressed as

$$\begin{equation}
    \left[ \begin{array}{c}
        \hat{E} \\
        \hat{E}_\lambda \\
         \hat{E}_{\lambda \lambda} 
    \end{array} \right] = \frac{1}{3} \left( \begin{array}{ccc} 
        1 & 1 & 1 \\
        1 & 1 & -2 \\
        1 & -2 & 1 
    \end{array}\right) \left[ \begin{array}{c}  R \\ G \\ B \end{array} \right].
\end{equation}
$$

For calibrated cameras, the **XYZ** responses are known and the Gaussian basis functions are estimated with higher precision. A linearized **RGB** camera which approximates the CIE 1964 **XYZ** basis for colorimetry by the following linear transform

$$\begin{equation}
    \left[ \begin{array}{c}
        \hat{X} \\
        \hat{Y} \\
         \hat{Z} 
    \end{array} \right] = \left( \begin{array}{ccc} 
        0.62 & 0.11 & 0.19 \\
        0.3 & 0.56 & 0.05 \\
        -0.01 & 0.03 & 1.11 
    \end{array}\right) \left[ \begin{array}{c}  R \\ G \\ B \end{array} \right],
    \label{eq:XYZcolorsystem}
\end{equation}
$$

and the best linear transform from the \emph{XYZ} system to the Gaussian color model is

$$\begin{equation}
    \left[ \begin{array}{c}
        \hat{E} \\
        \hat{E}_\lambda \\
         \hat{E}_{\lambda \lambda} 
    \end{array} \right] = \left( \begin{array}{ccc} 
        -0.48 & 1.2 & 0.28 \\
        0.48 & 0 & -0.4 \\
        1.18 & -1.3 & 0 
    \end{array}\right) \left[ \begin{array}{c}  \hat{X} \\ \hat{Y} \\ \hat{Z} \end{array} \right]
    \label{eq:XYZgaussianColor}
\end{equation}
$$

the product of the transformation matrices in equations (\ref{eq:XYZcolorsystem}) and (\ref{eq:XYZgaussianColor}) finally gives

$$\begin{equation}
    \left[ \begin{array}{c}
        \hat{E} \\
        \hat{E}_\lambda \\
         \hat{E}_{\lambda \lambda} 
    \end{array} \right] = \left( \begin{array}{ccc} 
        0.06 & 0.63 & 0.27 \\
        0.3 & 0.04 & -0.35 \\
        0.34 & -0.6 & 0.17 
    \end{array}\right) \left[ \begin{array}{c}  R \\ G \\ B \end{array} \right].
\end{equation}
$$