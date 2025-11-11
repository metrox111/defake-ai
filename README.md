# 🧠 DeFake-AI  
**Deepfake Detection and GAN Attribution using PyTorch, Gradio, and Explainable AI**

---

## 🧩 Overview
**DeFake-AI** is a deep learning system that detects StyleGAN-generated deepfakes and attributes them to specific GAN architectures (StyleGAN1, StyleGAN2, or StyleGAN3).  
It combines **ResNet18** for binary classification, **Dual EfficientNet-B0** for attribution, and **Grad-CAM** for explainability — all inside an interactive **Gradio** interface.

---

## ⚙️ Tech Stack
| Component | Technology |
|------------|-------------|
| Framework | PyTorch |
| Interface | Gradio |
| Explainability | Grad-CAM |
| Models | ResNet18, Dual EfficientNet-B0 |
| Dataset | StyleGAN-generated faces + Real images (CelebA-HQ) |

---

## 🧬 System Architecture

**Stages:**
1. **Preprocessing** – Resize, normalize, and extract features.  
2. **Classification (Binary Model)** – ResNet18 predicts *Real* or *Fake*.  
3. **Attribution & Explainability** – If fake, Dual EfficientNet-B0 attributes the GAN source and Grad-CAM generates heatmaps.
<img width="1600" height="602" alt="image" src="https://github.com/user-attachments/assets/98f8f937-5b47-4ae8-a3a7-cc51b05efb11" />

## 🧠 Model Architectures

### 🔹 Binary Detection Model (ResNet18)
This model classifies an image as **Real** or **Fake**.  
It’s based on a fine-tuned ResNet18 with dropout regularization for better generalization.

<img width="850" height="425" alt="image" src="https://github.com/user-attachments/assets/d8d92b3f-31b5-4156-9dde-0103ecf0ab89" />


---

### 🔹 Attribution Model (Dual EfficientNet-B0)
This dual-branch model identifies **which GAN (StyleGAN1/2/3)** generated a fake image.  
It processes both the RGB image and its FFT frequency spectrum through two EfficientNet-B0 branches, then fuses features for classification.

<img width="600" height="773" alt="image" src="https://github.com/user-attachments/assets/e41cbb0a-7141-406e-a777-7fd2126dcbb1" />


---

Each model is integrated with **Grad-CAM** for explainability, allowing visualization of which regions influenced the prediction.


---

## 📊 Results

### 🔸 Confusion Matrix – Binary Model
<img width="1200" height="900" alt="image" src="https://github.com/user-attachments/assets/8fd73633-2f43-41eb-b3f2-a99344dc4418" />


### 🔸 Confusion Matrix – Attribution Model
<img width="1159" height="1030" alt="image" src="https://github.com/user-attachments/assets/44749ee1-b28b-43ec-900f-5d90b4df8fb5" />


### 🔸 Classification Reports - Binary Model
<img width="711" height="318" alt="image" src="https://github.com/user-attachments/assets/deacd834-1afc-4849-9bbd-0330fd60015a" />


### 🔸 Classification Reports - Attribution Model
<img width="538" height="363" alt="image" src="https://github.com/user-attachments/assets/530678ab-f4f8-4c30-b60b-1190fe3d483f" />

---

## 🎨 Explainability (Grad-CAM)

Grad-CAM visualizations highlight image regions most influential to the model’s decision.

| Binary Detection | GAN Attribution |
|------------------|----------------|
|<img width="1600" height="533" alt="image" src="https://github.com/user-attachments/assets/215081ca-d466-48a4-8aaa-fabf8f03493a" /> |<img width="1150" height="636" alt="image" src="https://github.com/user-attachments/assets/56c9a080-6382-47bf-84a6-cdf89ea9e917" />
 |

> **Red regions** = high influence  
> **Blue regions** = low influence  

---

## 🖥️ Gradio Interface

| Upload | Analysis Result |
|--------|-----------------|
| ![Upload UI]<img width="1285" height="553" alt="image" src="https://github.com/user-attachments/assets/8aebcff7-4f25-49ff-bbbe-385a939447c3" /> | ![Results UI]<img width="1203" height="606" alt="image" src="https://github.com/user-attachments/assets/c8755c01-9d8d-4634-ae51-7b7a678b0647" />
 |

**How it works:**
1. Upload an image (JPG/PNG).  
2. The model predicts **Real** or **Fake**.  
3. If Fake → performs **GAN attribution** (StyleGAN1/2/3).  
4. Grad-CAM visualizes the model’s decision basis.

---

## 🧪 Training Scripts

All training notebooks are available under `/training/`.

| Script | Description |
|--------|-------------|
| `train_binary_resnet18.ipynb` | Trains the ResNet18 binary classifier |
| `train_dual_efficientnet.ipynb` | Trains the Dual EfficientNet-B0 attribution model |

---

## 📦 Model Weights

Model files are too large to include in the repo.  
Download them from the link below and place inside the `/models/` folder.

| Model | Description | Download |
|--------|--------------|-----------|
| `resnet18_binary_model.pth` | Binary classifier (Real vs Fake) | [Google Drive Link](https://drive.google.com/file/d/1fXxWkC5A3Tn01z79nYbRv86dBBoJhFQi/view?usp=sharing) |
| `attribution_efficientnetb0.pth` | GAN attribution (StyleGAN1/2/3) | [Google Drive Link](https://drive.google.com/file/d/12zjMmUd9pUilxTQFLJrac7qoFFa8rPlY/view?usp=sharing) |

---

## 🧩 Future Scope
- Extend to **video-based deepfake detection**  
- Integrate **LIME / SHAP** for richer interpretability  
- Optimize for **real-time inference** on edge devices  
- Add **web deployment** via lightweight backend
- Diversify the dataset for trainning (include sources from other GANs and even diffusion models)
---

## 👨‍💻 Team
| Name | Role |
|------|------|
| **[Piyush]** | Model Architecture & Integration |
| **[Sanjana]** | Dataset & Training |
| **[Suhana]** | UI & Explainability |

---




