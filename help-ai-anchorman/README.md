# Help AI Anchorman

## "Failed to fetch" 错误解决方案

Godot 4 Web 导出后,直接双击 `help_ai_anchorman.html` 打开会报错:

```
TypeError: Failed to fetch
```

### 原因

Godot Web 导出生成 `.wasm` 和 `.pck` 文件,浏览器在 `file://` 协议下出于安全限制无法 fetch 这些文件。必须通过 HTTP 服务器访问。

### 解决方法

在 `help-ai-anchorman` 目录下运行:

```powershell
.\run_web.ps1
```

脚本会自动:
1. 启动本地 HTTP 服务器(端口 8060)
2. 打开浏览器访问游戏页面

### 手动启动

如果不使用脚本,可手动执行:

```powershell
# Python 方式
python -m http.server 8060

# Node.js 方式
npx http-server -p 8060
```

然后在浏览器访问 `http://localhost:8060/help_ai_anchorman.html`

### 部署到服务器

上传到任意 HTTP 服务器(GitHub Pages、Netlify、Vercel 等)即可正常访问,无需本地服务器。

## 项目结构

- `project.godot` - Godot 项目配置
- `Scenes/` - 场景文件
- `Scripts/` - GDScript 脚本
- `assets/` - 美术资源
- `export_presets.cfg` - 导出预设
- `help_ai_anchorman.html` - Web 导出主页面
- `help_ai_anchorman.wasm` - WebAssembly 引擎
- `help_ai_anchorman.pck` - 游戏资源包
- `help_ai_anchorman.js` - 引擎加载脚本
