# sublime配置

## 公式显示
- 安装插件Markdown Preview
- 添加user配置如下，配置mathjax

```
   "js": [
        "https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js",
        "res://MarkdownPreview/js/math_config.js",
    ],
    "markdown_extensions": [
        {
            "pymdownx.arithmatex": { 
                "generic": true 
            }
        }
    ],
```