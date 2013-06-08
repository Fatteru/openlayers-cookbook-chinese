#Web Mapping Basics-Introduction#

如同每段历史都有一个开始，每份食谱都是从调味料开始。

在正式开始使用Openlayers创建我们自己的地图程序之前，本章先介绍一些基础的必备知识。

正如我们将在本章和接下来的章节所见，OpenLayers是一个庞大而复杂的框架，但同时也非常强大和灵活。

与其他库相比，譬如[Leaflet](http://leafletjs.com/)-一个非常好而且简单的javascript库，OpenLayers试图实现开发者创建一个WebGIS应用所需的所有东西的。因此，在Openlayers中不仅包括是GIS的相关内容，比如地图（map），图层（layer）或标准格式，而且还包括操纵DOM元素或其他来进行异步请求的辅助函数。

我们先暂时不详细说明，在后面的章节中我们将用一张大图来描述Openlayers框架。

在OpenLayers中主要概念就是地图（map）。它表示了信息呈现。地图（map）可以包含任意数量的图层（layer），它可以是栅格或矢量。每一个图层都有一个特定的格式的数据源：PNG图像，KML文件...此外，地图可以包含控件，这有助于与地图及其内容进行交互：平移，缩放，特征选择...

接下来就要正式开始OpenLayers的征途，通过不同的示例来学习OpenLayers。


