# 📁 Project Structure

```
EasyKiConverter/
├── easyki/                            # Core conversion engine
│   ├── __init__.py                   # Package initialization file
│   ├── config/                       # Configuration module
│   │   └── __init__.py              # Configuration module initialization file
│   ├── core/                         # Core utilities module
│   │   ├── __init__.py              # Core module initialization file
│   │   ├── geometry_utils.py        # Geometry utility functions
│   │   └── symbol_lib_utils.py      # Symbol library utility functions
│   ├── easyeda/                      # EasyEDA API and data processing
│   │   ├── __init__.py              # EasyEDA module initialization file
│   │   ├── easyeda_api.py           # EasyEDA API client
│   │   ├── easyeda_importer.py      # Data importer
│   │   ├── parameters_easyeda.py    # EasyEDA parameter definitions
│   │   ├── svg_path_parser.py       # SVG path parser
│   │   └── __pycache__/             # Python cache directory
│   ├── kicad/                        # KiCad export engine
│   │   ├── __init__.py              # KiCad module initialization file
│   │   ├── export_kicad_3d_model.py # 3D model exporter
│   │   ├── export_kicad_footprint.py# Footprint exporter
│   │   ├── export_kicad_symbol.py   # Symbol exporter
│   │   ├── parameters_kicad_footprint.py # KiCad footprint parameter definitions
│   │   ├── parameters_kicad_symbol.py # KiCad symbol parameter definitions
│   │   └── __pycache__/             # Python cache directory
│   └── utils/                        # Utilities module
│       └── __init__.py              # Utilities module initialization file
├── EasyKiConverter/                  # Legacy conversion engine (to be deprecated)
│   ├── __init__.py                  # Package initialization file
│   ├── requirements.txt             # Dependencies file
│   ├── __pycache__/                 # Python cache directory
│   ├── easyeda/                     # EasyEDA API and data processing
│   ├── kicad/                       # KiCad export engine
│   └── Web_Ui/                      # Web user interface
├── ui/                               # User interface
│   ├── __init__.py                  # Package initialization file
│   └── web/                         # Web interface
│       ├── __init__.py              # Web module initialization file
│       ├── app.py                   # Flask web application
│       ├── config_manager.py        # Configuration manager
│       ├── index.html               # Main page
│       ├── README.md                # Web interface documentation
│       ├── requirements.txt         # Web UI dependencies
│       ├── server.py                # Server
│       ├── user_config.json         # User configuration
│       ├── __pycache__/             # Python cache directory
│       ├── css/                     # Style files
│       │   └── styles.css           # Style file
│       ├── imgs/                    # Image resources
│       │   └── background.jpg       # Background image
│       └── js/                      # JavaScript files
│           └── script.js            # Frontend script
├── docs/                             # Detailed documentation directory
│   ├── contributing_en.md           # Contribution guidelines (English)
│   ├── contributing.md              # Contribution guidelines
│   ├── development_guide_en.md      # Development guide (English)
│   ├── development_guide.md         # Development guide
│   ├── performance_en.md            # Performance optimization (English)
│   ├── performance.md               # Performance optimization
│   ├── project_structure_en.md      # Project structure (English)
│   ├── project_structure.md         # Detailed project structure
│   ├── system_requirements_en.md    # System requirements (English)
│   ├── system_requirements.md       # System requirements
│   └── README.md                    # Documentation index
├── scripts/                          # Scripts directory
│   ├── start_webui.bat              # Windows startup script
│   └── start_webui.sh               # Linux startup script
├── LICENSE                          # GPL-3.0 license
├── README_en.md                     # English documentation
├── README.md                        # Chinese documentation
└── .gitignore                      # Git ignore rules
```

## 📋 Core Module Description

### 🎯 Core Conversion Engine
| Module | Function Description |
|--------|----------------------|
| **easyki/** | New core conversion engine containing all conversion logic |
| **easyki/easyeda/** | EasyEDA API client and data processing module |
| **easyki/kicad/** | KiCad format export engine, supporting symbols, footprints, and 3D models |
| **easyki/core/** | Core utility functions, including geometric calculations and symbol library processing |
| **easyki/config/** | Configuration management module |
| **easyki/utils/** | General utility functions |

### 🌐 Web UI Interface
| Module | Function Description |
|--------|----------------------|
| **ui/web/** | Web user interface |
| **ui/web/app.py** | Flask web application main program, providing REST API and static file services |
| **ui/web/index.html** | Main page, modern user interface with drag-and-drop and real-time feedback |
| **ui/web/css/styles.css** | Style files, frosted glass effects and responsive design |
| **ui/web/js/script.js** | Frontend interaction scripts, handling form submission, progress display, and result presentation |

### 📚 Documentation Directory
| File | Function Description |
|------|----------------------|
| **docs/README.md** | Documentation index, providing links and brief descriptions for all documents |
| **docs/project_structure.md** | Detailed project structure and module descriptions |
| **docs/development_guide.md** | Development environment setup and workflow guide |
| **docs/contributing.md** | Project contribution process and guidelines |
| **docs/performance.md** | Multi-threading parallel processing and performance optimization |
| **docs/system_requirements.md** | System requirements and supported component types |

### 📦 Data Processing Flow
1. **API Retrieval**: Get component data from EasyEDA/LCSC
2. **Data Parsing**: Parse symbol, footprint, and 3D model information
3. **Format Conversion**: Convert to KiCad compatible format
4. **File Generation**: Output .kicad_sym, .kicad_mod and other files