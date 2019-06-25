

## API设计原则

尽量遵循REST风格，详细规范如下

<https://java.timoney.xyz/qi-restful-she-ji-gui-fan>

这里列出几条自己的经验

- `GET`只能用来获取数据，坚决不能用来修改数据或者删除数据，不能妄想用`PathVariable`或者`RequestParam`代替其他方法，因为`GET`是最常用的获取数据的方法，曾经我就有过一次用`GET`方法写了个删除所有用户的`api`，然后经常会有数据清空的情况出现，查了运行`log`发现是谷歌的爬虫在半夜三四点调用了这个方法，真的问题很大！
- 子路径名尽量用名词，如果需要用动词尽量通过GET、POST、DELETE、PUT这些方法的含义来代替
  - 比如获取用户信息就不要用/get/user，直接用GET方法的/user就好了
  - 比如修改用户信息就不要用/user/modify，直接用PUT方法的/user就好了
- 每个子路径名都要用单个单词
  - 如/getUser，直接用/user
  - 如/fillQuestionnaire，直接用questionnaire/{id}/fill
- 提交数据用POST，修改数据用PUT，PUT要遵循幂等性，就是连续调用多次该API，数据不会有问题，详细的原因就不细说了
- REST的精髓就是资源，所以同一类资源要放在同一子目录下
  - 比如/fill/questionnaire和/collect/questionnire就不如把questionnaire作为公共子路径写成/questionnire/fill和/quesitonnire/collect



## API结构

[详细文档地址](https://documenter.getpostman.com/view/7006450/S1LzynKU?version=latest#ee6844e6-30c6-4637-a01d-c49eef6117fe)

本来可以通过 api.timoney.xyz 轻轻松松访问的

因为国外买的域名（本来图不用备案）最后还是被某讯云发现了，于是只能用服务器ip加端口访问

其实还是有注意点的，主要是有个上传图片（用于保存用户头像）的`api`需要把文件保存在服务器上，所以不要把图片类型的请求给拦截到，关键配置如下

    location ~ .*\.(gif|jpg|jpeg|png|bmp|swf)$
    {
        expires      30d;
        error_log off;
        access_log off;
    }
另外就是要把网站设置为默认网站，因为要通过ip访问上传的头像，一个服务器有多个网站，不设置默认网站就无法找到正确的路径