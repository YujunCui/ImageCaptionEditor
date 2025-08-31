# Image Caption Editor

A graphical interface tool for editing image-text pair data, supporting two data formats: image_json_pair format and message format.

## Features

- Supports two data formats:
  - **image_json_pair format**: Each image file corresponds to a JSON file with the same name, which contains image description information
  - **message format**: One JSON file contains multiple image description entries, each entry can reference multiple image files
- Multilingual interface support (Chinese/English)
- Image preview with zoom functionality
- Text editing area for JSON format description editing
- Navigation functions: browse forward/backward and jump to specific images
- Keyboard shortcut support for improved efficiency

## Interface Introduction

### Main Components

1. **Left Control Panel**
   - Language selection: Switch between Chinese and English interfaces
   - Mode selection: Choose data format (image_json_pair or message)
   - Directory settings: Select directory containing data
   - Image navigation: Browse images forward/backward, jump to specific images
   - Text editing: Enter edit mode
   - Information display: Show total image count and other information

2. **Right Display Area**
   - Image preview area: Display current image with zoom support
   - Text editing area: Display and edit JSON data of image descriptions

## Usage Guide

### Data Format Description

#### image_json_pair Format

This format requires each image file to have a corresponding JSON file with the same name, for example:
```
data/
├── image1.jpg
├── image1.json
├── image2.png
└── image2.json
```

The JSON file content format is as follows:
```json
[
  {
    "vision_path": "D:\\Data\\mllm_testdata\\test_imgs\\有肢体冲突\\0.jpg",
    "answer": "A couple outdoors, playing around, with trees and blue sky in the background."
  }
]
```

#### message Format

This format uses one JSON file containing all image description information:
```json
[
  {
    "messages": [
      {
        "content": "<image>Please briefly describe the image content.",
        "role": "user"
      },
      {
        "content": "A couple outdoors playing around, with trees and blue sky in the background.",
        "role": "assistant"
      }
    ],
    "images": [
      "D:\\Data\\mllm_testdata\\test_imgs\\有肢体冲突\\0.jpg"
    ]
  },
  {
    "messages": [
      {
        "content": "<image>Please briefly describe the image content.",
        "role": "user"
      },
      {
        "content": "Four people in a circle pushing each other with bamboo poles.",
        "role": "assistant"
      }
    ],
    "images": [
      "D:\\Data\\mllm_testdata\\test_imgs\\有肢体冲突\\71a046b26d52218a15be3fecc938f246.jpeg"
    ]
  }
]
```

### Operation Guide

1. **Select Data Directory**
   - Click the "Select Directory" button to choose the directory containing images and JSON files

2. **Browse Images**
   - Use the "First", "Previous", "Next", "Last" buttons for navigation
   - Use keyboard shortcuts: Home (First), End (Last), F (Next), D (Previous)
   - Enter the index number in the jump input box to jump directly to a specific image

3. **View Images**
   - Images will be automatically displayed in the left preview area
   - Use mouse wheel to scroll up and down to view multiple images
   - Use Ctrl+Mouse Wheel to zoom images, but images will be constrained within the preview area

4. **Edit Descriptions**
   - Click the "Edit Text" button or press E key to enter edit mode
   - Modify the JSON format description content in the text editing area
   - Press Ctrl+S to save changes, or press Esc to cancel editing
   - Click the "Save Changes" button to confirm saving, or click the "Exit Edit" button to discard changes

5. **Interface Language Switching**
   - Select English or Chinese in the "Language / 语言" option

## Keyboard Shortcuts

| Shortcut | Function |
|----------|----------|
| Ctrl+S | Save changes |
| Ctrl+Z | Undo |
| Ctrl+Y | Redo |
| Esc | Exit edit mode |
| E | Enter edit mode |
| F | Next image |
| D | Previous image |
| Home | First image |
| End | Last image |
| Ctrl+Mouse Wheel | Image zoom |
| Ctrl+0 | Reset image zoom |

## Notes

1. Ensure JSON file format is correct, otherwise the program may error
2. Image files and JSON files need to correspond correctly
3. In message format, image paths can be absolute paths or relative paths to the JSON file
4. Maintain correct JSON format when editing, otherwise saving will fail
5. The program automatically saves the zoom state of each image for consistent viewing experience
6. The program may freeze when processing large amounts of data, please process in batches.