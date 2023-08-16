**Goals:**
- Reducing data dimensions so it can be plotted $\rightarrow$ ==PCA-plot==.
- Tells us which variable is most valuable for clustering.

**Steps:**
1. Shift the data so the center (data points minus the means) is on top of the origin.
2. Find a fitted line that goes through the origin.
	- Minimize the distance of the line and the data points.
	- Or map the data points to the line and maximize the mapped points' distances from the origin (sum of squared distances $\rightarrow$ SS).
3. This fitted line is called ==Principal Component 1 (PC1)==.
	- In case of 2 dimensions, if the slope (==linear combination== of the variables) of PC1 is small, then the data is mostly spread out along the x-axis (1st variable). 
	- If slope = 0.25, then adding up 4 part X and 1 part Y gives us a 4.12 long vector (Pythagorean-theorem). Scaling the values so the vector length is 1 $\rightarrow$ X = 0.97, Y = 0.242
	- The unit long vector is the ==Eigenvector==, X and Y are the ==loading scores==.
	- PC1 ==Eigenvalue== = $SS(PC1)/(n-1)$
	- PC1 ==Singular value== = $\sqrt{SS(PC1)}$
4. PC2 is orthogonal to PC1
	- Scaled unit vector: X = -0.242, Y = 0.97
5. Make PC1 and PC2 the new axis.
	- The mapped values gives us the place of the data points in the PCA-plot

**Notes:**
- The eigenvalues are the variances of the PCs
- By summing up the variance, we can calculate that how much variation each PC accounts for $\rightarrow$ ==Scree-plot==: graphical representation of PC variations
- ==Normalizing the data points==: $Z = \frac{X-X_{mean}}{SD}=\frac{X-X_{mean}}{\sqrt{Var(X)}}$
- Deciding which components to use:
	- Smallest number of components that together hold 80-90% of the total variance.
	- Kaiser criterion: Components with greater variance than the mean of the variances.

**Math background:**
==Covariance matrix== of 2 variables:
$$
C=
\begin{bmatrix}  
Var(X) & Cov(Y,X) \\  
Cov(X,Y) & Var(Y) \\
\end{bmatrix}
$$
$$
Var(X)=\frac{1}{n-1}\sum_{i=1}^{n}(X_i-X_{mean})^2
$$

^eee9be

$$
Cov(X,Y)=\frac{1}{n-1}\sum_{i=1}^{n}(X_i-X_{mean})(Y_i-Y_{mean})=Cov(Y,X)
$$

^a25bc2

==Eigenvalues==:
$$
det|C-\lambda I|=0
$$
$$
det
\begin{vmatrix}  
Var(X)-\lambda & Cov(Y,X) \\  
Cov(X,Y) & Var(Y)-\lambda \\
\end{vmatrix}
=0
$$
$$
(Var(X)-\lambda)(Var(Y)-\lambda)-Cov(X,Y)Cov(Y,X)=0
$$
$$
(Var(X)-\lambda)(Var(Y)-\lambda)-Cov(X,Y)^2=0
$$
==Eigenvectors==:
$$
C*
\begin{bmatrix}  
v_x \\  
v_y \\
\end{bmatrix}
= \lambda * \begin{bmatrix}  
v_x \\  
v_y \\
\end{bmatrix}
$$
This gives us two equations and a result like this: $y=1.37x$. By choosing $x=1$, we have one of the eigenvectors (before making it a unit vector):
$$
\begin{bmatrix}  
1 \\  
1.37 \\
\end{bmatrix}
$$

==Mapping data to the new base:==
$$
Data * 
\begin{bmatrix}  
v_{1x} & v_{2x} \\  
v_{1y} & v_{2y} \\
\end{bmatrix}
=
\begin{bmatrix}  
PC1 & PC2
\end{bmatrix}
$$