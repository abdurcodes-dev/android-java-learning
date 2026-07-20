# PDF Viewer Library

## Overview
A PDF Viewer library allows Android apps to display PDF files inside an Android application.

## What I Learned
- Added the Android PDF Viewer library.
- Synced the Gradle project.
- Displayed a PDF in the app.
- Loaded a PDF file from the `assets` folder.

## Dependency

```gradle
implementation 'com.github.barteksc:android-pdf-viewer:3.2.0-beta.1'
```

## XML

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <com.github.barteksc.pdfviewer.PDFView
        android:id="@+id/pdfView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>

</RelativeLayout>
```

## Java

```java
package com.example.pdfviewer;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
import com.github.barteksc.pdfviewer.PDFView;

public class MainActivity extends AppCompatActivity {

    PDFView pdfView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        pdfView = findViewById(R.id.pdfView);
        pdfView.fromAsset("home_work_214.pdf").load();
    }
}
```

## 💡 Key Points
- Integrated a third-party PDF Viewer library.
- Displayed a PDF file from the `assets` folder.
- Learned basic library integration in Android.

## 📅 Learning Date
20 July 2026
