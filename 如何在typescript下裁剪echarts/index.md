## 前端风云：react下，typescript中，如何减少echarts图表库的包体积（echarts-for-react的情况）

> 前提概要：最近笔者在某公司实习的时候，负责开发一个内部数据展示网站的前端。当时图标展示库选用的是echarts，由于整体网站的技术栈是react，因此找了一个echarts的react包装库echarts-for-react。开发告一段落后，开始了喜闻乐见的扣包环节。本文就是记载从echarts中抠出400KiB的心路历程。

### 背景知识简介

**这里的故事有点长，对背景知识不感兴趣的同学可以跳过。**

没有开发过用于生产环境网站的前端同学可能会问：包体积是什么？扣包是什么？

在大前端语境下，javascript不仅仅负责前端的基本交互，而且负责表现层的渲染，一个典型的前端渲染网站的特征是，一开始html不需要复杂的内容，只需要引用script，加载好后js就会不断的修改html的body。下面是一个典型的例子，html没有任何东西，全靠js来渲染。当然这是一个理想化例子，现实中的网站即使是前端渲染html也不会这么简洁，script也可以内嵌到html内。

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width,initial-scale=1,shrink-to-fit=no">
        <meta name="theme-color" content="#000000">
        <link rel="manifest" href="/map/manifest.json">
        <link rel="shortcut icon" href="/map/favicon.ico">
        <title>Real Estate Map</title>
        <link href="/map/static/css/main.1c763e03.css" rel="stylesheet">
    </head>
    <script type="text/javascript" src="https://api.map.baidu.com/api?v=2.0&ak=BKGsE7oSVQyGDwG77CRCtfa9VFDA52Os"></script>
    <body>
        <noscript>You need to enable JavaScript to run this app.</noscript>
        <div id="root" class="map"></div>
        <script type="text/javascript" src="/map/static/js/main.59e05caa.js"></script>
    </body>
</html>

```

更有甚者将路由放到前端，在页面间跳转不再需要后端完成，完全交由前端。你会看到浏览器即使地址栏变了，整个页面也不会刷新一下（因为我们始终使用一个html，内容变化由js负责），这就给用户提供了一个很好的体验，这也就是我们常说的单页应用(SPA)。大家可以到Google Drive感受一下。

就这样前端的负责的部分越来越重，逻辑代码和引用的库也越来越多。如果是单页应用，好几个不同页面，不同页面为完成不同功能再带上他们的各自依赖包，体积瞬间爆炸，巨大的包体积会导致浏览器首页加载过长，用户体验就会很差。

但很多时候，我们会发现我们写的代码体积并不大，实际是引用的包，譬如这里的echarts，即使压缩后依然占800KiB，导致了包体积的膨胀，因此扣包的一个环节，裁剪依赖库，其实自js模块化开始即有之。echarts很优秀，包含很多炫酷的功能，但我只使用的最基础的图标库，于是这里就由了裁剪的空间。下面这张图无声地控诉了依赖包的体积过大问题。

![](./1.png)

### 如何在typescript下裁剪echarts

如果你是使用js，echarts裁剪方法，请参考[echarts-for-react](https://github.com/hustcc/echarts-for-react#2-usage)

主要思路是使用ReactEchartsCore这一组件，再把定制的echarts传给它

但如果你使用了typescript，就会typescript抛出以下错误。

```
src/Simple.tsx:4:30 - error TS7016: Could not find a declaration file for module 'echarts-for-react/lib/core'. '/mnt/c/wsl-workspace/test/node_modules/echarts-for-react/lib/core.js' implicitly has an 'any' type.
  Try `npm install @types/echarts-for-react` if it exists or add a new declaration (.d.ts) file containing `declare module 'echarts-for-react';`

4 import ReactEchartsCore from 'echarts-for-react/lib/core';
                               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

为什么会这样子呢？使用ReactEcharts是能通过typescript编译的啊？

分析错误并查阅一些资料后，我决定直接在`node_modules`修改它的库代码，具体这么修改呢？请看[file changes](https://github.com/hustcc/echarts-for-react/pull/225/files)。

幸运的是，仓库所有者已经merge这个pull request，并发了一版，因此，你只要升级这个库，并确定你使用的库版本是大于`echarts-for-react@2.0.15-beta.0`，就不需要手动修改库文件了。（可以通过查看package.json，来决定版本号）

如果低于这个版本，如何升级呢？

```
npm update echarts-for-react
```

另外我针对这种情况建了一个[示例仓库](https://github.com/xsthunder/react-example-echarts-for-react-reduce-echarts-bundle-size-in-ts)，里面包括最基础的示例和包体积的分析，如果还是有问题可以参考一下。