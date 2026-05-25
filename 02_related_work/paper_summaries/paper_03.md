# Paper 03 Summary
## Citation
Title: Manga Speech Bubble Segmentation
 Author: Juithealien
 Year: 2024
 Source: Hugging Face
 DOI/Link: https://huggingface.co/juithealien/manga109-segmentation-bubble

## Problem
This paper addresses the problem of automatic speech bubble detection and segmentation in manga images.
Main challenges:
Speech bubbles have various shapes and sizes
Manga pages contain complex layouts
Text and background may overlap
Accurate segmentation is required for OCR and manga translation

## Method
The paper uses:
YOLO11n Instance Segmentation
System workflow:
Input manga image
Feature extraction using CNN backbone
YOLO detection head detects speech bubbles
Segmentation branch generates masks
Output bounding boxes and segmentation masks
Main architecture:
YOLO backbone
Detection head
Instance segmentation mask branch

## Dataset
The paper uses:
Manga109-based Dataset
Dataset includes:
Manga pages
Speech bubble annotations
Pixel-level segmentation masks
Characteristics:
Black-and-white manga images
Multiple manga art styles
Annotated speech bubbles

## Evaluation
The paper evaluates the model using the following metrics:
Metric
Box
Mask
Precision
97.55%
97.66%
Recall
97.03%
97.15%
mAP@50
99.10%
99.13%
mAP@50-95
96.67%
94.69%

## Results show:
Very high accuracy
Stable segmentation masks
Good performance across different manga styles

## Main Contributions
Developed a speech bubble segmentation system for manga
Applied YOLO for instance segmentation
Achieved high detection accuracy
Supported OCR and manga translation workflows
Optimized for real-time inference

