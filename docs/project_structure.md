# 📁 项目结构

```
EasyKiConverter/
├── EasyKiConverter/                    # 核心转换引擎
│   ├── main.py                        # 命令行工具主入口
│   ├── helpers.py                     # 工具函数和辅助功能
│   ├── easyeda/                       # EasyEDA API 和数据处理
│   │   ├── easyeda_api.py            # EasyEDA API 客户端
│   │   ├── easyeda_importer.py       # 数据导入器
│   │   └── parameters_easyeda.py     # EasyEDA 参数定义
│   ├── kicad/                        # KiCad 导出引擎
│   │   ├── export_kicad_symbol.py    # 符号导出器
│   │   ├── export_kicad_footprint.py # 封装导出器
│   │   ├── export_kicad_3d_model.py  # 3D模型导出器
│   │   └── parameters_kicad_symbol.py # KiCad 参数定义
│   └── Web_Ui/                       # Web 用户界面
│       ├── app.py                    # Flask Web 应用
│       ├── index.html                # 主页面
│       ├── css/styles.css            # 样式文件
│       ├── js/script.js              # 前端脚本
│       ├── imgs/background.jpg       # 背景图片
│       └── requirements.txt          # Web UI 依赖
├── docs/                              # 详细文档目录
│   ├── README.md                     # 文档索引
│   ├── project_structure.md          # 项目结构详细说明
│   ├── development_guide.md          # 开发指南
│   ├── contributing.md               # 贡献指南
│   ├── performance.md                # 性能优化说明
│   ├── system_requirements.md        # 系统要求
│   ├── project_structure_en.md       # 项目结构（英文版）
│   ├── development_guide_en.md       # 开发指南（英文版）
│   ├── contributing_en.md            # 贡献指南（英文版）
│   ├── performance_en.md             # 性能优化说明（英文版）
│   └── system_requirements_en.md     # 系统要求（英文版）
├── start_webui.bat                    # Windows 启动脚本
├── LICENSE                           # GPL-3.0 许可证
├── README.md                         # 中文文档
├── README_en.md                      # 英文文档
└── .gitignore                       # Git 忽略规则
```

## 📋 核心模块说明

### 🎯 命令行工具
| 文件 | 功能描述 |
|------|----------|
| **main.py** | 命令行界面主入口，处理参数解析、验证，并协调整个转换过程 |
| **helpers.py** | 共享工具函数，包括日志设置、文件操作、KiCad库管理等 |

### 🌐 Web UI 界面
| 文件 | 功能描述 |
|------|----------|
| **app.py** | Flask Web应用主程序，提供REST API和静态文件服务 |
| **index.html** | 主页面，现代化的用户界面，支持拖拽和实时反馈 |
| **css/styles.css** | 样式文件，毛玻璃效果和响应式设计 |
| **js/script.js** | 前端交互脚本，处理表单提交、进度显示和结果展示 |

### 📚 文档目录
| 文件 | 功能描述 |
|------|----------|
| **README.md** | 文档索引，提供所有文档的链接和简要说明 |
| **project_structure.md** | 详细的项目结构和模块说明 |
| **development_guide.md** | 开发环境设置和开发流程指南 |
| **contributing.md** | 项目贡献流程和规范 |
| **performance.md** | 多线程并行处理和性能优化说明 |
| **system_requirements.md** | 系统要求和支持的元件类型 |

### 🔧 核心引擎
| 模块 | 功能描述 |
|------|----------|
| **easyeda/** | EasyEDA API客户端和数据处理模块 |
| **kicad/** | KiCad格式导出引擎，支持符号、封装和3D模型 |

### 📦 数据处理流程
1. **API获取**：从EasyEDA/LCSC获取元件数据
2. **数据解析**：解析符号、封装和3D模型信息
3. **格式转换**：转换为KiCad兼容格式
4. **文件生成**：输出.kicad_sym、.kicad_mod等文件