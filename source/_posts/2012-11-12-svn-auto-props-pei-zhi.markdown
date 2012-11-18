---
layout: post
title: "SVN Auto Props 配置"
date: 2012-11-12 19:20
comments: true
categories: 
---

### 常用的 Property

##### svn:eol-style

行结束字符串，一般设置为 native，这样 Subversion 会基于当前运行的操作系统来设置行结束符。

##### svn:keywords

用于关键字替换，$Id$、$Revision$、$Date$、$Author$ 等。

##### svn:mime-type

用于设置资源文件的 mime type，这样就可以直接在浏览器中查看 HTML、图片等。

### 配置方法

在类 Unix 的平台上，该文件位于 ~/.subversion 目录下。
在 Windows 平台上，该文件位于 C:\Documents and Settings\<user>\Application Data\Subversion 目录下。其中 user 为安装 Subversion 的用户。

找到 "config" 文件后，将 enable-auto-props 设置为 true，并在文件最末尾添加如下内容：

```
*.c = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.cpp = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.h = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.java = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.clj = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.scala = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.cs = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.php  = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.rb  = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.py  = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.jsp  = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.properties = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.ini = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.txt  = svn:keywords=Id Author Revision Rev Date;svn:eol-style=native
*.html = svn:keywords=Id Author Revision Rev Date;svn:mime-type=text/html
*.htm = svn:keywords=Id Author Revision Rev Date;svn:mime-type=text/html
*.xml = svn:keywords=Id Author Revision Rev Date;svn:mime-type=text/xml
*.js = svn:keywords=Id Author Revision Rev Date;svn:mime-type=text/javascript
*.css = svn:keywords=Id Author Revision Rev Date;svn:mime-type=text/css
*.gif = svn:mime-type=image/gif
*.png = svn:mime-type=image/png
*.jpg = svn:mime-type=image/jpeg
```
需要注意的是，这样设置只对新提交的文件生效。对于已经提交的文件，仍然需要手工设置属性。
