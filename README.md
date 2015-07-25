### Overview of JCropImageView

One of the popular scaletype configurations used in Android is the "centerCrop". However, it is limited to just center cropping. This usually crops off the faces of people from images that have an aspect ratio height > width. 

JCropImageView extends on the centercrop feature to provide additional control over how the images are displayed. For example in the screenshot below:

- JCropImageView is used on the top, and it shows IronMan's face. 
- ImageView (Android Default) with centerCrop is shown below, and only the body is shown.

[fill_top1] https://raw.githubusercontent.com/jimcoven/JCropImageView/master/screens/fill_top1.jpg "pic1"

In total, JCropImageView provides 11 configurations
 
* FitWidth  - 3 configurations - TOP/BOTTOM/CENTER
* FitHeight - 3 configurations - CENTER/LEFT/RIGHT
* FitBest   - 5 configurations - TOP/BOTTOM/CENTER/LEFT/RIGHT depending on which scale is used.
 
Note: The configurations for FitWidth + LEFT/RIGHT are correct, but they doesn't show any visual difference. This is because when an image is fit to width, the full width is already within the visible left and right bounds. They are effectively ALWAYS aligned LEFT and RIGHT.
 
Similarly for FitHeight, it is effectively ALWAYS aligned TOP and BOTTOM

THe configurations are more visible with FitBest, which will decide which bound to fit to. The default android scaleType=centerCrop is effectively 1 of the above configurations FitBest + CENTER

### How to use JCropImageView

A) Simply include the repository and dependency in your build.gradle file

```
repositories {
    mavenCentral()
}
dependencies {
    compile 'com.github.jimcoven:jcropimageview:0.1'
}
```

Just create an imageview as usual in xml. Then specify the configurations "app:cropType" and "app:cropAlign".
If "app:cropType" is not specified, this reverts back to the default behaviour an Android ImageView.

```
<com.github.jimcoven.view.JCropImageView
    android:id="@+id/image_view"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:cropType="fit_width"
    app:cropAlign="top"
/>
```

### Supported configurations are:

Supported configurations for "app:cropType" are:
* fit_width : Stretch to fit width
* fit_fill  : Stretch to fit width or height to fill
* fit_height: Stretch to fit height

Supported configurations for "app:cropAlign" are:
* top    : align top edge
* bottom : align bottom edge
* center : align center
* left   : align left edge
* right  : align right edge


