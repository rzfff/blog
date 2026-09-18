# AnHappy 的博客

个人博客源码仓,基于 **Hexo 8** + **Butterfly 5.7** 主题构建,中文站点,
线上地址:<https://anhappy.com/blog/>

## 结构

```text
source/_posts/          文章(Markdown)
source/css/custom/      自定义样式(渐变一体背景/透明卡片/pace 加载指示器/评论美化等 5 件)
source/js/custom/       自定义脚本(评论修复/页脚运行时长)
source/twikoo/          评论前端(自托管,与后端同版本)
source/fontawesome/     自托管字体图标(零外部 CDN)
source/infinitegrid/    自托管画廊组件(零外部 CDN)
themes/butterfly/       主题(独立 git 库,钉在上游 jerryc127/Butterfly,Apache-2.0)
_config.yml             站点配置(url/子路径 root=/blog/)
_config.butterfly.yml   主题配置(评论 twikoo/代码块样式/菜单/注入等)
```

## 构建与部署

构建在服务器上进行(Node 24):

```bash
cd /opt/services/blog
npx hexo clean && npx hexo generate
rm -rf /opt/services/www/blog && mkdir -p /opt/services/www/blog
cp -a public/. /opt/services/www/blog/        # nginx /blog/ 指向这里
```

主题升级:`cd themes/butterfly && git fetch && git reset --hard origin/master`,
再对照 `_config.butterfly.yml` 与新版默认配置的差异。

## 评论

后端 [Twikoo](https://twikoo.js.org/) 自托管于 `https://anhappy.com/twikoo/`,
前端 JS 自托管在 `source/twikoo/`(与后端版本保持一致)。

## 写新文章

Markdown 放 `source/_posts/` → 重新构建部署(流程同上)。

## 版权

- 文章内容 © AnHappy
- 主题 Butterfly 遵循 [Apache-2.0](https://github.com/jerryc127/Hexo-Theme-Butterfly/blob/master/LICENSE)
- 构建产物中引用的前端库版权归各自作者
