# tornado-ueditor
> ueditor 是百度的开源富文本编辑器，这里参考了 [jcteng/ueditor4tornado](https://github.com/jcteng/ueditor4tornado) , 还有 [grunmin/ueditor-tornado](https://github.com/grunmin/ueditor-tornado) , 后者也是在前者的基础上做出了一些自定义修改。
>
> 根据项目的特点，ueditor4tornado 由于不方便集成与自定义重写一些功能，ueditor-tornado 的修改也不符合需求，所以就参考两者的代码重新做了一些处理。
>
> 项目直接启动就是一个可查看的 demo ，方便理解和自定义修改。

ueditor 文件夹是从官方直接下载的 php 版本，将 config.json 的内容拿出来放到 ueditor.py 里面，处理下成为一个 ueditor_config 字典，放在这里来主要是考虑维护简单，文件也少，读取和渲染与测试也方便，最后删去了不用的 php 目录。

在 ueditor 文件下的 ueditor.config.js 文件中，修改了 `serverUrl: "/upload"` 这个参数，这个url就是上传图片等自行处理的路由，对应的 ueditor.py 里面的`(r'/upload', UploadHandler),` 。

启动 ueditor.py 就能在 `http://127.0.0.1:9009/ueditor` 地址访问到 demo ，图片等文件上传的重命名我修改成直接使用了 uuid 作为文件名，不适合的话你可以自己改下。

对于涂鸦图片传，在 py2 与 py3 环境下有些不同，默认开启的是 py3 适用，如果是在 py2 下，看下第 253 - 256 行自己注释以及启用下。





