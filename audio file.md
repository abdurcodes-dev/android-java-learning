# Simple Audio Player App

## Overview
A simple Android application built with Java that plays multiple local audio files using the Android MediaPlayer. The app allows users to play, pause, and switch between different songs with a clean Material Design 3 interface. This project was created as part of my Android development learning journey.

## What I Learned

- Using the Android MediaPlayer API
- Playing audio files from the res/raw folder
- Implementing play and pause functionality
- Switching between multiple audio tracks
- Managing MediaPlayer lifecycle correctly
- Releasing media resources to prevent memory leaks
- Handling audio completion events
- Using ImageView click listeners
- Creating reusable methods to reduce duplicate code
- Building a simple Material Design 3 user interface


## XML

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android" xmlns:app="http://schemas.android.com/apk/res-auto" xmlns:tools="http://schemas.android.com/tools" android:id="@+id/main" android:layout_width="match_parent" android:layout_height="match_parent" android:background="@color/white" android:orientation="vertical" tools:context=".MainActivity">
<LinearLayout android:layout_width="match_parent" android:layout_height="match_parent" android:padding="16dp" android:orientation="vertical">
<!--  Title  -->
<TextView android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Audio Player" android:textSize="22sp" android:textStyle="bold" android:textColor="#212121" android:layout_marginBottom="16dp"/>
<com.google.android.material.card.MaterialCardView android:layout_width="match_parent" android:layout_height="wrap_content" app:cardCornerRadius="16dp" app:cardElevation="2dp" android:layout_marginTop="10dp" app:cardBackgroundColor="@android:color/white">
<LinearLayout android:layout_width="match_parent" android:layout_height="wrap_content" android:padding="14dp" android:gravity="center_vertical" android:orientation="horizontal">
<!--  Music Icon  -->
<ImageView android:id="@+id/imgMusic" android:layout_width="56dp" android:layout_height="56dp" android:src="@drawable/checkmark" android:background="@drawable/bg_circle_green" android:padding="14dp"/>
<!--  Song Info  -->
<LinearLayout android:layout_width="0dp" android:layout_height="wrap_content" android:layout_weight="1" android:layout_marginStart="12dp" android:orientation="vertical">
<TextView android:id="@+id/txtTitle" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Song Number-One" android:textStyle="bold" android:textSize="16sp" android:textColor="#222222"/>
<TextView android:id="@+id/txtArtist" android:layout_width="wrap_content" android:layout_height="wrap_content" android:layout_marginTop="3dp" android:text="Singer Abc • 00:35" android:textSize="13sp" android:textColor="#777777"/>
<ProgressBar android:id="@+id/progress" style="?android:attr/progressBarStyleHorizontal" android:layout_width="match_parent" android:layout_height="4dp" android:layout_marginTop="10dp" android:max="100" android:progress="30" android:progressTint="#2E7D32"/>
</LinearLayout>
<!--  More  -->
<ImageView android:id="@+id/imgPlay" android:layout_width="40dp" android:layout_height="40dp" android:background="?attr/selectableItemBackgroundBorderless" android:src="@drawable/ic_play" android:tag="NOT_PLAYING"/>
</LinearLayout>
</com.google.android.material.card.MaterialCardView>
<com.google.android.material.card.MaterialCardView android:layout_width="match_parent" android:layout_height="wrap_content" app:cardCornerRadius="16dp" app:cardElevation="2dp" android:layout_marginTop="10dp" app:cardBackgroundColor="@android:color/white">
<LinearLayout android:layout_width="match_parent" android:layout_height="wrap_content" android:padding="14dp" android:gravity="center_vertical" android:orientation="horizontal">
<!--  Music Icon  -->
<ImageView android:layout_width="56dp" android:layout_height="56dp" android:src="@drawable/checkmark" android:background="@drawable/bg_circle_green" android:padding="14dp"/>
<!--  Song Info  -->
<LinearLayout android:layout_width="0dp" android:layout_height="wrap_content" android:layout_weight="1" android:layout_marginStart="12dp" android:orientation="vertical">
<TextView android:id="@+id/txtTitle2" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Song Number-Two" android:textStyle="bold" android:textSize="16sp" android:textColor="#222222"/>
<TextView android:id="@+id/txtArtist2" android:layout_width="wrap_content" android:layout_height="wrap_content" android:layout_marginTop="3dp" android:text="Singer Abc • 00:35" android:textSize="13sp" android:textColor="#777777"/>
<ProgressBar android:id="@+id/progress2" style="?android:attr/progressBarStyleHorizontal" android:layout_width="match_parent" android:layout_height="4dp" android:layout_marginTop="10dp" android:max="100" android:progress="70" android:progressTint="#2E7D32"/>
</LinearLayout>
<!--  More  -->
<ImageView android:id="@+id/imgPlay2" android:layout_width="40dp" android:layout_height="40dp" android:background="?attr/selectableItemBackgroundBorderless" android:src="@drawable/ic_play" android:tag="NOT_PLAYING"/>
</LinearLayout>
</com.google.android.material.card.MaterialCardView>
<com.google.android.material.card.MaterialCardView android:layout_width="match_parent" android:layout_height="wrap_content" app:cardCornerRadius="16dp" app:cardElevation="2dp" android:layout_marginTop="10dp" app:cardBackgroundColor="@android:color/white">
<LinearLayout android:layout_width="match_parent" android:layout_height="wrap_content" android:padding="14dp" android:gravity="center_vertical" android:orientation="horizontal">
<!--  Music Icon  -->
<ImageView android:layout_width="56dp" android:layout_height="56dp" android:src="@drawable/checkmark" android:background="@drawable/bg_circle_green" android:padding="14dp"/>
<!--  Song Info  -->
<LinearLayout android:layout_width="0dp" android:layout_height="wrap_content" android:layout_weight="1" android:layout_marginStart="12dp" android:orientation="vertical">
<TextView android:id="@+id/txtTitle3" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Song Number-Three" android:textStyle="bold" android:textSize="16sp" android:textColor="#222222"/>
<TextView android:id="@+id/txtArtist3" android:layout_width="wrap_content" android:layout_height="wrap_content" android:layout_marginTop="3dp" android:text="Singer Abc • 00:35" android:textSize="13sp" android:textColor="#777777"/>
<ProgressBar android:id="@+id/progress3" style="?android:attr/progressBarStyleHorizontal" android:layout_width="match_parent" android:layout_height="4dp" android:layout_marginTop="10dp" android:max="100" android:progress="40" android:progressTint="#2E7D32"/>
</LinearLayout>
<!--  More  -->
<ImageView android:id="@+id/imgPlay3" android:layout_width="40dp" android:layout_height="40dp" android:background="?attr/selectableItemBackgroundBorderless" android:src="@drawable/ic_play" android:tag="NOT_PLAYING"/>
</LinearLayout>
</com.google.android.material.card.MaterialCardView>
<com.google.android.material.card.MaterialCardView android:layout_width="match_parent" android:layout_height="wrap_content" app:cardCornerRadius="16dp" app:cardElevation="2dp" android:layout_marginTop="10dp" app:cardBackgroundColor="@android:color/white">
<LinearLayout android:layout_width="match_parent" android:layout_height="wrap_content" android:padding="14dp" android:gravity="center_vertical" android:orientation="horizontal">
<!--  Music Icon  -->
<ImageView android:layout_width="56dp" android:layout_height="56dp" android:src="@drawable/checkmark" android:background="@drawable/bg_circle_green" android:padding="14dp"/>
<!--  Song Info  -->
<LinearLayout android:layout_width="0dp" android:layout_height="wrap_content" android:layout_weight="1" android:layout_marginStart="12dp" android:orientation="vertical">
<TextView android:id="@+id/txtTitle4" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Song Number-Four" android:textStyle="bold" android:textSize="16sp" android:textColor="#222222"/>
<TextView android:id="@+id/txtArtist4" android:layout_width="wrap_content" android:layout_height="wrap_content" android:layout_marginTop="3dp" android:text="Singer Abc • 00:35" android:textSize="13sp" android:textColor="#777777"/>
<ProgressBar android:id="@+id/progress4" style="?android:attr/progressBarStyleHorizontal" android:layout_width="match_parent" android:layout_height="4dp" android:layout_marginTop="10dp" android:max="100" android:progress="60" android:progressTint="#2E7D32"/>
</LinearLayout>
<!--  More  -->
<ImageView android:id="@+id/imgPlay4" android:layout_width="40dp" android:layout_height="40dp" android:background="?attr/selectableItemBackgroundBorderless" android:src="@drawable/ic_play" android:tag="NOT_PLAYING"/>
</LinearLayout>
</com.google.android.material.card.MaterialCardView>
<com.google.android.material.card.MaterialCardView android:layout_width="match_parent" android:layout_height="wrap_content" app:cardCornerRadius="16dp" app:cardElevation="2dp" android:layout_marginTop="10dp" app:cardBackgroundColor="@android:color/white">
<LinearLayout android:layout_width="match_parent" android:layout_height="wrap_content" android:padding="14dp" android:gravity="center_vertical" android:orientation="horizontal">
<!--  Music Icon  -->
<ImageView android:layout_width="56dp" android:layout_height="56dp" android:src="@drawable/checkmark" android:background="@drawable/bg_circle_green" android:padding="14dp"/>
<!--  Song Info  -->
<LinearLayout android:layout_width="0dp" android:layout_height="wrap_content" android:layout_weight="1" android:layout_marginStart="12dp" android:orientation="vertical">
<TextView android:id="@+id/txtTitle5" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Song Number-Five" android:textStyle="bold" android:textSize="16sp" android:textColor="#222222"/>
<TextView android:id="@+id/txtArtist5" android:layout_width="wrap_content" android:layout_height="wrap_content" android:layout_marginTop="3dp" android:text="Singer Abc • 00:35" android:textSize="13sp" android:textColor="#777777"/>
<ProgressBar android:id="@+id/progress5" style="?android:attr/progressBarStyleHorizontal" android:layout_width="match_parent" android:layout_height="4dp" android:layout_marginTop="10dp" android:max="100" android:progress="30" android:progressTint="#2E7D32"/>
</LinearLayout>
<!--  More  -->
<ImageView android:id="@+id/imgPlay5" android:layout_width="40dp" android:layout_height="40dp" android:background="?attr/selectableItemBackgroundBorderless" android:src="@drawable/ic_play" android:tag="NOT_PLAYING"/>
</LinearLayout>
</com.google.android.material.card.MaterialCardView>
</LinearLayout>
</LinearLayout>
```

## Java

```java
package com.example.audioplayer;

import static android.view.View.GONE;
import static android.view.View.VISIBLE;

import android.Manifest;
import android.content.Context;
import android.media.MediaPlayer;
import android.net.ConnectivityManager;
import android.net.Network;
import android.net.NetworkInfo;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.ImageView;
import android.widget.ProgressBar;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.annotation.RequiresPermission;
import androidx.appcompat.app.AlertDialog;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

import java.io.IOException;

public class MainActivity extends AppCompatActivity {

    ImageView imgPlay, imgPlay2, imgPlay3, imgPlay4, imgPlay5;
    MediaPlayer mediaPlayer;
    ImageView currentPlaying;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });


        imgPlay = findViewById(R.id.imgPlay);
        imgPlay2 = findViewById(R.id.imgPlay2);
        imgPlay3 = findViewById(R.id.imgPlay3);
        imgPlay4 = findViewById(R.id.imgPlay4);
        imgPlay5 = findViewById(R.id.imgPlay5);

        /*
        imgPlay.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                imgPlay5.setImageResource(R.drawable.ic_play);

                if (imgPlay.getTag() != null && imgPlay.getTag().toString().contains("NOT_PLAYING")){

                    if (mediaPlayer != null ) mediaPlayer.release();
                    mediaPlayer = MediaPlayer.create(MainActivity.this, R.raw.wedding_nasheed);
                    mediaPlayer.start();
                    imgPlay.setImageResource(R.drawable.ic_pause);
                    imgPlay.setTag("PALYING_NOW");

                    mediaPlayer.setOnCompletionListener(new MediaPlayer.OnCompletionListener() {
                        @Override
                        public void onCompletion(MediaPlayer mediaPlayer) {
                            imgPlay.setImageResource(R.drawable.ic_play);
                            imgPlay.setTag("NOT_PLAYING");
                        }
                    });

                } else {

                    if (mediaPlayer != null) mediaPlayer.release();
                    imgPlay.setImageResource(R.drawable.ic_play);
                    imgPlay.setTag("NOT_PLAYING");
                }

            }
        });

        imgPlay2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                imgPlay.setImageResource(R.drawable.ic_play);

                if (imgPlay2.getTag() != null && imgPlay2.getTag().toString().contains("NOT_PLAYING")){

                    if (mediaPlayer != null ) mediaPlayer.release();
                    mediaPlayer = MediaPlayer.create(MainActivity.this, R.raw.the_way_of_the_tears);
                    mediaPlayer.start();
                    imgPlay2.setImageResource(R.drawable.ic_pause);
                    imgPlay2.setTag("PALYING_NOW");

                    mediaPlayer.setOnCompletionListener(new MediaPlayer.OnCompletionListener() {
                        @Override
                        public void onCompletion(MediaPlayer mediaPlayer) {
                            imgPlay2.setImageResource(R.drawable.ic_play);
                            imgPlay2.setTag("NOT_PLAYING");
                        }
                    });

                } else {

                    if (mediaPlayer != null) mediaPlayer.release();
                    imgPlay2.setImageResource(R.drawable.ic_play);
                    imgPlay2.setTag("NOT_PLAYING");
                }

            }
        });

        imgPlay3.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                imgPlay2.setImageResource(R.drawable.ic_play);

                if (imgPlay3.getTag() != null && imgPlay3.getTag().toString().contains("NOT_PLAYING")){

                    if (mediaPlayer != null ) mediaPlayer.release();
                    mediaPlayer = MediaPlayer.create(MainActivity.this, R.raw.jamalul_wujood);
                    mediaPlayer.start();
                    imgPlay3.setImageResource(R.drawable.ic_pause);
                    imgPlay3.setTag("PALYING_NOW");

                    mediaPlayer.setOnCompletionListener(new MediaPlayer.OnCompletionListener() {
                        @Override
                        public void onCompletion(MediaPlayer mediaPlayer) {
                            imgPlay3.setImageResource(R.drawable.ic_play);
                            imgPlay3.setTag("NOT_PLAYING");
                        }
                    });

                } else {

                    if (mediaPlayer != null) mediaPlayer.release();
                    imgPlay3.setImageResource(R.drawable.ic_play);
                    imgPlay3.setTag("NOT_PLAYING");
                }

            }
        });

        imgPlay4.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                imgPlay3.setImageResource(R.drawable.ic_play);

                if (imgPlay4.getTag() != null && imgPlay4.getTag().toString().contains("NOT_PLAYING")){

                    if (mediaPlayer != null ) mediaPlayer.release();
                    mediaPlayer = MediaPlayer.create(MainActivity.this, R.raw.videoplayback);
                    mediaPlayer.start();
                    imgPlay4.setImageResource(R.drawable.ic_pause);
                    imgPlay4.setTag("PALYING_NOW");

                    mediaPlayer.setOnCompletionListener(new MediaPlayer.OnCompletionListener() {
                        @Override
                        public void onCompletion(MediaPlayer mediaPlayer) {
                            imgPlay4.setImageResource(R.drawable.ic_play);
                            imgPlay4.setTag("NOT_PLAYING");
                        }
                    });

                } else {

                    if (mediaPlayer != null) mediaPlayer.release();
                    imgPlay4.setImageResource(R.drawable.ic_play);
                    imgPlay4.setTag("NOT_PLAYING");
                }

            }
        });

        imgPlay5.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                imgPlay4.setImageResource(R.drawable.ic_play);

                if (imgPlay5.getTag() != null && imgPlay5.getTag().toString().contains("NOT_PLAYING")){

                    if (mediaPlayer != null ) mediaPlayer.release();
                    mediaPlayer = MediaPlayer.create(MainActivity.this, R.raw.videoplayback_tune);
                    mediaPlayer.start();
                    imgPlay5.setImageResource(R.drawable.ic_pause);
                    imgPlay5.setTag("PALYING_NOW");

                    mediaPlayer.setOnCompletionListener(new MediaPlayer.OnCompletionListener() {
                        @Override
                        public void onCompletion(MediaPlayer mediaPlayer) {
                            imgPlay5.setImageResource(R.drawable.ic_play);
                            imgPlay5.setTag("NOT_PLAYING");
                        }
                    });

                } else {

                    if (mediaPlayer != null) mediaPlayer.release();
                    imgPlay5.setImageResource(R.drawable.ic_play);
                    imgPlay5.setTag("NOT_PLAYING");
                }

            }
        });

         */

        imgPlay.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                playSong(imgPlay, R.raw.jamalul_wujood);

            }
        });

        imgPlay2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                playSong(imgPlay2, R.raw.the_way_of_the_tears);

            }
        });

        imgPlay3.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                playSong(imgPlay3, R.raw.videoplayback);

            }
        });

        imgPlay4.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                playSong(imgPlay4, R.raw.videoplayback_tune);

            }
        });

        imgPlay5.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                playSong(imgPlay5, R.raw.wedding_nasheed);

            }
        });


    }

    //====== Song Playing Method here =========
    //=====================================================

    private void playSong(ImageView playButton, int audioFile){

        // যদি একই গান Play থাকে তাহলে Pause
        if(mediaPlayer != null && currentPlaying == playButton){

            if(mediaPlayer.isPlaying()){

                mediaPlayer.pause();
                playButton.setImageResource(R.drawable.ic_play);

            }else{

                mediaPlayer.start();
                playButton.setImageResource(R.drawable.ic_pause);

            }

            return;
        }

        // অন্য গান Play থাকলে বন্ধ করো
        if(mediaPlayer != null){

            mediaPlayer.stop();
            mediaPlayer.release();

            if(currentPlaying != null){
                currentPlaying.setImageResource(R.drawable.ic_play);
            }
        }

        mediaPlayer = MediaPlayer.create(this, audioFile);
        mediaPlayer.start();

        playButton.setImageResource(R.drawable.ic_pause);
        currentPlaying = playButton;

        mediaPlayer.setOnCompletionListener(mp -> {

            playButton.setImageResource(R.drawable.ic_play);

            mp.release();

            mediaPlayer = null;
            currentPlaying = null;

        });

    }

    //=================================================

    @Override
    protected void onDestroy() {
        super.onDestroy();

        if(mediaPlayer != null){

            mediaPlayer.release();
            mediaPlayer = null;

        }
    }
}
```

## 📁 Add Audio Files

The Orginal audio files are not include in this repository due to copyright reasons.

1. Create a folder in **`res`** named **`raw`**.
2. Copy your audio files (`.mp3` or `.wav`) into the **`raw`** folder.
3. Access them in Java using:

```java
MediaPlayer.create(this, R.raw.audio_file_name);
```

**Example:**

```text
app/
└── src/
    └── main/
        └── res/
            └── raw/
                ├── song1.mp3
                ├── song2.mp3
                ├── song3.mp3
                ├── song4.mp3
                └── song5.mp3
```

## 💡 Key Features

- Play multiple local audio files
- Play and pause audio playback
- Switch between songs seamlessly
- Automatically stop the previous song when a new one starts
- Update play/pause icons dynamically
- Release MediaPlayer resources properly
- Clean Material Design 3 user interface
- Beginner-friendly Java implementation

## 📅 Learning Date
22 July 2026
