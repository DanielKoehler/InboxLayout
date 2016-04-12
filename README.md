# InboxLayout
An implementation of zhaozhentao/InboxLayout that supports dynamic item population via a ListView.

This project is based on [InboxLayout](https://github.com/zhaozhentao/InboxLayout) by zhaozhentao.

<img src="https://raw.githubusercontent.com/DanielKoehler/InboxLayout/master/demo.gif" width="360" height="640" />

## Usage

#### Activity

```java 
    
    private MyRowItemAdapter mAdapter;
    
    ... 
    
    @Override
    protected void onCreate(Bundle savedInstanceState) {
    
        super.onCreate(savedInstanceState);

        final InboxBackgroundScrollView mListView = (InboxBackgroundScrollView)findViewById(R.id.inboxList);

        inboxLayoutScrollView = (InboxLayoutScrollView) findViewById(R.id.inboxlayoutContent);
        inboxLayoutScrollView.setBackgroundScrollView(mListView);// ListView
        inboxLayoutScrollView.setCloseDistance(50);

        // Defined Array values to show in ListView
        MyRowItem[] values = {
                new MyRowItem("some value", "another value"),
        };

        // specify an adapter (see also next example)
        mAdapter = new MyRowItemAdapter(this, values);

        mListView.setAdapter(mAdapter);

        mListView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {

                inboxLayoutScrollView.openWithAnim(view);

            }
        });
    }
    
    ...
        
```

#### Adapter


```java

class MyRowItemAdapter extends ArrayAdapter<MyRowItem>  {

    private final Context context;
    private final MyRowItem[] values;

    public MyAdapter(Context context, MyRowItem[] values) {
        super(context, -1, values);
        this.context = context;
        this.values = values;
    }
    
    @Override
    public View getView(int position, View convertView, ViewGroup parent) {

        LinearLayout rowView = (LinearLayout) LayoutInflater.from(parent.getContext()).inflate(R.layout.rowCell, parent, false);
        // set up row.
        return rowView;

    }

}

```

#### Layout 

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
