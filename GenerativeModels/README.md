# 🌿 PL-LDGAN: Hybrid Latent Diffusion + GAN for Potato Leaf Generation

PL-LDGAN is a hybrid generative framework combining:
✅ Autoencoder (AE) Reconstruction
✅ KL Regularization (Latent Stability)
✅ Latent Diffusion (Noise Prediction)
✅ PatchGAN Adversarial Learning

It generates high-quality synthetic potato leaf images for:
🍂 Early Blight
🍁 Late Blight
🌱 Healthy

# Step-1 Organise Dataset as below
POTATODATASET/
│

├── Early_blight/
│   ├── img1.jpg
│   ├── img2.jpg
│   └── ...
│

├── Late_blight/
│   ├── img1.jpg
│   └── ...
│

└── Healthy/
    ├── img1.jpg
    └── ...

Train separately for:
Early_blight
Late_blight
Healthy
This results in three trained PL-LDGAN models, one per class.

# Step-2 Environment Setup
Install Dependencies
pip install torch torchvision tqdm pillow
Recommended Hardware
GPU (CUDA enabled)
Minimum 8GB VRAM recommended
Model Architecture Overview
Encoder
256×256×3 → 64×64×256 latent representation
Latent Diffusion UNet
Noise prediction in latent space
500 diffusion timesteps
Decoder
64×64×256 → 256×256×3 reconstruction
PatchGAN Discriminator
Patch-level adversarial learning

# Step-3 Training the Model
Training Configuration
Parameter	Value
Image Size	256×256
Batch Size	8
Epochs	500
Timesteps	500
Learning Rate	2e-4

# Stpe-4 Loss Functions Used
Generator Loss:
Total Loss = AE + Diffusion + KL + GAN
Where:

AE → Reconstruction MSE
Diffusion → Noise prediction loss
KL → Latent regularization
GAN → PatchGAN adversarial loss
Discriminator Loss: Real vs Fake BCE Loss

# Step-5 Image Generation During Training
Every 20 epochs:
sample_20.png
sample_40.png
...
Generated images are saved automatically.

To generate after training:
z = torch.randn(8,256,64,64).to(device)
fake = G(z)
save_image((fake+1)/2, "generated.png", nrow=4)

# Step-6 Repeat Training Order for 3 Classes

Train in this order:
1️⃣ Early Blight
2️⃣ Late Blight
3️⃣ Healthy

Expected Outcomes

High structural fidelity leaf generation
Improved FID compared to vanilla GAN
Stable latent diffusion training
Better texture preservation in disease spots

PL-LDGAN improves over vanilla GAN and LDM by:
Operating in compact latent space
Combining reconstruction + diffusion + adversarial supervision
Maintaining disease-specific structural patterns

