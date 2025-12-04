# Image-Processing
Explorations in image processing and analysis using Python, NumPy, OpenCV, and Fourier-domain techniques. Includes frequency filtering, phase–amplitude analysis, sampling theory, interpolation, and geometric transformations.

# Image Processing & Analysis – Python Project

A collection of self-directed explorations in digital image processing, implemented using Python, NumPy, OpenCV, and Matplotlib.  
The project focuses on understanding how images behave in the frequency domain, how sampling affects reconstruction, and how geometric transformations can be implemented from scratch.

The repository includes modular Python code, visualizations, and explanations for each experiment.

---

##  Main Topics Covered

### **1. Frequency-Domain Analysis**
Understanding images not just in the spatial domain, but also through their spectral content.

Includes implementations of:
- 2D Discrete Fourier Transform (DFT)  
- Log-magnitude spectrum visualization  
- Low-pass frequency filtering  
- High-energy frequency selection (top-k magnitude)  
- Image reconstruction and MSE error trends  
- Insights on which frequencies matter most for natural images  

These experiments highlight how image structure is encoded in frequency components — low-frequency global shapes vs high-frequency details.

---

### **2. Phase vs Amplitude Experiments**
A deeper look at the role of phase in image reconstruction.

Includes:
- Extracting amplitude and phase of images  
- Swapping phase and amplitude between two images  
- Constructing hybrid images (self + other image)  
- Randomized amplitude or phase components  

**Key insight:**  
Phase contains most of the structural information of an image, while amplitude controls intensity and contrast.

---

### **3. Sampling Theory & Aliasing**
Hands-on demonstrations of sampling concepts.

Projects include:
- Synthesizing multi-frequency images  
- Visualizing aliasing in the frequency domain  
- Down-sampling and reconstructing signals  
- Understanding the Nyquist limit  
- Effects of sampling along x, y, and diagonal directions  

These experiments visually demonstrate how insufficient sampling creates overlapping spectra, distortion, and loss of detail.

---

### **4. Interpolation, Displacement & Rotation**
Implementing geometric transformations *from scratch* — without relying on OpenCV built-ins.

Includes:
- Bilinear interpolation implementation  
- Fractional pixel displacement  
- Cyclic (toroidal) image shifting  
- Manual 2D rotations around image center  
- Creating and applying binary masks  

These experiments reinforce how image geometry interacts with resampling and interpolation techniques.

---

##  Technologies Used

- **Python 3**
- **NumPy**
- **OpenCV**
- **Matplotlib**
- **Jupyter Notebook**

---

##  Running the Code

All can be run either in:
- **Jupyter Notebook**
- **Any Python IDE** (PyCharm / VSCode)

### Quick Access
[ Open code.ipynb](code.ipynb)

Environment requirements:
```bash
pip install numpy opencv-python matplotlib
