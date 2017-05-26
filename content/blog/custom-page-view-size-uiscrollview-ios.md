+++
draft = false
title = "Custom UIScrollview Paging Size"
date = "2016-11-07T18:33:28+07:00"
slug = "custom-uiscrollview-paging-size"
+++

A scroll view's paging size is determined by its bound, and there is no way to adjust it. It's difficult to explain why developer wants to change this size. Consider this calendar scenario where I want to show some preview of the next month.

![custom-date-picker](/images/date-picker.gif)

There is one way that you could achieve this, by setting the scroll view's width with the width of the page you like and set its `clipsToBounds` to `false`. Then, the scroll view will look the way you expect, but the area outside the bounds is not user-interactable, hence it destroys the behavior of scroll view.

If you happened to search for the solution, probably you will come across this [Stackoverflow topic](http://stackoverflow.com/questions/6945964/uiscrollview-custom-paging) with the custom `UIView` subclass, and overriding `hitTest` methods. Well that works, but there is a better way.

From iOS 5 and above, `UIScrollview` instances now have this `panGestureRecognizer` property public. Now you could just use it for the area outside scroll view and have the smooth scrolling behavior. Steps that you need to do:

- `clipsToBounds` to false
- put a `UIView` on top of your `UIScrollView`
- add the scroll view's `panGestureRecognizer` to that view

<script src="https://gist.github.com/khoiln/dc7186fea75c232ac367270a8d768703.js"></script>

That's it, you're done, how easy is that?
