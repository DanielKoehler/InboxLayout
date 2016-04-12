# InboxLayout
An implementation of zhaozhentao/InboxLayout that supports dynamic item population via a ListView.

This project is based on [InboxLayout](https://github.com/zhaozhentao/InboxLayout) by zhaozhentao.

<img src="https://raw.githubusercontent.com/DanielKoehler/InboxLayout/master/demo.gif" width="360" height="640" />



## Example Activity 

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    
    <FrameLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/frame">

        <com.danielkoehler.inbox.widget.InboxBackgroundScrollView
            android:overScrollMode="always"
            android:id="@+id/inboxList"
            android:layout_width="match_parent"
            android:fillViewport="true"
            android:layout_height="match_parent"
            android:background="#FFF">
        </com.danielkoehler.inbox.widget.InboxBackgroundScrollView>
        
        <com.danielkoehler.inbox.widget.InboxLayoutScrollView
            android:id="@+id/inboxlayoutContent"
            android:visibility="invisible"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:overScrollMode="always">
            <TextView android:layout_width="match_parent" android:layout_height="match_parent" android:text="@string/somestringcontent"/>
        </com.danielkoehler.inbox.widget.InboxLayoutScrollView>

    </FrameLayout>
</LinearLayout>
```
