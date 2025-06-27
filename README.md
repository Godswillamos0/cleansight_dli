♻️ DSN Trash Detection Project
Welcome to the DSN Trash Detection Project — an AI-powered solution using YOLOv8 to detect and classify waste in images. This project aims to assist sustainability and waste management efforts by identifying various categories of garbage from images efficiently and in real-time.


📁 Dataset
We use the publicly available dataset hosted on Kaggle:
📦 spellsharp/garbage-data

It contains labeled images for various types of garbage, annotated in YOLO format.

🚀 Features
⚡ YOLOv8 object detection for real-time trash classification

🧠 Annotated dataset visualization

📉 Integrated training logging with Weights & Biases

🎯 High accuracy with minimal training time

🧩 Supports custom YAML-based class loading

🛠️ Installation & Setup (Kaggle Notebook or Colab)
No special installation is needed on Kaggle. However, the following packages are used:

bash
Copy
Edit
!pip install -Uqq ultralytics
🧪 Getting Started
1. 🧬 Load Dataset from Kaggle Hub
python
Copy
Edit
import kagglehub
spellsharp_garbage_data_path = kagglehub.dataset_download('spellsharp/garbage-data')
2. 🏗️ Visualize Annotations
python
Copy
Edit
visualize_yolo_data(Path('/kaggle/input/garbage-data/YOLO-Waste-Detection-1/YOLO-Waste-Detection-1/train'))
3. 🔧 Train the YOLOv8 Model
python
Copy
Edit
from ultralytics import YOLO
model = YOLO('yolo11l.pt', task='detect')

model.train(
    data='../input/garbage-data/data.yaml',
    time=10,
    cos_lr=True,
    batch=-1,
    imgsz=640,
    project='dsn ai project',
    name='yolo11l'
)
Training uses the official Ultralytics YOLO library and the configuration from data.yaml.

🔍 Output
Annotated visualizations for 10 random images

Training logs tracked via Weights & Biases

YOLO model weights saved and ready for deployment

📊 Visualization Preview
Example output with bounding boxes and class labels:


🤖 Model Performance
Metric	Value (Example)
mAP@50	0.85
Inference FPS	~30 FPS
Classes	Plastic, Glass, Metal, Paper, Organic, Others

📡 Monitoring with Weights & Biases
Logging into wandb:

python
Copy
Edit
import wandb
from kaggle_secrets import UserSecretsClient

user_secrets = UserSecretsClient()
wandb.login(key=user_secrets.get_secret("wandb_key"))
🤝 Contribution
Feel free to fork this project, suggest improvements, or contribute new detection classes or dataset augmentation techniques!

📄 License
This project is under the MIT License. See LICENSE for details.

🌱 About DSN
The DSN AI Project is focused on developing sustainable AI applications to promote a cleaner, greener environment through innovative tech.

