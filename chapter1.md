#1. DecorView
DecorView一般是当前界面的底层容器（即setContentView所设置的父容器）

* 通过activity.getWindow.getDecorView()可以获得DecorView。
* getWindow().getDecorView().findViewById(android.R.id.content)也可以获取DecorView
* 通过getWindow().getDecorView().findViewById(android.R.id.content).getChildAt(0)即可获得Activity所设置的View

DecorView是PhoneWindow的内部类，继承FrameLayout

		public class PhoneWindow extends Window implements MenuBuilder.Callback {
			...
			private final class DecorView extends FrameLayout implements RootViewSurfaceTaker {...}
		}

### 2. DecorView与Activity的关系
我们知道Activity中PhoneWindow对象会创建一个DecorView，窗口顶层视图，然后通过LayoutInflater将xml内容布局解析成View，添加到DecorView中的顶层视图中，其id为android.R.id.content 。总的来说，对于Activity来说，顶层	View就是DecorView。

### 3. DecorView的应用

将view插入到activity的根view中，并且显示是在最顶上

	View view = View.inflate(activity, R.layout.loadingview, null);
	FrameLayout decorView = (FrameLayout) activity.getWindow().getDecorView();
	decorView.addView(view);

可以用来制作EmptyLayout、LoadingView等，用来插入到某个activity中，显示在最顶上.

