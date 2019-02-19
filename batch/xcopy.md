
# 踩坑

`xcopy source destination`，其中的source如果是目录的话，目录名不要加`\`，例如以下示例：
```
xcopy c:\test\ d:\test123 # 错误，提示路径无效
xcopy c:\test d:\test123 # 正确
xcopy c:\test\* d:\test123 # 正确
```
