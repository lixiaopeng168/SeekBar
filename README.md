
### 效果
![修改效果图](https://github.com/lixiaopeng168/SeekBar/blob/master/screenshot/demo5.jpeg)


## 本 demo 使用  
###  xml
```xml
 <com.xw.repo.BubbleSeekBar
        android:id="@+id/demo_1_seek_bar_5"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:layout_marginTop="30dp"
        app:bsb_always_show_bubble="true"
        app:bsb_touch_to_seek="true"
        app:bsb_show_thumb_bitmap="true"
        app:bsb_thumb_width="20dp"
        app:bsb_thumb_height="30dp"
        app:bsb_thumb_image="@mipmap/trade_node_tips"
        app:bsb_track_size="4dp"
        app:bsb_second_track_size="4dp"
        app:bsb_bubble_text_size="13dp"
        app:bsb_section_count="4"
        app:bsb_show_section_mark="true"
        app:bsb_thumb_radius="10dp"
        app:bsb_thumb_radius_on_dragging="20dp"
        app:bsb_second_track_color="#32ADF5"
        app:bsb_track_color="#84878F"/>
```

##### 根据BubbleSeekBar修改，详细使用和注意事项查看。
[BubbleSeekBar](https://github.com/woxingxiao/BubbleSeekBar/blob/master/README_zh.md)

### 如需修改成你想要的效果样式，请添加QQ 2305600865。 请备注：seekbar修改

## 注意事项  
- There are two versions of this library.The differences as follow:  

  version | init | getter/setter
  -------- | ---|---
  lite|xml|min, max, progress
  enhanced|xml, java|all attrs

  **_lite_** version is recommended.
- You must correct the offsets by setting `ScrollListener` when `BubbleSeekBar`'s parent view is scrollable
(such as `ScrollView`, except `ViewPager`), otherwise, the appearing position of the bubble may be wrong. For example::
```java
   mContainer.setOnYourContainerScrollListener(new OnYourContainerScrollListener() {
       @Override
       public void onScroll() {
           // call this method to correct offsets
           mBubbleSeekBar.correctOffsetWhenContainerOnScrolling();
       }
   });
```
- When customize the section texts, you should make sure that the attr `bsb_section_text_position`
has been set to `below_section_mark` at first, then follow the example below in your java code:
```java
   mBubbleSeekBar.setCustomSectionTextArray(new BubbleSeekBar.CustomSectionTextArray() {
       @NonNull
       @Override
       public SparseArray<String> onCustomize(int sectionCount, @NonNull SparseArray<String> array) {
           array.clear();
           array.put(1, "bad");
           array.put(4, "ok");
           array.put(7, "good");
           array.put(9, "great");

           return array;
       }
   });
```
##### 如需修改成你想要的效果样式，请添加QQ 2305600865。 请备注：seekbar修改

