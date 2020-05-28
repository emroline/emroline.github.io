---
categories: [ Android, Android Examples ]
tags: []
under_development: false
---
There are two ways to send SMS using an android app:
1. SmsManager API
2. Using Built-in SMS application

Here we will use `SmsManager API` to send message from our android application.

{% highlight kotlin %}
{% raw %}
SmsManager.getDefault().sendTextMessage("phoneNo", null, "sms message", null, null)
{% endraw %}
{% endhighlight %}

Our application will need `SEND_SMS` permission.

{% highlight xml %}
{% raw %}
<uses-permission android:name="android.permission.SEND_SMS"/>
{% endraw %}
{% endhighlight %}

Now follow the following steps to build an android application using which you can send SMS to any number.

1. Open Android Studio IDE and create new project. Name the project as `mySmsApp` under a package name `com.example.mysmsapp`
2. Select Kotlin under language option.
3. Modify `MainActivity.kt` and add the required code to handle sending sms.
4. Modify `activity_main.xml` to add the code for user interface.
5. Modify `AndroidManifest.xml` and add the permissions required.
6. Run the application and test it on some android device or emulator.


Following is the modified `AndroidManifest.xml`:

{% highlight xml %}
{% raw %}

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.mysmsapp">

    <uses-permission android:name="android.permission.SEND_SMS"/>

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>

{% endraw %}
{% endhighlight %}


Following is the modified `activity_main.xml`:

{% highlight xml %}
{% raw %}

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/inputNumber"
        android:layout_width="329dp"
        android:layout_height="wrap_content"
        android:ems="10"
        android:hint="Enter Phone no"
        android:inputType="textPersonName"
        app:layout_constraintBottom_toTopOf="@+id/inputMessage"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.529" />

    <EditText
        android:id="@+id/inputMessage"
        android:layout_width="329dp"
        android:layout_height="wrap_content"
        android:layout_marginBottom="184dp"
        android:ems="10"
        android:hint="Enter text"
        android:inputType="textPersonName"
        app:layout_constraintBottom_toTopOf="@+id/send_button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

    <Button
        android:id="@+id/send_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="256dp"
        android:text="SEND"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>

{% endraw %}
{% endhighlight %}

Following is the modified `MainActifity.kt`:

{% highlight kotlin %}
{% raw %}

package com.example.mysmsapp

import android.content.pm.PackageManager
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.telephony.SmsManager
import android.widget.EditText
import android.widget.Toast
import androidx.core.app.ActivityCompat
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {

    private val requestSendSms: Int = 2

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        send_button.setOnClickListener {
            if(ActivityCompat.checkSelfPermission(this, android.Manifest.permission.SEND_SMS) != PackageManager.PERMISSION_GRANTED){
                ActivityCompat.requestPermissions(this, arrayOf(android.Manifest.permission.SEND_SMS),requestSendSms)
            }else{
                sendSms()
            }
        }
    }

    override fun onRequestPermissionsResult(
        requestCode: Int,
        permissions: Array<out String>,
        grantResults: IntArray
    ) {
        if(requestCode == requestSendSms) sendSms()
    }

    private fun sendSms() {
        val number = findViewById<EditText>(R.id.inputNumber).getText().toString()
        val message = findViewById<EditText>(R.id.inputMessage).getText().toString()

        SmsManager.getDefault().sendTextMessage(number,null,message,null,null)

        Toast.makeText(this,"SMS sent.", Toast.LENGTH_SHORT).show()
    }
}


{% endraw %}
{% endhighlight %}

**Note:** You can download the source code of application from: <a href="https://github.com/emroline-opensource/android-application-to-send-sms-using-kotlin">Emroline OpenSource Github repo</a>