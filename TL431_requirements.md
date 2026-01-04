# TL431.ipynb 运行所需库

## 已安装的库

1. **ngspyce** - 已从 GitHub 安装
   ```bash
   pip install git+https://github.com/ignamv/ngspyce.git
   ```

2. **ipython-tikzmagic** - 已从 GitHub 安装
   ```bash
   pip install git+https://github.com/mkrphys/ipython-tikzmagic.git
   ```

3. **numpy** - 已安装
4. **matplotlib** - 已安装

## 需要手动配置的部分

### Ngspice DLL 文件

`ngspyce` 需要在以下位置找到 Ngspice DLL 文件：
- **Windows 64位**: `C:\Spice64\bin_dll\ngspice.dll`
- **Windows 32位**: `C:\Spice\bin_dll\ngspice.dll`

#### 解决方案1：下载官方 Ngspice DLL

从以下地址下载 Ngspice for Windows：
- https://sourceforge.net/projects/ngspice/files/ng-spice-rework/

下载后解压到 `C:\Spice64\` 目录，确保 DLL 文件在 `C:\Spice64\bin_dll\` 目录中。

#### 解决方案2：使用 PySpice 附带的 DLL

如果你已经安装了 PySpice，可以尝试从 PySpice 的安装目录复制 DLL 文件：
- PySpice DLL 位置：`D:\python\lib\site-packages\PySpice\Spice\NgSpice\Spice64_dll\dll-vs\`
- 复制到：`C:\Spice64\bin_dll\`

**注意**：可能需要复制所有相关的 DLL 文件（包括依赖项）。

#### 解决方案3：修改 ngspyce 源代码（高级）

可以修改 `ngspyce` 的源代码来使用不同的路径，但这需要重新安装包。

## 测试安装

运行以下命令测试：
```python
import ngspyce as ng
```

如果导入成功，说明配置正确。

## 其他注意事项

- `ngspyce` 还需要 `C:\Spice64\share\ngspice\` 目录（用于脚本文件）
- 确保所有依赖的 DLL 都在 `C:\Spice64\bin_dll\` 目录中

