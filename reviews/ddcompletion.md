# Deep Depth Completion of a Single RGB-D Image

**Problem**

Filling holes in a consistent manner of the depth channel of RGBD images obtained using standard RGBD sensors.

**Key points**

1. Authors propose using surface normals and occlusion boundaries as intermediate representations for regressing depth from RGB.
2. Empirically show that surface normals are better obtained using just RGB and not RGBD, using all the pixels as opposed to just observed or unobserved pixels.
3. Do a final optimization with the obtained surface normal and occlusion boundary using the incomplete depth as a regularization. Use a linear approximation to optimize the final error term using sparse Cholesky factorization.

**Results**

1. Great results in depth inpainting.
2. Great results in direct depth estimation.

**Notes**

1. Decoupling of depth estimation from surface normal estimation presenting an effective representation for depth prediction. 
2. No comment on other kind of data and how generalizable the method is.