# Praj PDF Converter

A local Streamlit dashboard for assembling images, OCR text, spreadsheets, office documents, and PDFs into a downloadable PDF.

## Run

1. Install Python 3.11+.
2. Create and activate a virtual environment:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

3. For image OCR, install the Tesseract desktop engine and ensure `tesseract.exe` is on PATH. On Windows, the standard install location is `C:\Program Files\Tesseract-OCR`.
4. Start the dashboard:

```powershell
streamlit run app.py
```

Supported inputs: PDF, PNG, JPG, JPEG, WebP, BMP, TIFF, XLSX, XLS, CSV, DOCX, TXT, and Markdown. OCR text is embedded in the PDF and can also be downloaded separately as a text file.

The **Files to Excel** mode extracts selectable PDF tables with `pdfplumber`, reconstructs image tables using Tesseract OCR word positions, copies all workbook sheets, and imports DOCX tables. Each detected table is written to its own Excel worksheet. Image table extraction requires the Tesseract desktop engine; PDF table extraction works best with selectable text and visible table structure.

The app stores local conversion activity in `praj_pdf_converter.db` using SQLite. The log records conversion status, timestamp, output filename, uploaded file metadata, and OCR counts; file contents are not stored in the database.