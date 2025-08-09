# EasyKiConverter 🔄

**[English](README_en.md)** | [中文](README.md)

一个强大的 Python 工具，用于将嘉立创（LCSC）和 EasyEDA 元件转换为 KiCad 格式，支持符号、封装和 3D 模型的完整转换。提供命令行工具和现代化 Web UI 两种使用方式。

## ✨ 功能特性

### 🎯 核心功能
- **符号转换**：将 EasyEDA 符号转换为 KiCad 符号库（.kicad_sym）
- **封装生成**：从 EasyEDA 封装创建 KiCad 封装（.kicad_mod）
- **3D模型支持**：自动下载并转换 3D 模型（支持多种格式）
- **批量处理**：支持多个元件同时转换
- **版本兼容**：支持 KiCad 5.x 和 6.x+ 版本

### 🌐 Web UI 界面
- **现代化界面**：美观的毛玻璃效果设计
- **实时进度**：转换过程可视化进度条
- **灵活输入**：支持 LCSC 编号或嘉立创链接
- **选择性导出**：可选择导出符号、封装或 3D 模型
- **即时预览**：转换结果实时显示

### 🛠️ 命令行工具
- **脚本自动化**：适合批量处理和 CI/CD 集成
- **参数丰富**：完整的命令行参数支持
- **日志详细**：详细的转换过程日志

## 🚀 快速开始

### 安装

```bash
# 克隆仓库
git clone https://github.com/tangsangsimida/EasyKiConverter.git
cd EasyKiConverter

# 安装依赖（根据使用方式选择）
# 仅命令行工具
pip install -r EasyKiConverter/requirements.txt

# Web UI（推荐）
pip install -r EasyKiConverter/Web_Ui/requirements.txt
```

### 🌐 Web UI 使用（推荐）

```bash
# 方式1：使用启动脚本（Windows）
start_webui.bat

# 方式2：手动启动
cd EasyKiConverter/Web_Ui
python app.py

# 然后在浏览器中访问：http://localhost:8000
```

**Web UI 使用步骤：**
1. 在输入框中输入 LCSC 元件编号（如：C13377）或嘉立创链接
2. 选择要导出的内容：符号、封装、3D模型
3. 设置输出目录和库名称
4. 点击"开始导出"按钮
5. 查看实时进度和转换结果

### 🛠️ 命令行使用

```bash
cd EasyKiConverter

# 转换单个元件（导出所有内容）
python main.py --lcsc_id C13377 --symbol --footprint --model3d

# 仅导出符号
python main.py --lcsc_id C13377 --symbol

# 指定输出目录和库名
python main.py --lcsc_id C13377 --symbol --footprint --output_dir ./my_libs --lib_name MyLibrary
```

## 📁 项目结构

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
| **main.py** | 命令行接口主入口，处理参数解析、验证，协调整个转换流程 |
| **helpers.py** | 共享工具函数，包括日志设置、文件操作、KiCad库管理等 |

### 🌐 Web UI 界面
| 文件 | 功能描述 |
|------|----------|
| **app.py** | Flask Web应用主程序，提供REST API和静态文件服务 |
| **index.html** | 主页面，现代化的用户界面，支持拖拽和实时反馈 |
| **css/styles.css** | 样式文件，毛玻璃效果和响应式设计 |
| **js/script.js** | 前端交互脚本，处理表单提交、进度显示和结果展示 |

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

## 🔧 命令行选项

```bash
python main.py [选项]

必需参数:
  --lcsc_id TEXT         要转换的LCSC元件编号 (如: C13377)

导出选项 (至少选择一个):
  --symbol               导出符号 (.kicad_sym)
  --footprint            导出封装 (.kicad_mod)
  --model3d              导出3D模型

可选参数:
  --output_dir PATH      输出目录路径 [默认: ./output]
  --lib_name TEXT        库文件名称 [默认: EasyKiConverter]
  --kicad_version INT    KiCad版本 (5或6) [默认: 6]
  --overwrite            覆盖现有文件
  --debug                启用详细日志
  --help                 显示帮助信息
```

### 📝 使用示例

```bash
# 导出所有内容到默认目录
python main.py --lcsc_id C13377 --symbol --footprint --model3d

# 仅导出符号到指定目录
python main.py --lcsc_id C13377 --symbol --output_dir ./my_symbols

# 导出到自定义库名
python main.py --lcsc_id C13377 --symbol --footprint --lib_name MyComponents

# 启用调试模式
python main.py --lcsc_id C13377 --symbol --debug
```

## 🛠️ 开发指南

### 设置开发环境

```bash
# 克隆项目
git clone https://github.com/tangsangsimida/EasyKiConverter.git
cd EasyKiConverter

# 创建虚拟环境
python -m venv venv
venv\Scripts\activate  # Windows
# source venv/bin/activate  # Linux/Mac

# 安装依赖
pip install -r EasyKiConverter/Web_Ui/requirements.txt
```

### 🌐 Web UI 开发

```bash
# 启动开发服务器
cd EasyKiConverter/Web_Ui
python app.py

# 访问开发界面
# http://localhost:8000
```

**前端开发：**
- 修改 `index.html` - 页面结构
- 修改 `css/styles.css` - 样式和动画
- 修改 `js/script.js` - 交互逻辑

**后端开发：**
- 修改 `app.py` - API 接口和路由
- 核心转换逻辑在 `../` 目录中

### 🛠️ 命令行开发

```bash
# 运行基本转换测试
cd EasyKiConverter
python main.py --lcsc_id C13377 --symbol --debug

# 测试不同元件类型
python main.py --lcsc_id C25804 --footprint --debug  # 测试封装
python main.py --lcsc_id C13377 --model3d --debug    # 测试3D模型
```

### 🔧 代码结构

- **easyeda/** - EasyEDA API 和数据处理
- **kicad/** - KiCad 格式导出引擎
- **Web_Ui/** - Flask Web 应用
- **main.py** - 命令行入口
- **helpers.py** - 共享工具函数

## 📝 系统要求

### 基本要求
- **Python 3.7+** （推荐 3.8+）
- **网络连接** （访问 EasyEDA/LCSC API）
- **KiCad 5.x 或 6.x+** （使用生成的库文件）

### Python 依赖
- **Flask 2.0+** （Web UI）
- **Flask-CORS** （跨域支持）
- **requests** （HTTP 请求）
- **其他依赖** 见 requirements.txt

### 支持的操作系统
- ✅ Windows 10/11
- ✅ macOS 10.14+
- ✅ Linux (Ubuntu 18.04+)

## 🎯 支持的元件类型

- 🔌 **连接器** - 各种接插件和端子
- 🔧 **分立器件** - 电阻、电容、电感、二极管等
- 💾 **集成电路** - MCU、存储器、运放等
- ⚡ **电源管理** - 稳压器、开关电源芯片等
- 📡 **射频器件** - 天线、滤波器等
- 🔍 **传感器** - 温度、压力、光学传感器等

## 🤝 贡献指南

我们欢迎各种形式的贡献！

### 🐛 报告问题
- 使用 [GitHub Issues](https://github.com/tangsangsimida/EasyKiConverter/issues)
- 提供详细的错误信息和复现步骤
- 包含 LCSC 元件编号和系统信息

### 💡 功能建议
- 在 Issues 中描述新功能需求
- 说明使用场景和预期效果

### 🔧 代码贡献
1. Fork 项目
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建 Pull Request

## 📄 许可证

本项目采用 **GNU General Public License v3.0 (GPL-3.0)** 许可证。

- ✅ 商业使用
- ✅ 修改
- ✅ 分发
- ✅ 专利使用
- ❌ 责任
- ❌ 保证

查看 [LICENSE](LICENSE) 文件了解完整许可证条款。

---

## 🙏 致谢

### 🌟 特别感谢

本项目基于 **[uPesy/easyeda2kicad.py](https://github.com/uPesy/easyeda2kicad.py)** 项目衍生而来。感谢原作者提供的优秀基础框架和核心转换算法，为本项目的开发奠定了坚实的基础。

### 🤝 其他致谢

感谢 [GitHub](https://github.com/) 平台以及所有为本项目提供贡献的贡献者。

我们要向所有贡献者表示诚挚的感谢。

<a href="https://github.com/tangsangsimida/EasyKiConverter/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=tangsangsimida/EasyKiConverter" />
</a>

感谢 [EasyEDA](https://easyeda.com/) 和 [嘉立创](https://www.szlcsc.com/) 提供的开放 API。

感谢 [KiCad](https://www.kicad.org/) 开源电路设计软件。

---

**⭐ 如果这个项目对您有帮助，请给我们一个 Star！**