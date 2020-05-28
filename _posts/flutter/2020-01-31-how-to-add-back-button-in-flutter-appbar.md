---
categories: [ Flutter]
#excerpt: 
tags: []
under_development: false
---

The sample code below shows how to add back button in AppBar in flutter.

Following is the content of **Main.dart** file:

{% highlight dart %}
{% raw %}
import 'package:flutter/material.dart';
import 'appbar_back.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      debugShowCheckedModeBanner: false,
      theme: ThemeData(
        primarySwatch: Colors.red,
      ),
      home: AppBarBack(),
    );
  }
}
{% endraw %}
{% endhighlight %}

In the above code, we have imported `appbar_back.dart` which represents the page that will show flutter back button when the application is run in android device or emulator.

Following is the content of **appbar_back**.dart file:

{% highlight dart %}
{% raw %}
import 'package:flutter/material.dart';

class AppBarBack extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        automaticallyImplyLeading: true,
        //`true` if you want Flutter to automatically add Back Button when needed,
        //or `false` if you want to force your own back button every where
        title: Text('AppBar Back Button'),
        leading: IconButton(icon:Icon(Icons.arrow_back),
          onPressed:() => Navigator.pop(context, false),
        )
      ),
      body: Center(
        child: Text("Main Screen"),
      ),
    );
  }
}
{% endraw %}
{% endhighlight %}

<p class="text-center">
<img src="/assets/images/flutter_app_back_button.jpg" alt="Flutter Logo">
</p>