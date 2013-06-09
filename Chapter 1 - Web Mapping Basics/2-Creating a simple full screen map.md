# Creating a simple full screen map #

当你创建地图相关程序时，首要任务就是创建地图本身。地图是整个应用程序的核心，是数据和数据可视化的载体。

本章节将指引我们创建第一个非常简单的在线地图应用程序。

> 假设你已经配置好自己Web服务器。请记住我们的示例无非就是HTML，CSS和JavaScript代码，因此我们需要一个Web服务器，以便通过浏览器访问我们的程序。

**准备**

编写OpenLayers程序最主要是编写HTML代码，当然，也包括JavaScript代码。所以，我们仅仅需要一个文本编辑器就可以开始我们的工作。

有很多很强大文本编辑器，其中有很多具备web编程特性。因为我们要开始探索的是一个开源项目-OpenLayers，所以我也推荐使用开源的文本编辑器。

对于Windows用户，推荐使用Notepad++（[http://notepad-plus-plus.org](http://notepad-plus-plus.org)），它非常简洁和快捷，提供语法高亮，并且可以通过插件来扩展功能。

另外，除了文本编辑器，你也可以使用集成开发环境，它不仅仅提供语法高亮功能，还包括自动提示、代码跳转等很多功能，让你工作更加事半功倍。

有两个集成开发环境开源项目：[Eclipse](http://www.eclipse.org)和[NetBeans](http://netbeans.org)，两者都是基于Java的项目，可以在所有平台上运行。

<!--more-->

**如何做**

1、创建一个空的index.html文件，然后将下面代码添加进去。先不用理解具体的含义，后面会一步步详细介绍。

{% codeblock lang:html %}
<!DOCTYPE html>
<html>
    <head>
        <title>Creating a simple map</title>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
	    
        <!-- Include OpenLayers library -->
        <script type="text/javascript" src="http://openlayers.org/api/2.11/ OpenLayers.js"></script>
        <style>
        html, body { 
            width: 100%;
            height: 100%;
            margin: 0;
            padding: 0;
        }
        </style>
	
        <!-- The magic comes here -->
        <script type="text/javascript">
        function init() {
            // Create the map using the specified
            // DOM element
            var map = new OpenLayers.Map("rcp1_map");
			
            // Create an OpenStreeMap raster layer and add to the map
            var osm = new OpenLayers.Layer.OSM();
            map.addLayer(osm);
			
            // Set view to zoom maximum map extent
            map.zoomToMaxExtent();
        }
        </script>
    </head>
    <body onload="init()">
        <div id="rcp1_map" style="width: 100%; height: 100%;"></div>
    </body>
</html>
{% endcodeblock %}

2、在浏览器中查看index.html文件，你将看到一个全屏的地图，并且有一些地图控制按钮在左上角，如下图所示:

![](http://fatteru.b0.upaiyun.com/olcb/chapter1/1.2.1.png)

**如何实现的**

让我们一步步揭开谜题。首先，我们创建了一个Html5文档，可以见文档前面的声明`<!DOCTYPE html>`。

在head部分，我们引入了OpenLayers的javascript库，如下所示:

{% codeblock lang:html %}
<script type="text/javascript" src="http://openlayers.org/api/2.11/ OpenLayers.js"></script>
{% endcodeblock %}

同时我们添加了一个Style，让文档充满整个屏幕如下所示：

{% codeblock lang:html %}
<style>
    html, body {
        width: 100%;
        height: 100%;
        margin: 0; 
        padding: 0;
    }
</style>
{% endcodeblock %}

在style元素后面有一些javascript代码，我们放在后面解释。

在head部分后面就是body部分，body有一个`onload`事件，就是说在body部分的内容加载完毕后自动执行`init()`函数。

{% codeblock lang:html %}
<body onload="init()">
{% endcodeblock %}

最后，在body部分我们添加了一个div，并且将其id设置为rcp1_map,这个元素就是Openlayers用来初始化地图的。

同样，我们设置这个元素的样式是其充满父级的全部空间：

{% codeblock lang:html %}
<div id="rcp1_map" style="width: 100%; height: 100%;"></div>
{% endcodeblock %}

现在我们来看看在head部分script元素内容。

如上文所述，使用onload事件会使`init()`函数在页面加载完成后立即执行。

首先我们创建了一个Openlayers.Map对象，也就是渲染在前面提到的div元素，通过DOM元素的id初始化实现的。

{% codeblock lang:js %}
var map = new OpenLayers.Map("rcp1_map");
{% endcodeblock %}

接下来，我们创建了一个栅格图层来显示OpenStreetMaps中的影像。

{% codeblock lang:js %}
// Create an OpenStreeMap raster layer and add to the map
var osm = new OpenLayers.Layer.OSM();
{% endcodeblock %}

创建图层后我们就将其添加到map中：

{% codeblock lang:js %}
map.addLayer(osm);
{% endcodeblock %}

最后，我们将map放大到最大可视范围：

{% codeblock lang:js %}
map.zoomToMaxExtent();
{% endcodeblock %}

**更多...**

记住，我们无法直接使用它。

本书中所有示例并没有编写为独立的应用程序。相反，为了改善用户体验，我们已经创建了一个丰富的应用程序，允许你选择和运行所需的示例，并且可以直接查看源代码。

![](http://fatteru.b0.upaiyun.com/olcb/chapter1/1.2.2.png)

所以在本书编写示例方式略有不同，因为它们依赖应用程序的设计。例如，可能不需要包括OpenLayers的库，因为它可能在程序的另外一个地方已经引用。

另外，在“如何做”部分实现的代码更倾向于独立的应用程序。

如果你查看了此章节的源代码，你会发现代码略微有些不同的地方：

{% codeblock lang:html %}
<!-- Map DOM element -->
<div id="ch1_simple_map" style="width: 100%; height: 95%;"></div>

<!-- The magic comes here -->
<script type="text/javascript">

    // Create the map using the specified DOM element
    var map = new OpenLayers.Map("ch1_simple_map");
    
    // Create an OpenStreeMap raster layer and add to the map
    var osm = new OpenLayers.Layer.OSM();
    map.addLayer(osm);
    
    // Set view to zoom maximum map extent
    map.zoomToMaxExtent();
</script>
{% endcodeblock %}

显而易见的，它包含了我们之前所描述的主要代码。拥有一个div元素来容纳地图，和一个包含所有javascript代码的script元素。

为了创建这个丰富的应用程序，我们使用了[Dojo框架](http://dojotoolkit.org)，它几乎提供了任何所需的功能：访问和修改文档对象结构，事件处理，国际化等等。但我们选择它的主要原因是它提供了一系列组件（标签，按钮，列表等），可以创建非常漂亮又实用的应用程序。

尽管讲解Dojo相关内容超出本书范围，但是它使用相当简单而且也不会影响我们讲解Openlayers内容。