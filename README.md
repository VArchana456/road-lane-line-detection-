# road-lane-line-detection-

This project implements a lane detection algorithm for processing images and videos using OpenCV and numpy. The algorithm highlights lane markings on roads, isolating white and yellow lines, and draws them on the image or video frames.

## Features

- **HSL Color Selection:** Converts the image to HSL color space to isolate white and yellow lane markings.
- **Grayscale Conversion:** Converts the image to grayscale.
- **Gaussian Blur:** Applies a Gaussian blur to smooth the image and reduce noise.
- **Canny Edge Detection:** Detects edges in the image.
- **Region of Interest Selection:** Masks the image to focus on the region of interest.
- **Hough Transform:** Detects lines in the edge-detected image.
- **Lane Line Drawing:** Draws the detected lane lines on the original image or video frame.

## Dependencies

- Python 3.x
- OpenCV
- numpy
- matplotlib
- moviepy

## Installation

1. Clone this repository:
    ```bash
    git clone https://github.com/yourusername/lanedetection.git
    ```
2. Navigate to the project directory:
    ```bash
    cd lanedetection
    ```
3. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

## Usage

### Processing Images

Place the images you want to process in the `images` folder. Supported formats are `.jpg`, `.png`, and `.jpeg`.

Run the following command to process all images in the `images` folder:
```bash
python process_images.py
```

### Processing Videos

Place the videos you want to process in the `video` folder. 

Run the following command to process all videos in the `video` folder:
```bash
python process_videos.py
```

## Code Overview

### Image Processing

The function `process_image(image)` processes a single image:

1. **HSL Color Selection:** `HSL_color_selection(image)`
2. **Grayscale Conversion:** `gray_scale(image)`
3. **Gaussian Blur:** `gaussian_blur(image)`
4. **Canny Edge Detection:** `canny_edge_detection(image)`
5. **Region of Interest:** `region_of_interest(image, vertices)`
6. **Hough Transform:** `hough_lines(image, rho, theta, threshold, min_line_len, max_line_gap)`
7. **Lane Line Drawing:** `lane_lines(image, lines)` and `draw_lane_lines(image, (left_line, right_line))`

### Video Processing

The function `process_video(video_path)` processes a video file by reading it frame by frame and applying the `process_image(image)` function to each frame.

## Example

### Processing Images

```python
import os
import cv2
import matplotlib.image as mpimg

image_folder = 'images'
for filename in os.listdir(image_folder):
    if filename.endswith(('.jpg', '.png', '.jpeg')):
        image_path = os.path.join(image_folder, filename)
        image = mpimg.imread(image_path)
        processed_image = process_image(image)
        cv2.imshow('Processed Image', processed_image)
        cv2.waitKey(0)
        cv2.destroyAllWindows()
```

### Processing Videos

```python
video_folder = 'video'
video_files = [os.path.join(video_folder, f) for f in os.listdir(video_folder) if os.path.isfile(os.path.join(video_folder, f))]
for video_file in video_files:
    process_video(video_file)
```

## Acknowledgments

- The code uses OpenCV and numpy libraries.
- The project is inspired by lane detection algorithms commonly used in self-driving car technology.
