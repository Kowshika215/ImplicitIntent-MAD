# Ex.No:3a Develop program to create a text field and a button “Navigate”. When you enter “www.gmail.com” and press navigate button it should open google page using Implicit Intents.


## AIM:

To create a navigate button using Implicit Intent to display the gmail page using Android Studio.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

1.Launch the Android application. 

2.Create an Implicit Intent object. 

3.Specify the required action (ACTION_VIEW, ACTION_DIAL, ACTION_SEND, etc.). 

4.Attach the required data using Uri.parse(). 

5.Invoke startActivity() with the Intent. 

6.Android searches for a compatible application.

7.Display the app chooser if multiple apps are available.

8.Launch the selected application.

9.Perform the requested action.


## PROGRAM:
```
/*
Program to print the text “Implicitintent”.
Developed by: Kowshika R
Registration Number : 212224220049
*/
```
## MainActivity.java

```
package com.example.imexapplication;

import android.content.ActivityNotFoundException;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        EditText editText;
        Button button;
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button button = findViewById(R.id.button);
        EditText editText = findViewById(R.id.editTextText);

        button.setOnClickListener(view -> {
            String inputUrl = editText.getText().toString().trim();
            if (inputUrl.isEmpty()) {
                editText.setError("Please enter a URL");
                return;
            }

            String targetUrl = (!inputUrl.startsWith("http://") && !inputUrl.startsWith("https://"))
                    ? "https://" + inputUrl
                    : inputUrl;

            Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(targetUrl));
            try {
                startActivity(intent);
            } catch (ActivityNotFoundException e) {
                Toast.makeText(this, "No browser found to open this link", Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

## activity_main.xml

```
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
        android:layout_width="148dp"
        android:layout_height="42dp"
        android:text="@string/enter_website"
        android:textSize="24sp"
        app:layout_constraintBottom_toTopOf="@+id/editTextText"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <EditText
        android:id="@+id/editTextText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="284dp"
        android:autofillHints="url"
        android:ems="10"
        android:hint="@string/enter_website_hint"
        android:inputType="textUri"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="144dp"
        android:text="@string/navigate"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

## OUTPUT

<img width="1917" height="1103" alt="image" src="https://github.com/user-attachments/assets/6ce771e4-9cda-4ca0-964b-e1d281c2bc95" />

<img width="1917" height="1140" alt="image" src="https://github.com/user-attachments/assets/1bb27d6e-e9e4-41bf-ac78-b6b71c3c10ce" />

<img width="1917" height="1137" alt="image" src="https://github.com/user-attachments/assets/77d2391f-e8e1-49c7-a59f-fdd7ef85aedc" />


## RESULT
Thus a Simple Android Application create a navigate button using Implicit Intent to display the gmail page using Android Studio is developed and executed successfully.


