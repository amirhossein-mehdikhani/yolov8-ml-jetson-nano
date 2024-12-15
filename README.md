
# ML and YOLOv8 for Jetson Nano Docker Image

This repository hosts the Docker image `amirhosseinmehdikhani/ml-jetson-nano`, based on NVIDIA’s **L4T ML** image tailored for the Jetson Nano platform. It includes **Ultralytics YOLOv8 (v8.0.208)** for state-of-the-art object detection and AI tasks.

## Features
- **Base Image**: `l4t-ml:r32.7.1-py3` from NVIDIA’s JetPack 4.6.1 (L4T R32.7.1).
- **Frameworks and Libraries**:
  - TensorFlow 1.15.5
  - PyTorch v1.10.0
  - torchvision v0.11.0
  - torchaudio v0.10.0
  - ONNX 1.11.0
  - CuPy 9.2.0
  - OpenCV 4.5.0 (with CUDA)
  - NumPy, SciPy, Pandas, Scikit-learn
- **Ultralytics YOLOv8 (v8.0.208)** added for advanced vision tasks.

## How to Use

### Pull the Image
To download the Docker image, use the following command:
```bash
sudo docker pull amirhosseinmehdikhani/ml-jetson-nano
```

### Run the Container
To start the container interactively, run:
```bash
sudo docker run -it --runtime nvidia \
    --network host \
    --volume /tmp/.X11-unix:/tmp/.X11-unix \
    --env DISPLAY=$DISPLAY \
    amirhosseinmehdikhani/ml-jetson-nano
```

### Verify YOLOv8 Installation
Once inside the container, verify that YOLOv8 is installed correctly by running:
```bash
python3 -m ultralytics check
```

### Example: Run YOLOv8 Inference
To perform object detection with YOLOv8, use the following example command:
```bash
python3 -m ultralytics detect predict \
    --weights yolov8n.pt \
    --source your_image_or_video_path
```
Replace `your_image_or_video_path` with the path to your input image or video.

## Notes
- Ensure that your Jetson Nano is set up with the NVIDIA Container Runtime.
- This image is designed for JetPack 4.6.1; compatibility with other versions may vary.

## References
- NVIDIA L4T ML: [Documentation](https://catalog.ngc.nvidia.com/orgs/nvidia/containers/l4t-ml)
- Ultralytics YOLOv8: [GitHub](https://github.com/ultralytics/ultralytics)
