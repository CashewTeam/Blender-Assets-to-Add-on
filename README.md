# Blender-Assets-to-Add-ons
将 Blender 资产库打包为拓展插件。  
理论上支持 Blender 3.0 之后的版本（因为 3.0 才有资产库），  
测试在 3.6 和 4.2 都能正常使用，在 4.2 以上版本会自动识别为新版的拓展。  

  
Package the Blender asset library as an extension plugin.  
Theoretically, it supports Blender versions after 3.0 (because 3.0 has an asset library).   
It has been tested to work normally in 3.6 and 4.2. It will be automatically recognized as an extension in versions above 4.2.  

# 如何使用 How to use
## 1. 下载仓库 Download this repositorie
点击绿色的Code按钮或者从Releases下载项目zip文件。  
Click the green Code button or download the project zip file from Releases.

## 2. 修改资产目录名称 Change the asset catalog name
Edit __init__.py  
资产库目录名需要与资产库名称相同 The asset library directory name must be the same as the asset library name.
``` python
ASSET_LIBRARY_NAME = "YourAssetsName"
```
## 3. 自定义拓展信息 Custom extension information

### 对于旧版拓展（4.2以下版本） For Add-ons (versions below 4.2)  
Edit __init__.py
``` python
bl_info = {
    "name": "Your add-on name 拓展名称",
    "version": (1, 0, 0),
    "blender": (3, 0, 0),
    "category": "Assets",
}
```
### 对于新版拓展 （4.2及以上版本） For extensions (version 4.2 and above)
Edit blender_manifest.toml
``` toml
schema_version = "1.0.0"

# Example of manifest file for a Blender extension
# Change the values according to your extension
id = "extension_id"
version = "1.0.0"
name = "extension name 拓展名称"
tagline = "extension describe"
maintainer = "Author 作者 <email@address.com>"
# Supported types: "add-on", "theme"
type = "add-on"

# # Optional: link to documentation, support, source files, etc
# website = "https://extensions.blender.org/add-ons/my-example-package/"

# # Optional: tag list defined by Blender and server, see:
# # https://docs.blender.org/manual/en/dev/advanced/extensions/tags.html
tags = ["Geometry Nodes", "Render"]

blender_version_min = "4.2.0"
```
## 4. 导入资产文件夹 Import assets folder
将你的资产文件夹内容放入拓展目录下的`YourAssetsName`文件夹（第二步中输入的名称）  
Place the contents of the assets folder into a folder called `YourAssetsName` in the extension directory (the name you entered in step 2)  


## 5. 打包并测试 Package and test
打包拓展目录并安装测试加载是否正常，确保最终目录结构如下所示。  
Package the expansion directory and install it to test, Make sure the final directory structure looks like this.

```
my_extension-0.0.1.zip
├─ my_extension
  ├─ YourAssetsName
    ├─blender_assets.cats.txt
    ├─Assets.blend
  ├─ __init__.py
  ├─ blender_manifest.toml
  └─ (...)
```

