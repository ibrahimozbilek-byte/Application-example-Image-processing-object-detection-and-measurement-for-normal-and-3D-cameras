#Normal Camera / RealSense Measurement and Depth Camera Application

This application measures objects' dimensions (length, width, height) in real-time and detects their 3D positions using the Intel RealSense D435i depth camera.

## Reference Implementation and Modular Structure

This project serves as a comprehensive reference implementation for developers looking to perform real-time object measurements using OpenCV. Thanks to its modular structure:

- Object detection and measurement algorithms can be easily integrated into different projects
- Camera module can be extended for other depth cameras
- User interface can be customized independently
- Measurement and calibration modules can be used standalone
- Visualization tools can be adapted to other projects
- Testing and debugging tools are provided out of the box

The modular architecture enables quick adaptation of the project to various industrial applications (quality control, robotics, automation, etc.).

## Features

- Real-time object detection and measurement
- Automatic and manual measurement modes
- Conveyor belt mode support
- Multi-language support (Turkish/English)
- Save measurement results in CSV format
- Calibration tools
- Visual debugging tools
- Simulation mode

## Requirements

### Hardware
- Intel RealSense D435i depth camera
  - Depth resolution: 1280 × 720
  - RGB resolution: 1920 × 1080
  - Depth FPS: Up to 90 fps
  - Measurement distance: 0.3m - 3m (optimal)
  - Depth accuracy: <2% at 2m
- USB 3.1 Gen 1 (USB-C) port
- Minimum 8GB RAM (recommended: 16GB)
- 6th generation or newer Intel Core i5/i7/i9 processor or equivalent
- Minimum 2GB free disk space
- Display resolution: minimum 1920x1080

### Software
- Python 3.8+
- Intel RealSense SDK 2.0
- PySide6 6.5.2
- OpenCV 4.8.0
- NumPy 1.24.3
- Matplotlib 3.7.2

## Installation

1. Install Intel RealSense SDK:
   - For Windows:
     1. Download the SDK from https://www.intelrealsense.com/sdk-2/
     2. Run the downloaded file and follow the installation steps
     3. Restart your computer after installation
   
   - For Linux:
     ```bash
     # Install required packages
     sudo apt-get update && sudo apt-get upgrade
     sudo apt-get install software-properties-common
     
     # Add Intel RealSense repository
     sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE
     sudo add-apt-repository "deb https://librealsense.intel.com/Debian/apt-repo $(lsb_release -cs) main"
     
     # Install SDK
     sudo apt-get install librealsense2-dkms librealsense2-utils librealsense2-dev
     ```

2. Install Python 3.8 or higher:
   - For Windows: https://www.python.org/downloads/
   - For Linux: `sudo apt-get install python3.8 python3.8-venv`

3. Create virtual environment (recommended):
   ```bash
   # For Windows
   python -m venv venv
   venv\Scripts\activate
   
   # For Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

4. Install required Python libraries:
   ```bash
   pip install -r requirements.txt
   ```

5. Connect the camera:
   - Use USB 3.1 Gen 1 (USB-C) port
   - Verify camera is recognized correctly:
     - Windows: Check in Device Manager
     - Linux: Test with `realsense-viewer`

6. Start the application:
   ```bash
   python main.py
   ```

## Usage

1. Launch the application:
```bash
python main.py
```

2. Main Features:
- **Automatic Detection**: Automatically detects and measures objects in view
- **Manual Measurement**: Measures objects selected by the user
- **Conveyor Mode**: Detects and measures moving objects
- **Calibration**: Provides tools for camera calibration
- **Visualization**: Visualizes detected objects and measurements

3. Keyboard Shortcuts:
- `Space`: Toggle automatic detection mode
- `C`: Toggle conveyor mode
- `S`: Save snapshot
- `ESC`: Close application

## Project Structure

```
RealsenseMeasureDepthCamera/
├── main.py                 # Main application file
├── Qt6Ui.py               # User interface components
├── configs.json           # Application configuration
├── requirements.txt       # Python dependencies
├── realsense/            # RealSense camera modules
│   ├── depth_camera.py   # Camera operations
│   └── object_measurer.py # Measurement operations
├── utils/                # Helper functions
│   ├── visualization.py  # Visualization tools
│   └── calibration.py   # Calibration operations
├── translations/         # Language files
├── tests/               # Test files
└── captures/            # Saved images
```

## Calibration

Camera calibration is important for accurate measurements:

1. Start calibration mode
2. Show calibration card
3. Take images from different angles
4. Complete calibration process

## Debugging

The program saves debug images to the `captures/` folder during operation:
- `debug_mask.jpg`: Object masks
- `debug_contours.jpg`: Detected contours
- `debug_detection.jpg`: Detection results

## Measurement Results

Measurement results are saved in CSV format:
- `measurement.txt`: Single measurements
- `conveyor_measurements.csv`: Conveyor mode measurements

## License

Commercial license 70$
https://arkoplatinnn.gumroad.com/l/oyyseg
