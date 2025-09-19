# 📁 项目结构

```
EasyKiConverter/
├── easyki/                            # 核心转换引擎
│   ├── __init__.py                   # 包初始化文件
│   ├── config/                       # 配置模块
│   │   └── __init__.py              # 配置模块初始化文件
│   ├── core/                         # 核心工具模块
│   │   ├── __init__.py              # 核心模块初始化文件
│   │   ├── geometry_utils.py        # 几何工具函数
│   │   └── symbol_lib_utils.py      # 符号库工具函数
│   ├── easyeda/                      # EasyEDA API 和数据处理
│   │   ├── __init__.py              # EasyEDA模块初始化文件
│   │   ├── easyeda_api.py           # EasyEDA API 客户端
│   │   ├── easyeda_importer.py      # 数据导入器
│   │   ├── parameters_easyeda.py    # EasyEDA 参数定义
│   │   ├── svg_path_parser.py       # SVG路径解析器
│   │   └── __pycache__/             # Python缓存目录
│   ├── kicad/                        # KiCad 导出引擎
│   │   ├── __init__.py              # KiCad模块初始化文件
│   │   ├── export_kicad_3d_model.py # 3D模型导出器
│   │   ├── export_kicad_footprint.py# 封装导出器
│   │   ├── export_kicad_symbol.py   # 符号导出器
│   │   ├── parameters_kicad_footprint.py # KiCad封装参数定义
│   │   ├── parameters_kicad_symbol.py # KiCad符号参数定义
│   │   └── __pycache__/             # Python缓存目录
│   └── utils/                        # 工具模块
│       └── __init__.py              # 工具模块初始化文件
├── EasyKiConverter/                  # 旧版转换引擎（将被弃用）
│   ├── __init__.py                  # 包初始化文件
│   ├── requirements.txt             # 依赖文件
│   ├── __pycache__/                 # Python缓存目录
│   ├── easyeda/                     # EasyEDA API 和数据处理
│   ├── kicad/                       # KiCad 导出引擎
│   └── Web_Ui/                      # Web 用户界面
├── ui/                               # 用户界面
│   ├── __init__.py                  # 包初始化文件
│   └── web/                         # Web界面
│       ├── __init__.py              # Web模块初始化文件
│       ├── app.py                   # Flask Web 应用
│       ├── config_manager.py        # 配置管理器
│       ├── index.html               # 主页面
│       ├── README.md                # Web界面说明
│       ├── requirements.txt         # Web UI 依赖
│       ├── server.py                # 服务器
│       ├── user_config.json         # 用户配置
│       ├── __pycache__/             # Python缓存目录
│       ├── css/                     # 样式文件
│       │   └── styles.css           # 样式文件
│       ├── imgs/                    # 图片资源
│       │   └── background.jpg       # 背景图片
│       └── js/                      # JavaScript文件
│           └── script.js            # 前端脚本
├── docs/                             # 详细文档目录
│   ├── contributing_en.md           # 贡献指南（英文版）
│   ├── contributing.md              # 贡献指南
│   ├── development_guide_en.md      # 开发指南（英文版）
│   ├── development_guide.md         # 开发指南
│   ├── performance_en.md            # 性能优化说明（英文版）
│   ├── performance.md               # 性能优化说明
│   ├── project_structure_en.md      # 项目结构（英文版）
│   ├── project_structure.md         # 项目结构详细说明
│   ├── system_requirements_en.md    # 系统要求（英文版）
│   ├── system_requirements.md       # 系统要求
│   └── README.md                    # 文档索引
├── scripts/                          # 脚本目录
│   ├── start_webui.bat              # Windows 启动脚本
│   └── start_webui.sh               # Linux 启动脚本
├── LICENSE                          # GPL-3.0 许可证
├── README_en.md                     # 英文文档
├── README.md                        # 中文文档
└── .gitignore                      # Git 忽略规则
```

## 📋 核心模块说明

### 🎯 核心转换引擎
| 模块 | 功能描述 |
|------|----------|
| **easyki/** | 新版核心转换引擎，包含所有转换逻辑 |
| **easyki/easyeda/** | EasyEDA API客户端和数据处理模块 |
| **easyki/kicad/** | KiCad格式导出引擎，支持符号、封装和3D模型 |
| **easyki/core/** | 核心工具函数，包括几何计算和符号库处理 |
| **easyki/config/** | 配置管理模块 |
| **easyki/utils/** | 通用工具函数 |

### 🌐 Web UI 界面
| 模块 | 功能描述 |
|------|----------|
| **ui/web/** | Web用户界面 |
| **ui/web/app.py** | Flask Web应用主程序，提供REST API和静态文件服务 |
| **ui/web/index.html** | 主页面，现代化的用户界面，支持拖拽和实时反馈 |
| **ui/web/css/styles.css** | 样式文件，毛玻璃效果和响应式设计 |
| **ui/web/js/script.js** | 前端交互脚本，处理表单提交、进度显示和结果展示 |

### 📚 文档目录
| 文件 | 功能描述 |
|------|----------|
| **docs/README.md** | 文档索引，提供所有文档的链接和简要说明 |
| **docs/project_structure.md** | 详细的项目结构和模块说明 |
| **docs/development_guide.md** | 开发环境设置和开发流程指南 |
| **docs/contributing.md** | 项目贡献流程和规范 |
| **docs/performance.md** | 多线程并行处理和性能优化说明 |
| **docs/system_requirements.md** | 系统要求和支持的元件类型 |

### 📦 数据处理流程
1. **API获取**：从EasyEDA/LCSC获取元件数据
2. **数据解析**：解析符号、封装和3D模型信息
3. **格式转换**：转换为KiCad兼容格式
4. **文件生成**：输出.kicad_sym、.kicad_mod等文件