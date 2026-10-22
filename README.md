Image Forgery Detection and Analysis
Project Overview
This project analyzes an uploaded image using traditional image-processing techniques to identify regions that may be suspicious or manipulated. It produces several visual outputs, including edge detection, frequency-domain representations, Error Level Analysis (ELA), a heatmap, and bounding boxes around regions flagged by a simple threshold.

Important: This is an exploratory image-forensics project. Its score and visualizations do not prove that an image is forged or authentic. Results can be affected by image format, compression history, resizing, and other processing.
Features
- Upload an image in Google Colab.
- Display the original image and a grayscale version.
- Apply Canny edge detection for spatial analysis.
- Calculate the Fast Fourier Transform (FFT) magnitude spectrum.
- Calculate a Discrete Cosine Transform (DCT) representation.
- Perform Error Level Analysis (ELA) by recompressing the image as JPEG.
- Generate a color heatmap from ELA differences.
- Threshold ELA differences and draw boxes around sufficiently large candidate regions.
- Display the outputs together in a visualization dashboard.
- Print a basic, heuristic “Forgery Score” and a tentative label.
Technologies Used
- Python
- OpenCV (opencv-python)
- NumPy
- Matplotlib
- Pillow
- Google Colab file-upload utility
Requirements
The notebook installs the main libraries with:
pip install opencv-python pillow matplotlib
NumPy is used by the script and is commonly installed with these packages. If needed, install it explicitly:
pip install numpy
The script imports google.colab.files, so the provided version is intended to run in Google Colab.
How to Run
1. Open Google Colab.
2. Create a new notebook or upload/open the notebook version of this project.
3. Copy the code into notebook cells, keeping the steps in order.
4. Run the library-installation cell.
5. Run the import cell.
6. Run the upload cell and select an image file.
7. Run the remaining cells in sequence.
8. Review the original image, grayscale image, edge map, FFT, DCT, ELA, heatmap, thresholded regions, and final dashboard.
Processing Pipeline
1. Image upload and loading: The uploaded file is read with OpenCV and converted from BGR to RGB for display.
2. Grayscale preprocessing: The image is converted to grayscale for edge and frequency analysis.
3. Spatial analysis: Canny edge detection highlights strong intensity transitions.
4. FFT analysis: The image is transformed into the frequency domain and its magnitude spectrum is displayed.
5. DCT analysis: The Discrete Cosine Transform visualizes frequency components.
6. Error Level Analysis: The image is saved again as a JPEG at quality 90, then pixel differences are amplified.
7. Heatmap: ELA differences are converted into a color heatmap for easier visual inspection.
8. Candidate-region detection: A threshold is calculated from the normalized ELA image, and contours larger than 500 pixels are boxed.
9. Heuristic score: The mean grayscale ELA intensity is printed and compared with a fixed threshold of 25 to produce a tentative label.
Output
The program displays:
- Original image
- Grayscale image
- Canny edge detection
- FFT magnitude spectrum
- DCT frequency components
- ELA difference image
- ELA-based heatmap
- Thresholded suspicious-region mask
- Image with candidate regions outlined
- A numerical heuristic score and tentative text result
Limitations
- The score threshold (25) is a manually selected heuristic, not a trained or validated classifier.
- ELA can highlight differences caused by ordinary compression or editing and can miss some manipulations.
- FFT and DCT visualizations provide image characteristics but do not independently determine authenticity.
- Highlighted boxes are candidate regions for manual review, not confirmed tampering.
- The script does not calculate accuracy, precision, recall, or other validated performance metrics.
- The code expects an image to be uploaded; it is not a batch-processing pipeline.
- The code imports Google Colab's upload utility and will need modification to run unchanged in a standard local Python environment.
Possible Improvements
- Add input validation and support for common image formats.
- Save generated visualizations and analysis results to files.
- Make thresholds configurable and compare results across several settings.
- Test on a labeled dataset containing authentic and manipulated images.
- Evaluate with precision, recall, F1-score, and confusion matrices.
- Consider a validated machine-learning model and clearly document its dataset and limitations.
Disclaimer
This tool is intended for educational and preliminary inspection purposes only. Do not use its output as sole evidence for forensic, legal, or other high-stakes decisions.
