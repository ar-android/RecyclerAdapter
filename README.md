# RecyclerAdapter
Little library android to create RecyclerView Adapter with simple way and fast

# Usage
### Add it in your root build.gradle at the end of repositories:
```gradle
allprojects {
		repositories {
			maven { url "https://jitpack.io" }
		}
}
```

### In your app/build.gradle
```gradle
dependencies {
     compile 'com.github.ar-android:RecyclerAdapter:1.1'
}
```

# Implementation
To use this adapter folow this step

## Step 1 : Create your item view for recyclerview
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
             android:layout_width="match_parent"
             android:layout_height="wrap_content">
    <TextView
        android:id="@+id/item_text"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:padding="10dp"
        android:textSize="20sp"
        android:text="Null"/>

</LinearLayout>
```
## Step 2 : Create yout viewholder
This sample view holder
```java
public class ItemHolder extends RecyclerView.ViewHolder{
    private TextView text;

    public ItemHolder(View itemView) {
        super(itemView);
        text = (TextView) itemView.findViewById(R.id.item_text);
    }

    public void bind(String model) {
        text.setText(model);
    }
}
```

## Step 3 : Create and set adapter
```java

    private void setupView() {
        data = new ArrayList<>();
        for (int i = 0; i < 10; i++) {
            data.add("Recycler position " + i + 1);
        }
        rv_view = (RecyclerView) findViewById(R.id.rv_view);
        adapter = new RecyclerAdapter<String, ItemHolder>(data, String.class, R.layout.item_holder, ItemHolder.class) {
            @Override protected void bindView(ItemHolder holder, String model, int position) {
                holder.bind(model);
            }
        };
        rv_view.setLayoutManager(new LinearLayoutManager(this));
        rv_view.setAdapter(adapter);
    }
```

If you want to give clicklistener :
```java
holder.itemView.setOnClickListener(new View.OnClickListener() {
    @Override public void onClick(View v) {
    	//To do click listener here
    }
});
```


LICENCE
-----

PercentView by [Ahmad Rosid](http://ahmadrosid.com/) is licensed under a [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0).

