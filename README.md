# TranslationViewDragHelper
A version of [ViewDragHelper](https://developer.android.com/reference/android/support/v4/widget/ViewDragHelper.html) which accounts for X and Y translations

[![Build Status](https://travis-ci.org/Commit451/TranslationViewDragHelper.svg?branch=master)](https://travis-ci.org/Commit451/TranslationViewDragHelper)
[![](https://jitpack.io/v/Commit451/TranslationViewDragHelper.svg)](https://jitpack.io/#Commit451/TranslationViewDragHelper)

# Usage
If you have ever used a `ViewDragHelper` before, you may have noticed that if you were to translate your views using View.setX() or View.setY(), your helper would no longer correctly allow you to drag the views. This library seeks to correct this. Usage is identical to `ViewDragHelper` usage
```java
TranslationViewDragHelper.Callback callback = new TranslationViewDragHelper.Callback() {
        @Override
        public boolean tryCaptureView(View child, int pointerId) {
            //Any children can be captured
            return true;
        }

        @Override
        public int clampViewPositionHorizontal(View child, int left, int dx) {
            //allow full movement along horizontal axis
            return left;
        }

        @Override
        public int clampViewPositionVertical(View child, int top, int dy) {
            //allow full movement along vertical axis
            return top;
        }
    };

TranslationViewDragHelper viewDragHelper = TranslationViewDragHelper.create(
                                            viewGroup,
                                            1.0f,
                                            callback);
```
See the sample [custom view](https://github.com/Commit451/TranslationViewDragHelper/blob/master/app/src/main/java/com/commit451/betterviewdraghelper/sample/AllowsForDragFrameLayout.java) for a more complete example

# Basis
The current version of this helper is derived from `ViewDragHelper` source from `24.2.0` of the Support Library. Due to private constructor access on ViewDragHelper, the source has to be copied out into the `TranslationViewDragHelper`. You can check the diff [here](https://www.diffchecker.com/)

License
--------

    Copyright 2016 Commit 451

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
