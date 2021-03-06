.. index:: ! psscale

psscale
=======

- 官方文档： :ref:`gmt:psscale`
- 简介：在地图上绘制灰色或彩色色条（colorbar）

选项
----

``-B[p|s]<parameters>``
    设置colorbar的标注、刻度和网格线间隔。

    在不使用 ``-B`` 选项，或者不指定标注间隔时，默认会根据CPT文件中每一行的内容对colorbar进行标注，具体见 :doc:`cpt` 。

    ``-B`` 的用法在 :doc:`B-option` 中已经介绍。默认情况下，对于水平colorbar而言，X轴的标签会放在colorbar的下边，Y轴标签放在colorbar的右边；对于垂直colorbar而言，X轴的标签放在colorbar的右边，Y轴标签放在colorbar的上边。

``-C``
    要绘制的CPT文件。

``-D[g|j|J|n|x]<refpoint>+w<length>/<width>[+e[b|f][<length>]][+h][+j<justify>][+m[a|c|l|u]][+n[<txt>]][+o<dx>[/<dy>]]``
    指定色标的尺寸和位置。

    #. ``[g|j|J|n|x]<refpoint>`` 指定底图上的参考量，见 :doc:`embellishments` 一节
    #. ``+j<justify>`` 指定色标上的锚点，默认锚点是 ``BL`` ，见 :doc:`embellishments` 一节
    #. ``+o<dx>[/<dy>]`` 指定参考点的额外偏移量，见 :doc:`embellishments`
    #. ``+w<length>/<width>`` 指定色标的长度和宽度，若长度为负值则会反转色标
    #. ``+h`` 绘制水平色标，默认为垂直色标
    #. ``+e`` 选项为前景色和背景色加一个三角形， ``+ef`` 表示只加前景色三角形， ``+eb`` 表示只加背景色三角形， ``<length>`` 是三角的高度，默认为色标宽度的一半
    #. ``+m[a|c|l|u]`` 将标注、标签和单位放在色标的另一边， ``a`` 代表标注， ``l`` 代表标签， ``u`` 代表单位。 ``c`` 表示将标签以单列字符垂直打印。
    #. ``+n<text>`` 在色标开始处绘制一个矩形，并用NaN的颜色填充

``-F``
    为colorbar加上背景边框，见 :doc:`embellishments` 一节

``-G<zlow>/<zhigh>``
    绘图前先对CPT文件做截断，使得其只绘制 ``<zlow>`` 到 ``<zhigh>`` 之间的部分。若其中某个值等于NaN，则不对CPT的那一端做处理。

``-I[<max_intens>|<low_i>/<high_i>]``
    为色标加上光照效果

    #. ``-I<max_intens>`` 光照强度为 ``[-<max_intens>, +<max_intens]`` ，默认值为1
    #. ``-I<low_i>/<high_i>`` 指定非对称的光照强度范围

``-L[i][<gap>]``
    生成等大小的color rectangels，见官方文档

``-M``
    使用YIQ变换将色标变成单调灰度色标

``-N[p|<dpi>]``
    见官方文档

``-Q``
    使用对数坐标，刻度表示为10的次幂

    CPT文件中所有的Z值都会被转换成 p = log10(z)，其中整数的p会以10^p的格式标注。

``-S``
    去除不同色块之间的黑色网格线

``-Z<zfile>``
    见官方文档

示例
----

::

    gmt makecpt -T-200/1000/100 -Crainbow > t.cpt
    gmt psscale -Ct.cpt -Dx8c/1c+w12c/0.5c+jTC+h -Bxaf+l"topography" -By+lkm > map.ps
