---
title: Fltter basics
updated: 2021-10-03 23:37
category: 
- flutter
---

> ### ✨ Credits
>
> I will be following [this YT video](https://www.youtube.com/watch?v=pTJJsmejUOQ) from freecodecamp.
> 
> Additional links:
>
> - [Author's blog post](https://fluttercrashcourse.com/blog)
> - [Installing on mac](https://www.youtube.com/watch?v=THsihXK1-14&t=0s)
> - [Installing on win](https://www.youtube.com/watch?v=EDlywQeg5Vs&t=0s)
> - [App that we will be building](https://github.com/seenickcode/tourismandco)



## 💖 Introduction (summary)

Todo: (in the end)

<div class="divider"></div>

## 1. Layout in flutter

[blog](https://fluttercrashcourse.com/blog/02-layout-basics)

Layouts control the way content is displayed dynamically.

For example, `Container` is same as `div` in html which stores content.

Usage: 
```dart
Scaffold(
    ...
    body: Container(
        // `decoration` defines how container
        // is presented to user.
        decoration: BoxDecoration( // keys: https://api.flutter.dev/flutter/painting/BoxDecoration-class.html
            color: Colors.red, // (or) Color.fromRGBO(38, 38, 38, 0.4)
        )

        // `child` is the contents
        child: Text('Content of a container.') 
    )
)
```

> **Note:** Container cannot exist all by itself. It needs to be added into `children` of `Column` or `Row`. And we have to define the axis keys like `mainAxisAlignment: MainAxisAlignment.start` and  `crossAxisAlignment: CrossAxisAlignment.strech`


There are two types of widgets - *row* and *column*. We will be mostly using column because of landscape orientation.

Types of axes: Axes are 

- Main axis
- Cross axis


- Column widget
- Row widget
- 
