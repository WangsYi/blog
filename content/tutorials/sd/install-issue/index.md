---
title: "Stable diffusion问题记录"
date: 2023-04-06T13:30:26+08:00
draft: false
tags: ["stable diffusion", "教程"]
---
## Python版本问题

> 运行时直接报错，找不到对应版本的pytorch等错误

解决：
```
python版本安装3.10.x，不要使用最新的3.11+
```

## xformer库报错

```
No module 'xformers'. Proceeding without it
```

解决：
```
# 升级python或者某些情况会出现，需要在web-ui.bat(linux为sh)中添加启动参数 '--reinstall-xformers --xformers'

# 原
:launch
%PYTHON% launch.py %* 
pause
exit /b
# 修改为
:launch
%PYTHON% launch.py %* --reinstall-xformers --xformers 
pause
exit /b
# 运行后会重新安装xformers，安装完后删除此参数
```

## 运行时卡在`DiffusionWrapper has 859.52 M params.`

解决：
```
# 找到venv\Lib\site-packages\huggingface_hub\file_download.py文件中下面部分代码
    # From now on, etag and commit_hash are not None.
    assert etag is not None, "etag must have been retrieved from server"
    assert commit_hash is not None, "commit_hash must have been retrieved from server"
    blob_path = os.path.join(storage_folder, "blobs", etag)
    pointer_path = os.path.join(storage_folder, "snapshots", commit_hash, relative_filename)
```
问题原因是etag有特殊自符\"
解决方法是，先用print(etag)打印出卡住的etag值，例如我的打印出来是类似`/("xxxxxxxxxxxxx`，引号前面不合法，截去，最后修改为
```
    # From now on, etag and commit_hash are not None.
    assert etag is not None, "etag must have been retrieved from server"
    assert commit_hash is not None, "commit_hash must have been retrieved from server"
    print(etag[3:])
    blob_path = os.path.join(storage_folder, "blobs", etag[3:])
    pointer_path = os.path.join(storage_folder, "snapshots", commit_hash, relative_filename)
```