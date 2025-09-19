# 🛠️ 开发指南

## 设置开发环境

```bash
# 克隆项目
git clone https://github.com/tangsangsimida/EasyKiConverter.git
cd EasyKiConverter

# 创建虚拟环境
python -m venv venv
source venv/bin/activate  # Linux/Mac
# venv\Scripts\activate  # Windows

# 安装依赖
pip install -r ui/web/requirements.txt
```

## 🌐 Web UI 开发

```bash
# 启动开发服务器
cd ui/web
python server.py

# 访问开发界面
# http://localhost:8000
```

**前端开发：**
- 修改 `index.html` - 页面结构
- 修改 `css/styles.css` - 样式和动画
- 修改 `js/script.js` - 交互逻辑

**后端开发：**
- 修改 `server.py` - API 接口和路由
- 核心转换逻辑在 `easyki/` 目录中

## 🛠️ 命令行开发

目前项目正在重构中，命令行工具尚未完全实现。核心转换逻辑位于 `easyki/` 目录中。

## 🔧 代码结构

- **easyki/** - 新版核心转换引擎
  - **easyki/easyeda/** - EasyEDA API 和数据处理
  - **easyki/kicad/** - KiCad 格式导出引擎
  - **easyki/core/** - 核心工具函数
  - **easyki/config/** - 配置管理
  - **easyki/utils/** - 通用工具函数
- **ui/web/** - Flask Web 应用
- **docs/** - 文档目录
- **scripts/** - 启动脚本

## 🔧 Web UI 选项

Web UI 提供了图形化界面来使用 EasyKiConverter 的功能：

1. 访问 http://localhost:8000
2. 输入要转换的 LCSC 元件编号
3. 选择要导出的文件类型（符号、封装、3D 模型）
4. 点击导出按钮开始转换

### 📝 使用示例

```bash
# 启动 Web UI 服务器
cd ui/web
python server.py

# 或使用启动脚本
./scripts/start_webui.sh  # Linux/Mac
scripts/start_webui.bat   # Windows
```