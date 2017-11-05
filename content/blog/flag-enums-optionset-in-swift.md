+++
date = "2016-10-01T16:58:44+07:00"
draft = false
title = "Bitwise Flags Enum in Swift using OptionSet"
slug = "bitwise-flag-enum-in-swift-optionset"
+++

`Bitwise Flags using Enum` is a technique that is heavily used in the Apple SDK. You can see that Apple tends to use that everywhere from `UIKit` to `Foundation`.

<script src="https://gist.github.com/khoiln/c20f3399e54c8b4ec08e43d3784c8e22.js"></script>

In Swift, enum doesn't behave that way. *Fact: Did you know enum in Swift can even have methods?*

<script src="https://gist.github.com/khoiln/c1b90b2fcce70e972d5555bac1edf930.js"></script>

Swift want all the enum value to be literal, and `1 << 0` isn't it. So we'll have to revise that in to:

<script src="https://gist.github.com/khoiln/8e5f7cf91dca5cde54ec5f7c9ea86b8f.js"></script>

That code above although is grammatically correct but isn't Swify enough. In Swift, enums are meant to use when the cases are `mutually exclusive`, that means only single option at a time. Swift has a protocol called `OptionSet` `that presents a mathematical set interface to a bit mask`. A struct conforms to the protocol will have a standard set operation: `contains`, `union` ... implemented through the magic of `protocol extension`.

So the code above in a correct Swifty way would be something like:

<script src="https://gist.github.com/khoiln/d1cb21560263e46c0486c0050071b9e2.js"></script>

By conforming to the OptionSet protocol, we also have the power to use some very useful common methods that are implemented for you by the standard library

<script src="https://gist.github.com/khoiln/221458e343ed51daeedc21038d7d2219.js"></script>

`OptionSet` isn't a `Collection` or a `Sequence`, so you won't be able to iterate through the elements in it. For the full references on `OptionSet`, check out the [Apple Docs](https://developer.apple.com/reference/swift/optionset).
