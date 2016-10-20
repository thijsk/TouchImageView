#TouchImageView library 
[![](https://jitpack.io/v/lnsd/TouchImageView.svg)](https://jitpack.io/#lnsd/TouchImageView)

<p align="center">
	<img src="https://raw.githubusercontent.com/LNSD/TouchImageView/master/artwork/ic_launcher-web.png" width="240">
</p>


Created by: Mike Ortiz - [@MikeOrtiz](https://github.com/MikeOrtiz)

Contributions by:
 * Patrick Lackemacher - [@plackemacher](https://github.com/plackemacher)
 * [@Babay88](https://github.com/Babay88)
 * Ipsilon Developments Inc - [@ipsilondev](https://github.com/ipsilondev)
 * Hank - [@hank-cp](https://github.com/hank-cp)
 * Stephen Paul Weber - [@singpolyma](https://github.com/singpolyma)
 * Julian Villella - [@JVillella](https://github.com/JVillella)
 * Lorenzo Delgado - [@LNSD](https://github.com/LNSD) 

##Capabilities

TouchImageView extends ImageView and supports all of ImageView’s functionality. In addition, TouchImageView adds pinch zoom,dragging, fling, double tap zoom functionality and other animation polish. The intention is for TouchImageView to  mirror as closely as possible the functionality of zoomable images in Gallery  apps.


##How to include in your project:

**Step 1.** Add the JitPack repository to your build file

Add it in your [root build.gradle](https://github.com/LNSD/TouchImageView/blob/master/build.gradle#L21) at the end of repositories:
``` gradle
	allprojects {
		repositories {
			...
			maven { url "https://jitpack.io" }
		}
	}
```

**Step 2.** Add the dependency to your [module build.gradle](https://github.com/LNSD/TouchImageView/blob/master/example/build.gradle):

``` gradle
	dependencies {
	        compile 'com.github.lnsd:TouchImageView:v1.3.1'
	}
```

##Examples

Please view the [sample app](https://github.com/LNSD/TouchImageView/tree/master/example) which includes examples of the following functionality:

####Single TouchImageView

Basic use of a single TouchImageView. Includes usage of `OnTouchImageViewListener`, `getScrollPosition()`, `getZoomedRect()`, `isZoomed()`, and `getCurrentZoom()`.

####ViewPager Example

TouchImageViews placed in a ViewPager like the Gallery app.

####Mirroring Example

Mirror two TouchImageViews using `onTouchImageViewListener` and `setZoom()`.

####Switch Image Example

Click on TouchImageView to cycle through images. Note that the zoom state is maintained though the images are switched.

####Switch ScaleType Example

Click on TouchImageView to cycle through supported ScaleTypes.

##Limitations

TouchImageView does not yet support pinch image rotation.
Also, the [scale types](https://developer.android.com/reference/android/widget/ImageView.html#attr_android:scaleType) `FIT_START` and `FIT_END` are not yet supported.

##Support

Minimum API: 8

##Contributing

Before creating an issue, please make sure that a ticket is not already open. Also,  please check that your issue has not already been fixed in the dev branch. If the issue is reproducible on the dev branch, please provide clear repro instructions in the issue. Last, if you’d like to contribute code, please open all pull requests against the dev branch.

##Usage

Place TouchImageView.java in your project. It can then be used the same as ImageView.

``` java
    TouchImageView img = (TouchImageView) findViewById(R.id.img);
```

If you are using TouchImageView in XML, then you must provide the full package name, because it is a custom view.

``` xml
    <com.ortiz.touchview.TouchImageView
	    android:id="@+id/img”
	    android:layout_width="match_parent"
	    android:layout_height="match_parent" />
```

##API

Get the current zoom. This is the zoom relative to the initial scale, not the original resource.
``` java
    float getCurrentZoom();
```

Get the max zoom multiplier.
``` java
    float getMaxZoom();
```

Get the min zoom multiplier.
``` java
    float getMinZoom();
```

Return the point at the center of the zoomable image. The `PointF` coordinates range in value between 0 and 1 and the focus point is denoted as a fraction from the left and top of the view. For example, the top left corner of the image would be (0, 0). And the bottom right corner would be (1, 1).
``` java
    PointF getScrollPosition();
```

Return a `RectF` representing the zoomed image.
``` java
    RectF getZoomedRect();
```

Returns `false` if image is in initial, unzoomed state. `True`, otherwise.
``` java
    boolean isZoomed();
```

Reset zoom and translation to initial state.
``` java
    void resetZoom();
```

Set the max zoom multiplier. Default value is 3.
``` java
    void setMaxZoom(float max);
```

Set the min zoom multiplier. Default value is 1.
``` java
    void setMinZoom(float min);
```

Set the focus point of the zoomed image. The focus points are denoted as a fraction from the left and top of the view. The focus points can range in value between 0 and 1.
``` java
    void setScrollPosition(float focusX, float focusY);
```

Set zoom to the specified scale. Image will be centered by default.
``` java
    void setZoom(float scale);
```

Set zoom to the specified scale. Image will be centered around the point (focusX, focusY). These floats range from 0 to 1 and denote the focus point as a fraction from the left and top of the view. For example, the top left corner of the image would be (0, 0). And the bottom right corner would be (1, 1).
``` java
    void setZoom(float scale, float focusX, float focusY);
```

Set zoom to the specified scale. Image will be centered around the point (focusX, focusY). These floats range from 0 to 1 and denote the focus point as a fraction from the left and top of the view. For example, the top left corner of the image would be (0, 0). And the bottom right corner would be (1, 1).
``` java
    void setZoom(float scale, float focusX, float focusY, ScaleType scaleType);
```

Set zoom parameters equal to another `TouchImageView`. Including scale, position, and `ScaleType`.
``` java
    void setZoom(TouchImageView img);
```

## License ([tl;dr](https://tldrlegal.com/license/mit-license))

```
The MIT License (MIT)

Copyright (c) 2012-2015 Michael Ortiz

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
