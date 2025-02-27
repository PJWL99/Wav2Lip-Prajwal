Here's How I implemented the model...

# Wav2Lip - Lip Sync Model Implementation

## 📌 Project Overview  
This project implements **Wav2Lip**, a state-of-the-art lip-syncing model. Given an input video and an audio file, the model generates a new video where the speaker’s lips are synchronized with the provided speech.

---

## 🚀 Steps to Run the Project  

### **1️⃣ Clone the Repository**
```bash
git clone https://github.com/Rudrabha/Wav2Lip.git
cd Wav2Lip
```

### **2️⃣ Create and Activate Virtual Environment**
```bash
python -m venv wav2lip_env
wav2lip_env\Scripts\activate  # Windows
source wav2lip_env/bin/activate  # Mac/Linux
```

### **3️⃣ Install Dependencies**
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### **4️⃣ Download and Place Model Checkpoints**
- Download the **Wav2Lip checkpoint** from:  
  💽 [Google Drive Link](https://drive.google.com/drive/folders/1W9mq3vAl83VVjuEv9TOpATQojcI9D7Kb)  
- Place the `.pth` file inside the `checkpoints/` folder.

### **5️⃣ Generate Audio from Text (TTS)**
Use **Google Text-to-Speech (gTTS)** to generate the speech audio:
```python
from gtts import gTTS

text = """Namaste Mathangi! My name is Anika, and I’m here to guide you through managing your credit 
card dues. Mathangi, as of today, your credit card bill shows an amount due of INR 5,053 which 
needs to be paid by 31st December 2024. Missing this payment could lead to two significant consequences: 
First, a late fee will be added to your outstanding balance. 
Second, your credit score will be negatively impacted, which may affect your future borrowing ability. 
Make your payment by clicking the link here... Pay through UPI or bank transfer. Thank you!"""

tts = gTTS(text, lang='en', tld='co.in')  # Indian accent
tts.save("audio.mp3")
```

### **6️⃣ Convert Image to Video**
If using an **image** instead of a **video**, create a short silent video:
```bash
ffmpeg -loop 1 -i input_image.jpg -c:v libx264 -t 5 -pix_fmt yuv420p input_video.mp4
```

### **7️⃣ Run Wav2Lip for Lip Syncing**
```bash
python inference.py --checkpoint_path checkpoints/wav2lip_gan.pth --face input_video.mp4 --audio audio.mp3
```

### **8️⃣ Output Location**
- The generated **lip-synced video** is saved in the `results/` folder.

---
