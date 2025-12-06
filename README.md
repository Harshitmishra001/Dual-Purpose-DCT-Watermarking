# A Dual-Purpose DCT Watermarking Framework for Robust Copyright Protection and Fragile Tamper Localisation

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Framework](https://img.shields.io/badge/Framework-DCT-green)](https://github.com/topics/watermarking)

This repository contains the official source code and experimental data for the manuscript **"A Dual-Purpose DCT Watermarking Framework for Robust Copyright Protection and Fragile Tamper Localisation"**, submitted to *The Visual Computer* (Springer Nature).

---

## 📄 Abstract

Digital watermarking is essential for multimedia security, serving two primary goals: robust copyright protection and fragile content authentication.  
This paper introduces a blind, hybrid Discrete Cosine Transform (DCT)-based watermarking framework that operates exclusively in the luminance (Y) channel of the YCbCr colour space. By preserving chrominance channels, the method maintains colour fidelity while embedding dual watermarks for security.

The robust component modulates low-frequency AC coefficients to withstand common signal processing attacks, supported by a novel **Multi-Dimensional Synchronisation Search** that counters geometric distortions such as rotation and scaling.

The fragile component employs an **AES-encrypted SHA-256 hash**, embedded via an **Iterative LSB Stabilisation** process that ensures convergence between the embedded signature and block content.

The framework achieves high imperceptibility with an average PSNR of **37.62 dB** and SSIM of **0.965** on the Kodak dataset. Under an expanded suite of **13 attacks**, including StirMark geometric distortions, the robust watermark attains an overall NC of **0.70**, with strong performance under rotation (NC ≈ 0.79) and aspect ratio modifications (NC ≈ 0.78).  
The fragile watermark demonstrates near-perfect tamper localisation precision (**0.997**) and an F1-score of **0.843**.

---

## 🚀 Key Features

* **Dual-Layer Embedding:**  
  Simultaneous embedding of a robust copyright mark (ECC-encoded) and a fragile authentication signature (AES-encrypted) within the same `8×8` DCT blocks.

* **Geometric Resilience:**  
  Features a **Synchronization Search Module** to recover watermarks from affine and projective transformations, including Rotation (`1°`), Scaling, and Aspect Ratio changes.

* **Cryptographic Security:**  
  Utilizes AES-128 encryption in the fragile layer to prevent *collage* and *vector quantization* forgery attacks.

* **High Fidelity:**  
  Operates strictly in the Y-channel to preserve color information (achieving **PSNR ≈ 37.6 dB**).

---

## 🛠️ Installation & Setup

### **Prerequisites**
- Python 3.8 or higher  
- pip package manager  

---

### **1. Clone the Repository**

```bash
git clone https://github.com/YOUR_USERNAME/Dual-Purpose-DCT-Watermarking.git
cd Dual-Purpose-DCT-Watermarking
```

---

### **2. Install Dependencies**

```bash
pip install -r requirements.txt
```

---

### **3. Download Dataset**

This framework uses the **Kodak Lossless True Color Image Suite**.

Download the PNG images from:  
http://r0k.us/graphics/kodak/

Then place all **24 PNG images** into:

```
archive/
```

---

## 💻 Usage

To run the complete experimental pipeline (Embedding → Attacks → Extraction → Evaluation):

```bash
Run the code in main.ipynb
```

### **This script performs the following:**

- Embeds the robust and fragile watermarks into all images in `archive/`.
- Simulates **13 attacks**, including:
  - **Signal Processing:**  
    JPEG 30/70, Gaussian Noise, Blurring  
  - **StirMark Geometry:**  
    Rotation, Shearing, Scaling, Aspect Ratio, Perspective  
  - **Tampering:**  
    Cropping attacks
- Recovers the watermark using the **Synchronization Search** module.
- Generates performance metrics:  
  **NC, BER, PSNR, SSIM, F1-Score**
- Produces the **LaTeX-formatted results tables** used in the manuscript.

---

## 📊 Performance Highlights

| Attack Type                | Robust NC | Fragile Precision | Recovery Status       |
|---------------------------|-----------|-------------------|-----------------------|
| Rotation (`1°`)           | 0.789     | 1.000             | ✅ Success (Sync)     |
| Aspect Ratio (0.9×)       | 0.782     | 1.000             | ✅ Success (Sync)     |
| Perspective               | 0.779     | 1.000             | ✅ Success (Sync)     |
| JPEG (Q=70)               | 0.775     | 1.000             | ✅ Success (Robust)   |
| Cropping (25%)            | 0.603     | 0.956             | ✅ Localisation OK    |

---

## 🔗 Citation

If you use this code or framework in your research, please cite:

```bibtex
@article{Mishra2025DualPurpose,
  title={A Dual-Purpose DCT Watermarking Framework for Robust Copyright Protection and Fragile Tamper Localisation},
  author={Mishra, Harshit and Lone, Mohd Rafi and Sharma, Ajay and Tyagi, Praveen Kumar},
  journal={The Visual Computer},
  year={2025},
  publisher={Springer}
}
```

---

## 📜 License

This project is licensed under the **MIT License**.  
See `LICENSE` for details.

---

## 📦 Requirements (`requirements.txt`)

```text
numpy>=1.21.0
opencv-python>=4.5.0
matplotlib>=3.4.0
scikit-image>=0.18.0
scikit-learn>=1.0.0
pycryptodome>=3.10.0
reedsolo>=1.5.4
```
