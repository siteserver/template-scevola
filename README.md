**模版演示地址：** http://theme.demo.siteserver.cn/scevola/index.html

如果还未安装产品的特提供相应链接：

**产品下载：** http://cms.siteserver.cn

**产品安装：** http://docs.siteserver.cn/getting-started/index.html

**模版下载：** http://templates.siteserver.cn/t-scevola/index.html

**新建站点：** http://docs.siteserver.cn/getting-started/create.html

这次，我们提供了一套企业模板，一套响应式网站模版，适应于企业、科技、个人博客、互联网、媒体等产品型公司以及各种企业集团网站模板所有图片在手机端都进行过处理，简单而又清爽的企业、博客响应式网站模板。

**一、首页(栏目页)**
**二、树状结构页**
**三、内容页**
**四、福利篇**

**一、首页(栏目页)**

![](/assets/image001.png)
 
这里扯点本模版之外的事，个人来说，拿到一套网站或者说模版，我喜欢第一时间进入到后台，看看它的信息管理或者栏目管理（因为这是最容易或直接知道一个网站结构的地方。可能有人会说，看看前台导航不就行了，是的，是有些网站前台导航结构就反应整个网站的结构，前台页面很多干扰，注意有以下几个地方：页面容易遗漏、不直观、有些栏目不在导航栏目显示）
 
![](/assets/image002.png)

我们可以看到，整个网站的栏目结构非常简单，结合一下网站前端网页（也可以到显示管理—模版匹配去看看网站模版情况），我们很容易的知道，这个是一个博客型的轻型网站。
那回到这个网站我们会发现干货、动态、服务（其实首页也是）使用了同一个模版页。

![](/assets/image003.png)
 
**1.1 文章列表**
 
![](/assets/image004.png)

通过这个图，我们会发现首页的列表里，第一篇文章跟后面的文章样式是不一样，那我们接下来看看具体的代码（STL语言嵌套）——显示管理——模版管理——首页模版（我们查看模版匹配会知道，首页使用的模版具体是哪一个）

![](/assets/image005.png)
 
<stl:pageContents topLevel="0" isNoDup="true" scope="All" groupChannelNot="not" pageNum="10" order="AddDate">
          <stl:if type="ItemIndex" operate="Equals" value="1">
            <stl:yes>
第一篇文章
</stl:yes>
 <stl:no>
   其他文章
 </stl:no>
</stl:pageContents>

我们大概的解读一下这端代码：
首先外层我们用到了一个标签 <stl:pageContents></stl:pageContents>，这是一个翻页标签，相比普通的内容Contents列表，意味着这个页面是可以翻页的。这也是这两标签的唯一区别，所有他们的属性是共用的，

参考：（ http://stl.siteserver.cn/contents/index.html http://stl.siteserver.cn/pageItems/index.html）我们会知道这里调取的是首页（topLevel="0" ）下所有（scope="All"）不属于栏目组not(groupChannelNot="not")里不重复的（isNoDup="true"）最新（order="AddDate"）文章列表，并且每页显示十条（pageNum="10"）

然后，翻页列表标签里面，用了一个If判断标签http://stl.siteserver.cn/if/index.html，当前项序号（ItemIndex）的值为是否为1（operate="Equals" value="1"），是的时候是什么展现方式，不是的时候又是什么样的。

**1.2首页右侧（网站标签+随机散文）**

![](/assets/image006.png)
 
首先，标签的管理在设置管理——组别和标签设置——内容标签管理

![](/assets/image007.png)
 
在每篇文章的最后的内容标签字段里填上相应的标签即可，像首页右边的这些标签，点击这些标签，就能把有这个标签的文章都给列出来。
 那随机散文用到的调取方式，也就是我们上文讲过的contents内容列表标签。
 
![](/assets/image008.png)

可能有的新人会发现在首页模版里，找不到上图这段代码。先卖个关子，我们把下面这个章节看我就懂了。

**二、树状结构页（关于我们、公司简介）**

![](/assets/image009.png)
 
我们可以看到这个模版页面的左侧是一个树状切换效果，一般我们把这样的公用模块作为包含文件（多个页面共用的部分），比如一般网页的头部、底部。然后再调用到需要的模版页里。

![](/assets/image010.png)
 
比如这里的调取代码<stl:include file="/include/left_nav.html"></stl:include>
这样我们只需要在包含文件left进行嵌套或者修改，那所有用到了这个包含文件的页面都会跟着改变。
我们现在知道上一章节标签和随机热文那段代码在哪了吧，也是在另一个包含文件(aside)里。

**三、内容页**

![](/assets/image011.png)
 
我们会发现内容页跟栏目列表页的基本框架是一样的。只是一个调取的是内容列表（contents）一个调取的是内容（content）
 
![](/assets/image012.png)

**四、福利篇**

本次，我们增加一个实体标签的解读，我们在上图看见的标签里｛Stl.SiteUrl｝

![](/assets/image013.png)
 
这是站点根目录地址的实体标签。为了灵活的调取，我们的模版标签分为STL常规标签和STL实体标签。举个例子：

比如我们调取内容<stl:content type=”title”></stl:content>，它的实体标签{content.Title}  是不是更简单？图片{content.ImageUrl}、内容简介{content. Summary}。像一些站点ID、站点名称等必须用实体标签

实体标签参考:http://stl.siteserver.cn/channels/79.html