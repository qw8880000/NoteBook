
## vim 编辑的中文注释在source insight下乱码

原因：source insight 不支持utf-8编码，支持的是cp936
解决：使用`iconv`来转换编码，例如`iconv -f utf-8 -t cp936 file1.txt -o file1.txt`

## 为什么 vim 编辑变慢

有可能是因为输入的字符与快捷键冲突

