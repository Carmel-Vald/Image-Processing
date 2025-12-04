
# Image Processing – Project 2


##  Topics

### ** Gaussian Pyramid & Laplacian Pyramid**
- Construction of multi-resolution pyramids  
- Downsampling & upsampling  
- Gaussian blurring and scale-space  
- Difference-of-Gaussians (DoG)  
- Understanding how pyramid levels affect edges, noise, and fine vs coarse structures  

All pyramid functions are implemented manually as required.

---

### ** Harris Corner Detector**
- Gradient calculation using Sobel filters  
- Structure tensor computation  
- Harris response formula  
- Thresholding  
- Non-maximum suppression (NMS)  
- Comparison to OpenCV’s corner detector  

Outputs include response heatmaps and keypoint overlay visualizations.

---

### ** Feature Matching**
- Extracting descriptors around detected corners  
- Similarity metrics (SSD / NCC)  
- Nearest-neighbor matching  
- Ratio test to reject ambiguous matches  
- Plotting the matched feature pairs  

A clean pipeline combining your own Harris detector + matching.

---

### ** RANSAC & Homography Estimation**
- Robust homography estimation using RANSAC  
- Sampling random match subsets  
- Computing inliers  
- Homography via least-squares / SVD  
- Comparison to OpenCV’s `findHomography`  

Plots include inliers vs outliers and alignment quality.

---

### ** Image Warping & Panorama Stitching**
- Computing the warp of the second image into the first image's coordinate frame  
- Backward mapping and interpolation  
- Blending approaches  
- Final panorama creation  

This part integrates all earlier stages into a full panorama pipeline.

---

##  Technologies Used
- **Python 3**
- **NumPy**
- **Matplotlib**
- **OpenCV**
- **SciPy**
- **Jupyter Notebook**

- ##  Quick Access

[ **Open code.ipynb**](code.ipynb)
