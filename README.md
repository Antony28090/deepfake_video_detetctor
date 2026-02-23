# Deepfake Video Detector

A web application that detects whether a given video contains deepfake manipulations. It utilizes a PyTorch-based Deep Learning model (EfficientNet-B0) to analyze video frames and provide a confidence score indicating if the video is Real or Fake.

## Features

- **Web Interface:** Simple, easy-to-use web interface built with Flask for uploading videos.
- **Video Processing:** Extracts frames from uploaded videos (formats: mp4, avi, mov) for analysis.
- **Deep Learning Model:** Uses a fine-tuned EfficientNet-B0 model for binary classification (Real vs. Fake).
- **Adaptive Thresholding:** Employs an intelligent decision logic based on average, maximum, and 90th percentile probabilities across frames to reduce false positives and accurately detect glitches or noise.
- **Confidence Score:** Returns a clear percentage indicating the likelihood of the video being fake or real.

## Project Structure

- `app.py`: The main Flask application handling routing, file uploads, and rendering templates.
- `model.py`: Defines the `DeepFakeModel` architecture using PyTorch's EfficientNet-B0.
- `processor.py`: Contains the core logic for video frame extraction, preprocessing, model inference, and the adaptive decision-making algorithm.
- `train.py`: Script for training the deepfake detection model on a dataset.
- `verify_model.py`: Script for evaluating the model's performance on test data.
- `download_data.py`: Utility script for downloading the required dataset.
- `test_setup.py`: Script to verify the environment and dependencies are correctly set up.
- `templates/`: Contains HTML templates (`index.html`, `result.html`) for the web interface.
- `static/css/`: Contains CSS files (`style.css`) for styling the web application.

## Setup and Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Antony28090/Deepfake_Video_Detetctor.git
   cd Deepfake_Video_Detetctor
   ```

2. **Install Dependencies:**
   Ensure you have Python installed. Install the required libraries:
   ```bash
   pip install torch torchvision opencv-python Flask numpy werkzeug
   ```
   *(Note: Depending on your system and GPU availability, you might need specific PyTorch installation commands from the official PyTorch website).*

3. **Download/Prepare Model Weights:**
   The application expects trained model weights. Ensure you have the weights file (e.g., `deepfake_model_best.pth`, `deepfake_model_final.pth`, or `deepfake_model.pth`) in the project root directory. If none are found, predictions will fall back, but may not be accurate.

## Usage

1. **Start the Web Server:**
   ```bash
   python app.py
   ```
2. **Access the Application:**
   Open your web browser and navigate to `http://127.0.0.1:5000/`.
3. **Upload a Video:**
   Select a `.mp4`, `.avi`, or `.mov` file and click upload to analyze. The application will process the video and display the result.

## License
MIT