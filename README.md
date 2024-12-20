# MarkItDown Converter

MarkItDown Converter is a web application that converts various document formats into Markdown. It supports files, URLs, and includes AI-powered image analysis capabilities.

## Acknowledgments

- Built with [MarkItDown](https://github.com/path/to/markitdown)
- Uses OpenAI's GPT-4o for image analysis
- Icons from Font Awesome

## Features

- **Multiple Input Methods**:
  - Drag & drop files
  - File selection dialog
  - URL conversion
  - Image analysis with GPT-4o

- **Supported Formats**:
  - PDF documents
  - Word documents (.docx)
  - PowerPoint presentations (.pptx)
  - Excel spreadsheets (.xlsx)
  - Images (PNG, JPG, JPEG, GIF, WEBP)
  - Web pages (via URL)

- **API Integration**:
  - RESTful API for programmatic access
  - cURL support for command-line usage
  - OpenAI integration for image analysis

## Installation

1. Clone the repository:
```bash
git clone https://github.com/CleverCloud/markitdown-converter.git
cd markitdown-converter
```

2. Install dependencies with `uv` (recommended):
```bash
# Install uv if not already installed on Linux, macOS
curl -LsSf https://astral.sh/uv/install.sh | sh

# Install uv if not already installed on Windows
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

uv sync
```

3. Optional: Set environment variables:
```bash
export QUART_ENV=development  # or production
export OPENAI_API_KEY=your-api-key  # or users will have to enter their own
```

## Usage

### Running the application for development

```bash
uv run uvicorn app:app --host 0.0.0.0 --port 8080 --reload
```

### Web Interface

Open your browser and navigate to `http://localhost:8080`. You can:
- Drag and drop files
- Select files using the file dialog
- Convert content from URLs
- Use OpenAI for image analysis (API key required)

### API Usage

Convert a file:
```bash
curl -X POST \
    -F "file=@your_file.pdf" \
    http://localhost:8080/convert
```

Convert from URL:
```bash
curl -X POST \
    -F "url=https://example.com/document.pdf" \
    http://localhost:8080/convert
```

Analyze image with OpenAI:
```bash
curl -X POST \
    -F "file=@image.jpg" \
    -F "api_key=your-openai-key" \
    http://localhost:8080/convert
```
## Deployment on Clever Cloud

1. Install the Clever Tools with `npm` (or [other methods](https://github.com/CleverCloud/clever-tools?tab=readme-ov-file#installation)):
```bash
npm i -g clever-tools
```

2. Login to your Clever Cloud account:
```bash
clever login
```

3. Get this repository and create a new Python application:
```bash
# Clone the repository
git clone https://github.com/CleverCloud/markitdown-converter.git

# Create the application
cd markitdown-converter
clever create -t python
```

4. Configure the required environment variables:
```bash
clever env set QUART_ENV production
clever env set CC_PRE_BUILD_HOOK "uv sync"
clever env set CC_RUN_COMMAND "uv run uvicorn app:app --host 0.0.0.0 --port 9000 --workers 4"
clever env set OPENAI_API_KEY  # if you want to provide your own OpenAI API key
```

5. Deploy your application:
```bash
clever deploy
```

Your application will be available at the URL provided by Clever Cloud. You can access it with:
```bash
clever open
```

Additional deployment commands:
```bash
# Scale your application
clever scale --flavor <flavor>

# Add a domain name
clever domain add <your-domain.com>

# Check application status
clever status

# View application information
clever activity
```

For more details, see the [Clever Cloud Documentation](https://developers.clever-cloud.com/doc).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
