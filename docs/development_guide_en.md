# 🛠️ Development Guide

## Setting up Development Environment

```bash
# Clone project
git clone https://github.com/tangsangsimida/EasyKiConverter.git
cd EasyKiConverter

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Linux/Mac
# venv\Scripts\activate  # Windows

# Install dependencies
pip install -r ui/web/requirements.txt
```

## 🌐 Web UI Development

```bash
# Start development server
cd ui/web
python server.py

# Access development interface
# http://localhost:8000
```

**Frontend Development:**
- Modify `index.html` - Page structure
- Modify `css/styles.css` - Styles and animations
- Modify `js/script.js` - Interaction logic

**Backend Development:**
- Modify `server.py` - API interfaces and routing
- Core conversion logic in `easyki/` directory

## 🛠️ Command Line Development

The project is currently under refactoring, and the command-line tool is not yet fully implemented. The core conversion logic is located in the `easyki/` directory.

## 🔧 Code Structure

- **easyki/** - New core conversion engine
  - **easyki/easyeda/** - EasyEDA API and data processing
  - **easyki/kicad/** - KiCad format export engines
  - **easyki/core/** - Core utility functions
  - **easyki/config/** - Configuration management
  - **easyki/utils/** - General utility functions
- **ui/web/** - Flask web application
- **docs/** - Documentation directory
- **scripts/** - Startup scripts

## 🔧 Web UI Options

The Web UI provides a graphical interface to use EasyKiConverter's functionality:

1. Access http://localhost:8000
2. Enter the LCSC part number to convert
3. Select the file types to export (symbols, footprints, 3D models)
4. Click the export button to start conversion

### 📝 Usage Examples

```bash
# Start Web UI server
cd ui/web
python server.py

# Or use startup scripts
./scripts/start_webui.sh  # Linux/Mac
scripts/start_webui.bat   # Windows
```