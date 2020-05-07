# 常用命令

## tar
压缩／解压缩文件
```
tar -cvzf target.tar source/
tar -xf source.tar
```

被压缩文件不想要目录结构
```
tar -cvzf target.tar -C source_dir source_files
```