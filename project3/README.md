
# Project 3 - Sampling, Aliasing & Image Restoration

## major topics:

1. **Sampling & Aliasing** in space and time using a real video sequence  
2. **Image Restoration with a Learned Regularization Parameter** using block-DCT distortion and L2 recovery

The work includes Python code, visualizations, analyses, and explanations strictly following the requirements of the official assignment instructions.  
Report and implementation are based on:  
- Submitted PDF report: *Wet 3 exc.* :contentReference[oaicite:2]{index=2}  
- Official assignment handout: *Computer Homework 3* :contentReference[oaicite:3]{index=3}  

---

## Goals

- Understand spatial and temporal sampling and the aliasing artifacts they introduce.  
- Analyze sampling effects on real video content (Dire Straits – *Brothers in Arms*).  
- Implement Zero-Order Hold temporal reconstruction.  
- Apply the block-DCT + quantization distortion model inspired by JPEG.  
- Build block matrices, Kronecker products, and Toeplitz convolution operators.  
- Learn a regularization parameter λ that minimizes empirical loss.  
- Restore distorted images using a closed-form L2 solution.  
- Compare restoration quality on synthetic vs natural images.

---

## Repository Contents

- **`Wet3_code.ipynb`**  
  Main Jupyter notebook implementing all tasks in Homework 3.

- **`hw3_206489338_211409867.pdf`**  
  Full written report containing all visualizations and explanations.

- **`my_data/`**  
  Locally captured or processed files (e.g., sampled videos, restored outputs).

---

## Main Experiments

### 1. Spatial Sampling & Aliasing (Video Frames)

#### 1.a Spatial Sampling
- Extract the frame at **50s** from the song *Brothers in Arms*.  
- Rotate the frame to align the guitar neck horizontally.  
- Visualize:
  - Rotated image  
  - 400th column intensity profile  
  - Number of visible guitar string shadows  
- Perform **row sampling** using interval Δy.  
- Interpolate back to original resolution using **bilinear interpolation** (`cv2.resize`).  
- Compare pre/post-sampling intensity profiles and discuss aliasing.

#### 1.b Temporal Sampling
- Analyze the pendulum frequency in the 10–20s segment of the video.  
- Sample frames using interval Δp.  
- Reconstruct time sequence using **Zero-Order Hold** (frame repetition).  
- Export sampled video (same duration & FPS).  
- Compare motion stability and derive the minimum Δp that avoids temporal aliasing.

---

### 2. Image Restoration with a Learned Parameter

#### 2.a Distortion Model (Block-DCT + Quantization)
- Construct the **8×8 DCT matrix H**.  
- Assemble a **block-diagonal DCT operator** for 32×32 images.  
- Apply JPEG-like quantization using matrix **Q**.  
- Distort all images in:
  - **Training set** (for learning λ)  
  - **Test set** (for evaluation)

Visualizations include distorted feathers image, synthetic image, and natural image (as shown in the report). :contentReference[oaicite:4]{index=4}

#### 2.b Optimization: Learning λ
- Formulate the L2 restoration objective:  

 <img src="https://render.githubusercontent.com/render/math?math=\min_X\|Y-H^T X H\|_2^2+\lambda\|DX\|_2^2">


  where **D** is the Laplacian operation matrix.  
- Convert 2D convolution to Toeplitz operation using the provided `to_operation` function.  
- Compute empirical loss across the training set.  
- Search λ across log-scale values and refine around the minimum.  
- Plot loss vs λ and discuss stability.

#### 2.c Restoration with Optimal λ
- Use closed-form solution:  

<img src="https://render.githubusercontent.com/render/math?math=\hat{X}_{cs}=(\lambda D^T D+I)^{-1}(H\otimes H)Y_{cs}">


- Display:
  - Original image  
  - Distorted image  
  - Restored image  
- Compare behavior of **synthetic vs natural scenes**:
  - Synthetic: clearer edges → better restoration  
  - Natural: textures → higher Err2 and detail loss due to smoothing (as shown in report) :contentReference[oaicite:5]{index=5}

---

## Key Insights

- **Spatial aliasing** reduces the number of visible guitar string shadows due to undersampling.  
- **Temporal aliasing** makes the pendulum appear to move incorrectly; avoiding aliasing requires choosing Δp according to the scene’s frequency.  
- **Higher quantization levels** yield lower distortion and smoother convergence (seen in the RGB channel experiment) :contentReference[oaicite:6]{index=6}.  
- **L2 denoising** improves smoothness but may blur fine natural textures.  
- **Learned λ** balances noise reduction and detail preservation—its optimal value depends on image complexity.

---

## How to Run

1. Open **`Wet3_code.ipynb`** in Jupyter Notebook or VS Code.  
2. Install dependencies:

   ```bash
   pip install numpy matplotlib opencv-python scipy
