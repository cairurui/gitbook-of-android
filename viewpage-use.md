# ViewPage-use

offscreenpagelimit 左右缓冲的page数 （中序遍历）

滑动时，fragment其实还是没有被回收的，只是内部的view被回收了。

viewpage使用FragmentPagerAdapter中fragment的总结：

* 1、通过offscreenpagelimit类控制page container 的cache数 n\*2+1
* 2、当加载page超出cache count，会用fragmentManager来释放fragment。
* 3、被释放的fragment实际上不会被完全回收，因为没有被调用onDestroy，下次再初始化时，也没有调用onCreate。
* 4、当fragment被显示在屏幕上时，setUserVisibleHint为true，不显示时为false。

而使用FragmentStatePagerAdapter是会完全回收和完全初始化Fragment的。

setUserVisibleHint:当fragment显示在界面上时为true，是系统调用的方法，不需要自己调用。此方法优先于其他生命周期方法。

再次总结：
* FragmentPagerAdapter：是整个View被回收掉了。
* FragmentStatePagerAdapter：是整个Fragment被回收了。

