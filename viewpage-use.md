# ViewPage-use

offscreenpagelimit 左右缓冲的page数 （中序遍历）

滑动时，fragment其实还是没有被回收的，只是内部的view被回收了。

viewpage中fragment的总结：
* 1、通过offscreenpagelimit类控制page container 的cache数 n*2+1
