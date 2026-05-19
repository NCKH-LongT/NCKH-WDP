# Topic Proposal

## 1. Group Information

- Class: SE1823
- Group: G06
- Leader: Nguyen Tuan Tu
- Members: Nguyen Tien Dat, Huynh Kha Tu, Nguyen Minh Huy

## 2. Proposed Title

English title:

AI-Assisted Manga Localization Management System with Collaborative Editorial Workflow

Vietnamese title:

Hệ thống quản lý localization manga tích hợp AI và workflow biên tập cộng tác

## 3. Application Domain

- Manga localization workflow
- AI-assisted image processing
- Collaborative editorial management
- Digital content production
- Computer vision applications

## 4. Problem Statement

Traditional manga localization workflows rely heavily on manual editing and disconnected collaboration processes between assistants and editors. Tasks such as speech bubble cleaning, text replacement, and revision tracking are often performed manually using multiple separate tools.

These workflows create several measurable bottlenecks:

- Manual speech bubble cleaning requires significant editing time for each manga page.
- Editors spend considerable time reviewing localization revisions and coordinating with assistants.
- Production teams face difficulties tracking task progress and revision history across multiple chapters.
- Existing manga editing tools mainly focus on standalone image editing and lack integrated workflow management and AI-assisted localization support.

As manga production scales, these limitations reduce workflow efficiency and increase production overhead.

Therefore, a centralized manga localization management system integrated with AI-assisted speech bubble processing and collaborative editorial workflow support is needed.

## 5. Motivation

Modern manga production requires efficient coordination between assistants, editors, and production teams. However, localization workflows still depend heavily on repetitive manual editing processes.

Recent computer vision models such as YOLO and U-Net can automate repetitive localization tasks including speech bubble detection and segmentation. Integrating these AI models into a collaborative workflow system may help reduce editing effort, improve workflow tracking, and support more efficient manga localization pipelines.

This study investigates how existing AI models can be integrated into a manga localization management system to support AI-assisted editing and collaborative editorial workflows.

## 6. Target Users

The main target users of the proposed system are:

- Manga Assistants
- Tantou Editors
- Mangaka
- Editorial Boards
- Publishing Teams

## 7. Proposed AI Model / Method

The proposed system integrates several AI and image processing components into the localization workflow.

### YOLO

Used for:

- Speech bubble detection
- Region localization
- Bubble bounding box generation

### U-Net

Used for:

- Speech bubble segmentation
- Pixel-level mask generation
- Editable bubble region extraction

### OpenCV

Used for:

- Image preprocessing
- Bubble whitening
- Region cleaning
- Post-processing operations

### Human-in-the-loop Workflow

Used for:

- Manual correction of AI-generated regions
- Editorial review and approval
- Revision management
- Assistant-editor collaboration

## 8. System Features

The main features of the proposed system include:

1. Manga project and chapter management

2. AI-assisted speech bubble detection and segmentation

3. Bubble whitening and editable localization regions

4. Collaborative canvas-based manga editing

5. Production task assignment and tracking

6. Editorial annotation and revision workflow

7. Localization version management

8. Export and archive management

## 9. Expected Contribution

The expected contributions of this study include:

1. Proposing an AI-assisted manga localization workflow management architecture.

2. Integrating YOLO and U-Net into a collaborative manga editing system.

3. Supporting editable AI-assisted speech bubble localization workflows.

4. Improving collaboration between assistants and editors through centralized workflow management.

5. Evaluating the effectiveness of AI-assisted localization compared with traditional manual workflows.

## 10. Evaluation Plan

The proposed system will be evaluated using AI performance metrics and workflow usability evaluation.

- Dataset:
  - Manga109 dataset
  - Annotated manga page samples
  - Custom speech bubble annotations

- Baseline:
  - Traditional manual localization workflow
  - Manual bubble editing without AI assistance

- Metrics:

  ### Detection Metrics
  - Precision
  - Recall
  - mAP

  ### Segmentation Metrics
  - IoU
  - Dice Score

  ### Workflow Metrics
  - Localization processing time
  - Task completion time
  - User satisfaction score

- Expert evaluation:
  - Evaluation by editors and assistants regarding segmentation quality and workflow usability

- User survey:
  - Survey on collaboration efficiency, editing usability, and AI-assisted workflow usefulness

## 11. Related Papers

| No | Title                                                                            | Year | Source                              | Link / DOI                                   |
| --- | -------------------------------------------------------------------------------- | ---- | ----------------------------------- | -------------------------------------------- |
| 1 | Building a Manga Dataset "Manga109" with Annotations for Multimedia Applications | 2020 | IEEE MultiMedia                     | https://doi.org/10.1109/MMUL.2020.2987895 |
| 2 | U-Net: Convolutional Networks for Biomedical Image Segmentation | 2015 | MICCAI / Springer LNCS | https://doi.org/10.1007/978-3-319-24574-4_28 |
| 3 | YOLOv4: Optimal Speed and Accuracy of Object Detection | 2020 | arXiv | https://doi.org/10.48550/arXiv.2004.10934 |
| 4 | Deep CNN-based Speech Balloon Detection and Segmentation for Comic Books | 2019 | arXiv preprint (cs.CV) | https://doi.org/10.48550/arXiv.1902.08137 |
| 5 | Human-in-the-Loop Machine Learning: A State of the Art | 2022 | Artificial Intelligence Review | https://doi.org/10.1007/s10462-022-10246-w |
