# TikZ Magic 错误修复

## 问题

运行 tikz cell 时出现错误：`pdflatex terminated with signal 1` 或 `CommandNotFoundException`

## 原因

`tikzmagic` 扩展需要 LaTeX 环境来编译和渲染 TikZ 图形。Windows 系统默认没有安装 LaTeX。

## 解决方案

### 方案1：安装 MiKTeX（推荐，较小）

1. 下载 MiKTeX：
   - 访问：https://miktex.org/download
   - 下载 Windows 安装程序

2. 安装 MiKTeX：
   - 运行安装程序
   - 选择 "Install packages on-the-fly: Yes"（推荐）
   - 完成安装

3. 验证安装：
   ```powershell
   pdflatex --version
   ```

4. 重启 Jupyter Notebook 或重新加载扩展：
   ```python
   %reload_ext tikzmagic
   ```

### 方案2：安装 TeX Live（完整，较大）

1. 下载 TeX Live：
   - 访问：https://www.tug.org/texlive/
   - 下载 Windows 安装程序

2. 安装（需要较长时间，约 4GB）

3. 验证安装并重启 Jupyter

### 方案3：跳过 TikZ Cells（临时方案）

如果不需要显示电路图，可以：
1. 跳过运行 tikz cell（它们是可选的，只是用于可视化）
2. 或者将 tikz cell 改为 markdown 说明

### 方案4：使用在线 LaTeX 服务（不推荐）

某些工具可以连接到在线 LaTeX 服务，但通常配置较复杂。

## 验证修复

安装 LaTeX 后，运行以下测试：

```python
%%tikz
\draw (0,0) circle (1cm);
```

如果显示一个圆圈，说明安装成功。

## 注意事项

- MiKTeX 安装后，第一次使用某些包时可能需要下载，这可能需要一些时间
- 确保 MiKTeX 的 `bin` 目录在系统 PATH 中（安装程序通常会自动处理）
- 如果仍有编码错误，可能是 Windows 命令行编码问题，可以尝试设置环境变量 `PYTHONIOENCODING=utf-8`

