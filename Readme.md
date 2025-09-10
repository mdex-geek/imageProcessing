# JavaFX Multithreaded Image Processing
This project demonstrates a high-performance image processing pipeline in JavaFX using multithreading. An input image is split into 10x10 blocks, processed in parallel with a mathematical filter, and each block is rendered to the canvas matrix location as soon as it completes.

## Features
- JavaFX UI with real-time canvas rendering

- Multithreaded processing: Each image block processed on its own thread

- Mathematical filters: Kernel/convolution-based image filtering

- First-ready, first-rendered: UI updates dynamically as blocks finish

- Extensible pipeline: Swap filters or block sizes easily

## Architecture
```
flowchart TD
    A[Load image] --> B[Split into 10x10 blocks]
    B --> C{Thread pool}
    C --> D[Process block/filter]
    D --> E[Render immediately on canvas]
```
- Image Splitting: Uses BufferedImage/ImageIO to divide the image into equal 10x10 pixel blocks.

- Multithreading: Employs JavaFX concurrency API (Task, Service) and ExecutorService for parallel computation.

- Mathematical Filtering: Convolves each block with a chosen filter (e.g., sharpening or edge detection).

- Canvas Updating: Each thread calls Platform.runLater() to safely update the JavaFX Canvas as soon as its block is finished.

## Usage
Clone this repository:

 ```git clone https://github.com/mdex-geek/imageProcessing.git```
 
Run using your JavaFX-compatible IDE (JDK 17+ recommended).

Select and load an image via the UI.

See blocks appear dynamically as they finish processing.
## Technical Highlights
- Clean separation between UI and computation

- Thread-safe updates via JavaFX concurrency facilities

- Extensible for different filter kernels or block sizes

- Demonstrates best practices with JavaFX thread safety

References
JavaFX Official Docs

JavaFX Concurrency Guide

Image Processing Algorithms in Java
