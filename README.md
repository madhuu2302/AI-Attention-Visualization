# AI Attention Visualizer

An educational AI application that demonstrates how **OCR, sentence embeddings, and the attention mechanism** work together to analyze text from study-note images.

The application is built using **Python and Streamlit**. Users can upload an image containing text, extract the text using Tesseract OCR, generate word embeddings using Sentence Transformers, and visualize attention scores for the extracted words.

##App : http://localhost:8501/

## Features

* Upload JPG, JPEG, or PNG study-note images
* Extract text from images using Tesseract OCR
* Process extracted words
* Generate word embeddings using Sentence Transformers
* Calculate attention scores using NumPy
* Display word-level attention using Streamlit progress bars
* Identify the word with the highest attention score
* Simple and beginner-friendly web interface

## Project Workflow

```text
Image
  ↓
OCR
  ↓
Extract Text
  ↓
Process Words
  ↓
Sentence Embeddings
  ↓
Attention Mechanism
  ↓
Word Attention Scores
  ↓
Visualization
```

## Technologies Used

| Technology            | Purpose                      |
| --------------------- | ---------------------------- |
| Python                | Main programming language    |
| Streamlit             | Web application interface    |
| Pillow                | Image handling               |
| Tesseract OCR         | Text extraction from images  |
| Pytesseract           | Python wrapper for Tesseract |
| Sentence Transformers | Generate text embeddings     |
| NumPy                 | Attention calculations       |

## Project Structure

```text
AI-Attention-Visualizer/
│
├── app.py
├── ocr.py
├── embedding.py
├── attention.py
├── requirements.txt
└── README.md
```

The project is organized into separate modules for the Streamlit application, OCR, embeddings, and attention calculation.

## How It Works

### 1. Image Upload

The user uploads a study-note image through the Streamlit interface.

### 2. OCR

Tesseract OCR extracts the text from the uploaded image using `pytesseract`.

### 3. Word Processing

The extracted text is split into individual words and basic unwanted characters are removed.

### 4. Word Embeddings

The application uses the `all-MiniLM-L6-v2` Sentence Transformer model to convert words into numerical vectors. The model produces **384-dimensional embeddings**.

### 5. Attention Calculation

The embeddings are passed through a basic scaled dot-product attention mechanism using NumPy.

The attention process uses:

```text
Query (Q)
Key (K)
Value (V)
   ↓
Q × Kᵀ
   ↓
Scaling
   ↓
Softmax
   ↓
Attention Weights
```

The implementation uses randomly initialized projection matrices for the demonstration.

### 6. Visualization

The calculated attention scores are displayed as progress bars in the Streamlit application. The word with the highest calculated attention score is also displayed.

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/AI-Attention-Visualizer.git
```

```bash
cd AI-Attention-Visualizer
```

### 2. Install Python Dependencies

```bash
python -m pip install -r requirements.txt
```

The required Python packages are:

```text
streamlit
numpy
pillow
pytesseract
sentence-transformers
```

### 3. Install Tesseract OCR

Tesseract OCR must be installed separately because it is an external OCR program.

On Windows, a common installation path is:

```text
C:\Program Files\Tesseract-OCR\tesseract.exe
```

Update the path in `ocr.py` if Tesseract is installed in a different location.

Example:

```python
import pytesseract

pytesseract.pytesseract.tesseract_cmd = (
    r"C:\Program Files\Tesseract-OCR\tesseract.exe"
)

def extract_text(image):
    return pytesseract.image_to_string(image)
```

## Run the Application

Open the project folder in VS Code and run:

```bash
python -m streamlit run app.py
```

Streamlit will open the application in your web browser.

## Example

Upload an image containing study notes.

The application will display:

```text
Uploaded Image
      ↓
Extracted Text
      ↓
Processed Words
      ↓
Word Attention
      ↓
Highest Attention Word
```

## Important Note

This project is designed as an **educational demonstration of the attention mechanism**.

The Query, Key, and Value projection matrices are randomly initialized. Therefore, the word receiving the highest attention score should **not be interpreted as a reliable measure of semantic importance**. The visualization is mainly intended to demonstrate how attention scores are calculated.

## Future Improvements

Possible improvements include:

* Better OCR preprocessing
* Improved attention visualization
* Real trained attention models
* More advanced text processing
* Support for additional image formats
* Interactive visualization of attention relationships

## Learning Outcomes

This project helps demonstrate:

* OCR-based text extraction
* Image processing
* Word embeddings
* Sentence Transformers
* Query, Key, and Value concepts
* Scaled dot-product attention
* Softmax
* AI visualization
* Streamlit application development

## AUTHOR

Madhumitha U
