---
categories: [ Flutter]
#excerpt: 
tags: []
under_development: false
---
This is a high level overview of how the flutter works under the hood.

Flutter app is composed of **Widgets**(Stateless of Stateful), that are rendered on a Skia canvas, and sent to the platform. The platform shows the canvas, and sends events back as required.

<p class="text-center">
<img src="/assets/images/flutter_working.png" alt="">
</p>

### Widgets
The central idea behind Flutter is that, **In Flutter, Everything is a widget**. The entire UI is build by combining different widgets.

A widget can define:
* a structural element (like a button or menu)
* a stylistic element (like a font or color scheme)
* an aspect of layout (like padding)
* and so on…

The application is itself a widget. The application is the top-level widget which is composed of one or more children widgets, which again are composed of children widgets. This feature enables us to create a UI of any complexity.

Following is the widget hierarchy of a simple Hello World <a href="https://www.emroline.com/papers/creating-a-simple-application-with-android-studio-and-flutter">application</a>:
<p class="text-center">
<img src="/assets/images/flutter_widget_hierarchy.png" alt="">
</p>

Note some points about above hierarchy:
* MyApp is the top-level widget. Its created by user and build uing the Flutter native widget, MaterialApp.
* MaterialApp has home property to specify the UI of home page, which is also a used created widget, MyHomePage.
* MyHomePage is build using flutter native widget, Scaffold.
* Header UI is build using flutter native widget, AppBar.
* Body Ui is build using Center widget.
* The Center widget has a property called Child, which is build using Text widget.

### Gestures
Flutter widgets support user interaction using GestureDetector widget. Its an invisible widget which can capture user interactions such as tap, drag, etc of its child widget. We can incorporate interactive features into a widget by composing it with GestureDetector widget.

### Concept of State
Flutter widgets support State maintenance by using StatefulWidget. Widget needs to be derived from StatefulWidget to support state maintenance. StatefulWidget will be auto re- rendered whenever its internal state is changed. The re-rendering is optimized by finding the difference between old and new widget UI and rendering only the necessary changes.


Flutter doesn't use OEM widgets, but provides developers with its own ready-made widgets that look native to Android or iOS apps (following Material Design or Cupertino). Developers can create their own widgets as well.

Flutter also provides developers with reactive-style views. To avoid performance issues deriving from using a compiled programming language to serve as the JavaScript bridge, Flutter uses Dart. It compiles Dart ahead of time (AOT) into the native code for multiple platforms.

That way, Flutter can easily communicate with the platform without needing a JavaScript bridge that involves a context switch between the JavaScript realm and the native realm. Compiling to native code also boosts the app startup time.

So those were some points about how Flutter works under the hood.
