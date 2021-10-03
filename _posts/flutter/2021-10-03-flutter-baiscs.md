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
>
> see the whole code in blog page.

There are two types of widgets - `Row` and `Column`. We will be mostly using column because of landscape orientation.


Types of body widgets:

- Column
- Row

Types of axes: Axes are lines along screen. These are keys to `Column` or `Row` widget.

- `mainAxisAlignment`: vertical line from top to bottom.
- `mainAxisAlignment`: horizontal line from left to right.

> We do the following inside `body` to get a successful view:
> 
> - Define body widget (`Row`, `Column` etc.) 
> - Axis alignements
> - `child` or `children`

```dart
body: Column(
    mainAxisAlignment: MainAxisAlignment.start,
    crossAxisAlignment: CrossAxisAlignment.stretch,
    children: [
    Container(
        decoration: BoxDecoration(
        color: Colors.red,
        ),
        child: Text('hi'),
    ),
        Container(
        decoration: BoxDecoration(
        color: Colors.green,
        ),
        child: Text('hi'),
    ),
        Container(
        decoration: BoxDecoration(
        color: Colors.blue,
        ),
        child: Text('hi'),
    ),
    ],
));
```