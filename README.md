# Scene-Localization

Scene-Localization is a Python-based project that leverages OpenAI's CLIP model to perform scene localization in images using natural language queries. The core functionality enables users to input an image (from a URL or local path) and a set of text prompts, and it returns the regions within the image that best match each prompt.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Code Structure](#code-structure)
- [Details of Main Components](#details-of-main-components)
- [Examples](#examples)
- [Dependencies](#dependencies)
- [License](#license)

---

## Overview

This repository demonstrates the use of vision-language models for spatial localization of natural language concepts within images. It does this by sliding a window across the image, comparing each crop to the input prompt using CLIP, and highlighting the region with the highest similarity.

## Features

- Localize arbitrary concepts in images using text prompts.
- Uses CLIP (ViT-B/32) for robust vision-language similarity.
- Visualizes regions in the image that best match the query.
- Command-line interface for user interaction.

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Aahant0607/Scene-Localization.git
   cd Scene-Localization
   ```

2. **Install Python dependencies:**
   You can install the required packages using pip:
   ```bash
   pip install torch torchvision transformers pillow opencv-python-headless matplotlib requests
   ```

## Usage

Run the main script and follow the prompts:
```bash
python aims_project.py
```

- Enter the URL of the image to analyze.
- Enter your natural language queries, separated by commas.

The script will display the original image with bounding boxes and the cropped regions for each prompt.

## Code Structure

```
Scene-Localization/
├── README.md
└── aims_project.py
```

### File Details

- **aims_project.py**  
  The main script implementing all functionality:
  - Loads the CLIP model and processor.
  - Defines functions for loading and preprocessing images, generating sliding window crops, computing image-text similarity, and visualizing results.
  - Provides a demo function for interactive use from the command line.

- **README.md**  
  This documentation file.

## Details of Main Components

### 1. Loading and Preprocessing Images
- `load_image(image_path_or_url)` loads an image from a local path or URL and returns a PIL Image.

### 2. Candidate Region Generation
- `generate_candidate_regions(image, window_size=224, stride=112)` uses a sliding window to extract crops from the image, returning both crops and their bounding boxes.

### 3. Text-Image Similarity Computation
- `compute_similarity(regions, text_query)` computes CLIP similarity scores between the prompt and every crop.

### 4. Scene Localization
- `localize_scene(image_path_or_url, text_query, top_k=1)` finds the crop with highest similarity to the prompt and returns the cropped image, bounding box, and similarity score.

### 5. Visualization
- `demo(image_path_or_url, queries)` visualizes the results: the original image with a bounding box and the best-matching crop for each prompt.

### 6. User Interaction
- The script prompts the user for an image URL and queries, then displays the results.
- Example prompts might be: "a man in a red shirt", "a dog playing fetch".

## Examples

Sample image URLs (can be used for testing):
```text
https://images.tribuneindia.com/cms/gall_content/2016/3/2016_3$largeimg21_Monday_2016_013209330.jpg
https://www.slowfood.com/wp-content/uploads/2023/12/wet-market-dhaka-1.jpg
https://elements-resized.envatousercontent.com/elements-video-cover-images/2dbb75c9-f2a7-4f22-b4e1-1d428ece8e43/video_preview/video_preview_0000.jpg?w=500&cf_fit=cover&q=85&format=auto&s=805b1a1c3d0bfe90f6ba8c4ace2e9a1b0
```

Example queries:
- a man in a red shirt
- a dog playing fetch
- a group of people

## Dependencies

- torch
- torchvision
- transformers
- pillow
- opencv-python-headless
- matplotlib
- requests

(Install via pip as shown above.)


For any questions or contributions, please open an issue or pull request.
