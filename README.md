# Ex.No:2b To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:
1. **Start the project:** Create a new Android project with two Empty Activities (`MainActivity` and `MainActivity2`).

2. **Design the First Screen:** In `activity_main.xml`, add an `EditText` to receive the number input and a `Button` to trigger the calculation.

3. **Design the Second Screen:** In `activity_main2.xml`, add a `TextView` to display the calculated factorial result.

4. **Get Input (MainActivity):** Inside `MainActivity.java`, set an `OnClickListener` on the button to retrieve the entered number from the `EditText`.

5. **Pass Data using Explicit Intent:** Create an `Intent` targeting `MainActivity2.class`. Attach the entered number to the intent using `intent.putExtra()`, and start the activity using `startActivity(intent)`.

6. **Receive Data (MainActivity2):** In `MainActivity2.java`, use `getIntent().getStringExtra()` (or `getIntExtra()`) to retrieve the passed number.

7. **Calculate Factorial:** Write a loop or recursive function to compute the factorial of the received number.

8. **Display Result:** Update the `TextView` in the second activity to show the computed factorial value.

9. **Stop:** Run and test the application.


## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: Ashwin Akash M
Registeration Number : 212223230024
*/
```
### activity_main.xml
```java
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Explicit Intent Main Activity"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.3" />

    <Button
        android:id="@+id/btnGo"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Go to Second Activity"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView"
        android:layout_marginTop="32dp" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
### activity_second.xml
```java
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".SecondActivity">

    <!-- Title -->
    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Explicit Intent Second Activity"
        android:textSize="20sp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="100dp"/>

    <!-- Button -->
    <Button
        android:id="@+id/btnGoBack"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="GO TO HOME ACTIVITY"
        app:layout_constraintTop_toBottomOf="@id/textView2"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="50dp"/>
</androidx.constraintlayout.widget.ConstraintLayout>
```
### MainActivity.java
```java
package com.example.explicitintent;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        // Button click → Open SecondActivity
        Button btnGo = findViewById(R.id.btnGo);
        btnGo.setOnClickListener(v -> {
            Intent intent = new Intent(MainActivity.this, SecondActivity.class);
            startActivity(intent);
        });
    }
}
```
### SecondActivity.java
```java
package com.example.explicitintent;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_second);

        // Button click → Go back to MainActivity
        Button btnGoBack = findViewById(R.id.btnGoBack);
        btnGoBack.setOnClickListener(v -> {
            Intent intent = new Intent(SecondActivity.this, MainActivity.class);
            startActivity(intent);
        });
    }
}

```
### AndroidManifest.xml
```java
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.ExplicitIntent">

        <!-- Main Activity (Launcher) -->
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <!-- Second Activity (for explicit intent) -->
        <activity
            android:name=".SecondActivity"
            android:exported="false" />
    </application>

</manifest>
```
## OUTPUT
<img width="1919" height="1073" alt="image" src="https://github.com/user-attachments/assets/1256f01e-6445-4939-9fa2-33e685961be6" />
<img width="1918" height="1075" alt="image" src="https://github.com/user-attachments/assets/3b0ed855-51c4-41a4-aed8-63ef17cdc49d" />




## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


