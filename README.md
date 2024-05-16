# testRepo
link referensi :
1. https://forums.developer.nvidia.com/t/driver-drowsiness-detection-based-on-eyes-on-jetson-nano/227295
2. https://github.com/hazeeq911/Driver-Drowsiness-Detection
3. https://github.com/nikhilgawai/Driver_Drowsiness-Detection-on-Jetson-Nano-2GB


1. https://qengineering.eu/install-pytorch-on-jetson-nano.html
2. https://elinux.org/Jetson_Zoo
3. https://pytorch.org/blog/running-pytorch-models-on-jetson-nano/
4. https://i7y.org/en/yolov8-on-jetson-nano/ [berhasil dicoba di Jetson Nano running good 10 Mei 2024 03:27 WITA - SCARLET 2]

# SCARLET 2 Project
1. Install system baru di Jetson Nano 4G
2. Hapus file libreoffice dan thunderbird
3. Bikin swap tambahan
4. update dan upgrade system OS
5. Buka terminal eksekusi perintah :
   sudo apt install -y python3.8 python3.8-venv python3.8-dev python3-pip \libopenmpi-dev libomp-dev libopenblas-dev libblas-dev libeigen3-dev libcublas-dev
6. Cloning repo YOLOv8,
   pada terminal eksekusi perintah :
   git clone https://github.com/ultralytics/ultralytics
8. Masuk ke folder ultralytics
9. Membuat virtual environment python3.8,
   pada terminal eksekusi perintah :
   python3.8 -m venv scarlet2-env
10. Aktifkan virtual environment,
   pada terminal eksekusi perintah :
   source scarlet2/bin/activate
11. Update Python packages not specified in YOLOv8,
   pada terminal eksekusi perintah :
   pip install -U pip wheel gdown
12. Download dan install the pre-built PyTorch, TorchVision paket python3.8,
   pada terminal eksekusi perintah :
   a. download pytorch 1.11.0
   gdown https://drive.google.com/uc?id=1hs9HM0XJ2LPFghcn7ZMOs5qu5HexPXwM
   b. download torchvision 0.12.0
   gdown https://drive.google.com/uc?id=1m0d8ruUY8RvCP9eVjZw4Nc8LAwM8yuGV
   python3.8 -m pip install torch-*.whl torchvision-*.whl
14. Install the Python package for YOLOv8,
   pada terminal eksekusi perintah :
   pip install .
15. test program YOLOv8,
   pada terminal eksekusi perintah :
    a. kode 1 : yolo task=detect mode=predict model=yolov8n.pt source=0 show=True
    b. kode 2 : yolo task=segment mode=predict model=yolov8n-seg.pt source=0 show=True
   
   Note that for object detection, tasks=detect displays bounding boxes, and tasks=segment displays bounding boxes and segmentation.
   YOLOv8 has several models (yolov8n, yolov8s, yolov8m, yolov8l, yolov8x), and the following are the actual FPS when running on Jetson Nano.
16. Display window akan menampilkan visualisasi kamera secara live


# Buat SWAP di Nano
1. Masuk ke terminal
2. Ketik : free -h
3. Ketik : df -h
4. Ketik : sudo fallocate -l 4G /swapfile
5. Ketik : ls -lh /swapfile
# Mengaktifkan SWAP Partition
1. Ketik : sudo chmod 600 /swapfile
2. Ketik : sudo mkswap /swapfile
3. Ketik : sudo swapon /swapfile
# Cek partisi SWAP
1. Ketik : free -h
# Backup FSTAB
1. Ketik : sudo cp /etc/fstab /etc/fstab.bak
2. Ketik : echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

sumber : https://www.forecr.io/blogs/programming/how-to-increase-swap-space-on-jetson-modules
