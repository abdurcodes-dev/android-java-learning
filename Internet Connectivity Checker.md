# Internet Connectivity Checker

## Overview
A simple Android application built with Java that checks internet connectivity using `if-else` conditions and displays an `AlertDialog` when no internet connection is available. It also shows a confirmation dialog before exiting the app. This project was created as part of my Android development learning journey.

## What I Learned

- Checking internet connectivity in Android
- Using `ConnectivityManager` and `NetworkInfo`
- Applying `if-else` conditions
- Displaying `AlertDialog` for user notifications
- Creating an exit confirmation dialog
- Handling network availability
- Working with Button click events
- Updating UI dynamically with `TextView

## XML

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.drawerlayout.widget.DrawerLayout xmlns:android="http://schemas.android.com/apk/res/android" xmlns:app="http://schemas.android.com/apk/res-auto" xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent" android:layout_height="match_parent" tools:context=".MainActivity">
<androidx.coordinatorlayout.widget.CoordinatorLayout android:layout_width="match_parent" android:layout_height="match_parent">
<com.google.android.material.appbar.AppBarLayout android:layout_width="match_parent" android:layout_height="wrap_content">
<com.google.android.material.appbar.MaterialToolbar android:layout_width="match_parent" android:layout_height="?attr/actionBarSize" android:background="#3F51B5" app:title="Home Work" app:titleTextColor="@color/white"/>
</com.google.android.material.appbar.AppBarLayout>
<LinearLayout android:layout_width="match_parent" android:layout_height="match_parent" android:orientation="vertical" android:gravity="center" android:padding="20dp">
<TextView android:id="@+id/resultText" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Check Internet Connection" android:textSize="20sp" android:textStyle="bold" android:textColor="#333333" android:layout_marginBottom="30dp"/>
<Button android:id="@+id/checkButton" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Check Connection" android:textAllCaps="false"/>
</LinearLayout>
</androidx.coordinatorlayout.widget.CoordinatorLayout>
</androidx.drawerlayout.widget.DrawerLayout>
```

## Java

```java
package com.example.testwork;

import android.content.Context;
import android.content.DialogInterface;
import android.net.ConnectivityManager;
import android.net.NetworkInfo;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AlertDialog;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    TextView resultText;
    Button checkButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        resultText = findViewById(R.id.resultText);
        checkButton = findViewById(R.id.checkButton);


        checkButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

               ConnectivityManager connectivityManager = (ConnectivityManager) getSystemService(Context.CONNECTIVITY_SERVICE);
               NetworkInfo networkInfo = connectivityManager.getActiveNetworkInfo();

               if (networkInfo != null && networkInfo.isConnected()){
                   resultText.setText("Internet Connected");
               } else{
                   resultText.setText("No Internet!");

                   new AlertDialog.Builder(MainActivity.this)
                           .setTitle("No Internet Connection")
                           .setMessage("Please check your internet connection.")
                           .setPositiveButton("OK", null)
                           .show();

               }


            }
        });

    }
    
    //=============================================================
    @Override
    public void onBackPressed() {
        //super.onBackPressed();

        new AlertDialog.Builder(MainActivity.this)
                .setTitle("Exit App!")
                .setMessage("Do you want to exit the app?")
                .setPositiveButton("Confirm", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int which) {
                        finish();
                    }
                })
                .setNegativeButton("Cancel", null)
                .show();
    }
    //===============================================================
    
}
```

## 💡 Key Features

- Check internet connection with a button click
- Show connection status on the screen
- Display an alert when there is no internet connection
- Show an exit confirmation dialog when the Back button is pressed
- Beginner-friendly Java implementation

## 📅 Learning Date
20 July 2026
