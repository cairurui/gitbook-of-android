# ViewPage-use

offscreenpagelimit 左右缓冲的page数 （中序遍历）

滑动时，fragment其实还是没有被回收的，只是内部的view被回收了。

viewpage使用FragmentPagerAdapter中fragment的总结：

* 1、通过offscreenpagelimit类控制page container 的cache数 n\*2+1
* 2、当加载page超出cache count，会用fragmentManager来释放fragment。
* 3、被释放的fragment实际上不会被完全回收，因为没有被调用onDestroy，下次再初始化时，也没有调用onCreate。
* 4、当fragment被显示在屏幕上时，setUserVisibleHint为true，不显示时为false。


