# RecyclerViewPager
A ViewPager implemention base on RecyclerView. Support fling operation like gallary.

android.support.v4.view.ViewPager的完美替代品

## Features:
1. Base on RecyclerView.
2. Custom fling factor.
3. Custom paging trigger.
4. Support Vertical and Horizontal orientation.
5. Support FragmentViewPager (api 12+)
6. Infinite-Loop-ViewPager
7. Support TabLayout

## 特性:
1. 扩展自RecyclerView.
2. 可自定义fling滑动速率.
3. 可自定义翻页触发条件.


![RecyclerViewPager](https://github.com/zyj1609wz/RecyclerViewPager/blob/master/v1.gif)
![RecyclerViewPager](https://github.com/zyj1609wz/RecyclerViewPager/blob/master/v2.gif)


## Usage

### how to import?
add this into gradle

```gradle
// Yes, I have switched to jitpack.io.

repositories {
    ...
    maven { url "https://jitpack.io" }
    ...
}

```
add proguard rules if need

	-keep class com.lsjwzh.widget.recyclerviewpager.**
	-dontwarn com.lsjwzh.widget.recyclerviewpager.**


### Basic Usage:

It is easy to setup like a Recycler List View.

#### xml:

```xml
<com.lsjwzh.widget.recyclerviewpager.RecyclerViewPager
    android:id="@+id/list"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingLeft="15dp"
    android:paddingRight="15dp"
    app:rvp_triggerOffset="0.1"
    app:rvp_singlePageFling="true"
    android:clipToPadding="false"/>
```
#### code:
```java
RecyclerViewPager mRecyclerView = (RecyclerViewPager) view.findViewById(R.id.list);

// setLayoutManager like normal RecyclerView, you do not need to change any thing.
LinearLayoutManager layout = new LinearLayoutManager(getActivity(),LinearLayoutManager.HORIZONTAL,false);
mRecyclerView.setLayoutManager(layout);

//set adapter
//You just need to impelement ViewPageAdapter by yourself like a normal RecyclerView.Adpater.
mRecyclerView.setAdapter(new RecyclerView.Adpater<X>());

// That is all.

```
### Support TabLayout:

#### 1.Add Dependency:
```gradle
dependencies {
    ...
    compile 'com.github.lsjwzh.RecyclerViewPager:tablayoutsupport:v1.1.0-beta5'
    ...
}
```
#### 2.Call 'setupWithViewPager'
```java
TabLayout tabLayout = (TabLayout) findViewById(R.id.tabs);
TabLayoutSupport.setupWithViewPager(tabLayout, mRecyclerView, mAdapter);
```
### Infinite Loop ViewPager:
```xml
<com.lsjwzh.widget.recyclerviewpager.LoopRecyclerViewPager
        android:id="@+id/viewpager"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_marginTop="20dp"
        android:clipToPadding="false"
        android:paddingTop="15dp"
        android:paddingBottom="15dp"/>
```
You just need to use `LoopRecyclerViewPager` replace `RecyclerViewPager`.
The usage of `LoopRecyclerViewPager` is the same as `RecyclerViewPager`.
No matter what you specify position you want to scroll, `LoopRecyclerViewPager` will transform it
 to right position.
Ex:In a `LoopRecyclerViewPager` with 10 items, `scrollToPosition(1)` will get
  same scroll behavior as `scrollToPosition(11)`、`scrollToPosition(21)` and so on.

#### How to get actual position in LoopRecyclerViewPager:
```
    int actualPosition = mLoopRecyclerViewPager.transformToActualPosition(adapterPosition);
```
If you just want to get current actual position, you can do it like this:

```
    int actualCurrentPosition = mLoopRecyclerViewPager.getActualCurrentPosition();
```

### Special Thanks:
[saadfarooq](https://github.com/saadfarooq)
[taxomania](https://github.com/taxomania)

