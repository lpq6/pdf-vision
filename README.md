# PDF Vision Skill

## Overview
This skill extracts text content from **image-based or scanned PDFs** using your Xflow vision API (`qwen3-vl-plus`). It's designed for PDFs that contain images instead of selectable text.

## Installation
The skill is automatically available when placed in your OpenClaw workspace skills directory:
```
~/.openclaw/workspace/skills/pdf-vision/
```

## Prerequisites
- **Xflow API configured** in your OpenClaw config (`~/.openclaw/openclaw.json`)
- **Python libraries**: `pypdfium2` (already installed)
- **System tools**: `curl`, `base64`

## Usage Examples

### Command Line
```bash
# Basic usage
./scripts/pdf_vision.py --pdf-path /path/to/document.pdf

# Specify page number (1-indexed)
./scripts/pdf_vision.py --pdf-path /path/to/document.pdf --page 2

# Custom prompt for structured extraction
./scripts/pdf_vision.py --pdf-path invoice.pdf --prompt "Extract vendor, date, and total as JSON"

# Save output to file
./scripts/pdf_vision.py --pdf-path document.pdf --output extracted.txt
```

### Shell Script
```bash
# Using the bash version
./scripts/extract_pdf_vision.sh --pdf-path /path/to/document.pdf --prompt "Your custom prompt"
```

## Integration with OpenClaw
This skill can be called programmatically from other OpenClaw workflows or used as a standalone tool for processing scanned documents.

## Supported Document Types
- Scanned academic documents (class schedules, transcripts, etc.)
- Photographed documents
- Image-only PDFs
- Documents with complex layouts and tables
- Multi-language documents (Chinese, English, etc.)

## Performance Notes
- Processing time: ~10-15 seconds per page
- Image quality: Higher resolution scans yield better results
- File size: Large PDFs may need to be split into individual pages first

## Troubleshooting
- **"PDF file not found"**: Ensure the PDF path is correct and accessible
- **"API configuration error"**: Verify your OpenClaw config has valid Xflow credentials
- **"No text extracted"**: Try adjusting the prompt or check image quality
- **"Page number invalid"**: PDF page numbers are 1-indexed in the command line

## License
MIT License - Free to use and modify.