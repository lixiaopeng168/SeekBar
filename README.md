##### 根据BubbleSeekBar修改，如需查看原作者源码请访问
[BubbleSeekBar](https://github.com/woxingxiao/BubbleSeekBar/blob/master/README_zh.md)
### 效果
![修改效果图](https://github.com/lixiaopeng168/SeekBar/tree/master/screenshot/demo5.gif)
## Usage  
### Init in xml
```xml
<com.xw.repo.BubbleSeekBar
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:bsb_bubble_color="@color/color_red_light"
    app:bsb_bubble_text_color="@color/colorPrimaryDark"
    app:bsb_max="50.0"
    app:bsb_min="-50"
    app:bsb_progress="0"
    app:bsb_second_track_color="@color/color_red"
    app:bsb_section_count="5"
    app:bsb_section_text_position="bottom_sides"
    app:bsb_show_progress_in_float="true"
    app:bsb_show_section_mark="true"
    app:bsb_show_section_text="true"
    app:bsb_show_thumb_text="true"
    app:bsb_show_thumb_bitmap="true"
    app:bsb_thumb_width="@dimen/normal_40dp"
    app:bsb_thumb_height="@dimen/normal_50dp"
    app:bsb_track_color="@color/color_red_light"/>
```

### Init in java (not for **_lite_** version)
```java
mBbubbleSeekBar.getConfigBuilder()
               .min(0.0)
               .max(50)
               .progress(20)
               .sectionCount(5)
               .trackColor(ContextCompat.getColor(getContext(), R.color.color_gray))
               .secondTrackColor(ContextCompat.getColor(getContext(), R.color.color_blue))
               .thumbColor(ContextCompat.getColor(getContext(), R.color.color_blue))
               .showSectionText()
               .sectionTextColor(ContextCompat.getColor(getContext(), R.color.colorPrimary))
               .sectionTextSize(18)
               .showThumbText()
               .thumbTextColor(ContextCompat.getColor(getContext(), R.color.color_red))
               .thumbTextSize(18)
               .bubbleColor(ContextCompat.getColor(getContext(), R.color.color_green))
               .bubbleTextSize(18)
               .showSectionMark()
               .seekBySection()
               .autoAdjustSectionMark()
               .sectionTextPosition(BubbleSeekBar.TextPosition.BELOW_SECTION_MARK)
               .build();
```
Check out the demo for more details. Or download the apk: [**sample.apk**](https://github.com/woxingxiao/BubbleSeekBar/raw/master/apk/sample.apk)
## Attentions  
- There are two versions of this library.The differences as follow:  

  version | init | getter/setter
  -------- | ---|---
  lite|xml|min, max, progress
  enhanced|xml, java|all attrs

  **_lite_** version is recommended.
- You must correct the offsets by setting `ScrollListener` when `BubbleSeekBar`'s parent view is scrollable
(such as `ScrollView`, except `ViewPager`), otherwise, the appearing position of the bubble may be wrong. For example:
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

