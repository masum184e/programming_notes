# File Structure
```
app
├─ build
├─ libs
├─ src
│   ├─ main
│   │   ├─ java
│   │   │   └─ com/example/myapplication
│   │   │    
│   │   ├─ res
│   │   │   ├─ layout - store XML layout files that define the user interface of your activities and fragments.
│   │   │   │   
│   │   │   ├─ drawable - store drawable resources such as PNG files, vector graphics, and XML shapes.
│   │   │   │   
│   │   │   ├─ values - store XML files that define values like strings, colors, and dimensions. Common files include strings.xml, colors.xml, and dimens.xml.
│   │   │   │
│   │   │   ├─ mipmap - store resources for application icons, typically in different resolutions.
│   │   │   │   
│   │   │   └─ menu - store XML files that define menus for activities or fragments.
│   │   │   
│   │   │  
│   │   └─ manifests
│   │       └─ AndroidManifest.xml - It describes essential information about your app, including the package name, components (activities, services, broadcast receivers, content providers), permissions, and other application-level configurations.
│   ├─ androidTest
│   │   └─  java
│   │       └─ com/example/myapplication
│   │           └─ ExampleInstrumentedTest.java
│   └─ test
│      └─ java
│          └─ com/example/myapplication
│             
└─ build.gradle

```
# Layout

### LinearLayout
It arranges its child views in a single direction, either vertically or horizontally. This makes it a straightforward choice for creating simple layouts where views are stacked in a single column or row.

- `android:orientation` - determine the direction of the child view
    - `vertical` - stack children from top to bottom
    - `horizontal` - places children side by side from left to right
- `android:gravity` - specify how the content should be aligned to all child views within the layout
- `android:layout_gravity` - specify how the content should be aligned to individual child views.
- `android:layout_weight` - 

LinearLayout is easy to understand and implement. It provides a predictable way to arrange views in a single direction. Allows for easy alignment of child views along a single axis. But LinearLayout lead to poor performance, as the layout becomes more complex and takes longer to render.

### RelativeLayout
It allows you to position and size child views in relation to each other or to the parent container.

- `android:layout_alignParentTop`, `android:layout_alignParentBottom`, `android:layout_alignParentLeft`, `android:layout_alignParentRight` - Aligns the child view to the corresponding edge of the __parent__.
- `android:layout_centerInParent`, `android:layout_centerHorizontal`, `android:layout_centerVertical` - Centers the child view in the __parent__, either completely or along one axis.
- `android:layout_above`, `android:layout_below`, `android:layout_toLeftOf`, `android:layout_toRightOf` - Positions the child view relative to __another child view__.
- `android:layout_margin`, `android:layout_marginTop`, `android:layout_marginBottom`, `android:layout_marginLeft`, `android:layout_marginRight` - Sets the space around the child view.
- ``android:layout_alignTop`, `android:layout_alignBottom`, `android:layout_alignLeft`, `android:layout_alignRight` - Aligns the edges of __two child views__.

It allows for complex layouts where child views can be positioned relative to each other and to the parent. It helps to avoid deeply nested layouts, which can improve performance and useful for responsive designs where the position of views may change based on different screen sizes or orientations.

### TableLayout
A type of `ViewGroup` that arranges it's child in grid format.  It organizes views into rows and columns, and allows for complex layouts where alignment and spacing are important.

It consists of `TableRow` objects, each representing a row in the table.
- `android:stretchColumns`
- `android:shrinkColumns`
- `android:collapseColumns`
- `android:layout_span`
- `android:layout_column`

### FrameLayout
It is designed to block out an area on the screen to display a single item. Generally, It is used to hold a single child view, but it can also be used to overlay multiple child views, stacking them on top of each other. It display view layer by layer and one layer at a time.
- `android:foreground` 
- `android:foregroundGravity`
- `android:measureAllChildren`

# View
### TextView

- `android:text` - sets the initial text displayed by the View
- `android:layout_width` or `android:layout_height` - sets the widht and height of the view. Possible values are:
    - `match_parent` - it will set the entire height/width of parent view 
    - `wrap_content`- it will set the space as much as needed
- `android:id` - assigned identifier is used to refer the view in java/kotlin
- `android:textColor` - sets the color of the text.
- `android:textSize` - sets the font size of the text.
- `android:visibility` - control the visibility. Possible values are `visible`, `invisible`, `gone`.
- `android:backgroundTint` - specify a color overlay to the background of drawable item.

### ImageView

- `android:src` - specify the image to be displayed
- `android:scaleType` - control how an image is resized. Possible values are:
    - `fitXY` - scale the image to fit exactly within the view
    - `fitStart` - scale the image to fit within the view and align it to the top left.
    - `fitEnd` - scale the image to fit within the view and align it to the bottom right.
    - `fitCenter` - scale the image to fit within the view and center it.
- `android:adjustViewBounds` - adjust the bounds to maintain the aspect ratio. Possible values are true or false.

### EditText

- `android:inputType` - specify the type of the data. Possible values are:
    - `textCapWords` - Capitalize the first letter of each word.
    - `textCapCharacters` - Capitalize all characters.
    - `textCapSentences` - Capitalize the first letter of each sentence.
    - `textAutoCorrect` - Enable auto-correction.
    - `textMultiLine` - Allow multiple lines of text input.
- `android:hint` - set placeholder
- `android:text` - set the initial text
- `android:maxLength` - specify the maximum length of the text can be entered
- `android:imeOptions` - specify additional options for an input method editor. This will display a `Go`, `Search`, `Enter`, `Done` button on the keyboard. Possible values are `actionDone`, `actionGo`, `actionNext`, `actionSearch`, `actionSend`, `flagNoFullscreen`
- `android:textCursorDrawble` - customize the appearance of the cursor. You need to create a custom drawable resource and apply it here.
- `clearFocus()` - dismiss the soft keyboard if it's open

### Adapter
Adapter pulls the data from the source & convert into a view and then set the view into ListView/GridView/Spinner. Commonly used adapters are:
- Array Adapter - single list item
- Base Adapter - customized list item

```
ListView listView = findViewById(R.id.listView);

String[] countries = {"USA", "Canada", "UK", "Australia", "Germany","France"};

ArrayAdapter<String> adapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, countries);

listView.setAdapter(adapter);
```

Adapter takes three parameters: the context (`this`), the layout for each item (`android.R.layout.simple_list_item_1` is a `built-in layout` provided by Android for a simple list item), and the array of data.
`setAdapter()` populates the ListView with the data provided by the adapter.

### ListView
ListView is a viewgroup that can display a list of scrollable items. Each of the item is clickable
- `android:divider` -
- `android:dividerHeight` -
- `android:dividerSelector` -

List Data Container:
```
<string-array name="list_container">
    <item>Item 1</item>
    <item>Item 2</item>
    <item>Item 3</item>
    <item>Item 4</item>
    <item>Item 5</item>
</string-array>
```

Accessing the data container:
```
String[] items = getResources().getStringArray(R.array.list_container);
```

Apply Eventlistner on each item:
```
listView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
    @Override
    public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
        String selectedItem = (String) parent.getItemAtPosition(position);

        Toast.makeText(MainActivity.this, "Selected item: " + selectedItem, Toast.LENGTH_SHORT).show();

        Intent intent = new Intent(MainActivity.this, AnotherActivity.class);
        intent.putExtra("SELECTED_ITEM", selectedItem);
        startActivity(intent);
                }
        });
```

# Toast
### Custom Toast
1. __Custom Layout for Toast:__
```
<LinearLayout android:id="@+id/customToast">
    <ImageView android:id="@+id/toast_icon" />
    <TextView android:id="@+id/toast_message" />
</LinearLayout>
```
2. __Inflate the custom layout for the Toast:__
```
LayoutInflater inflater = getLayoutInflater();
View layout = inflater.inflate(R.layout.custom_toast,(ViewGroup)findViewById(R.id.custom_toast_id));
```
3. __Create and show the Toast:__
```
Toast customToast = new Toast(MainActivity.this);
customToast.setDuration(Toast.LENGTH_LONG);
customToast.setGravity(Gravity.CENTER, 0, 0);
customToast.setView(layout);
customToast.show();
```

# Java Handling
### Eventlistener
- `Button myButton = findViewById(R.id.myButton)` - finds a button with the id `myButton` defined in the layout XML file and assigns it to a variable named myButton. It should be declare outside of `onCreate` and initialize inside it.
- `myButton.setOnClickListener(new View.OnClickListener() { ... })` - sets an OnClickListener on the button called `myButton`.

### Handling Multiple Eventlistner

- __Implement the Listener Interfaces:__ implement the listener interfaces for the events you want to handle. For example, if you want to handle click events on buttons, you'll implement the View.OnClickListener interface.
```
public class MainActivity extends AppCompatActivity implements View.OnClickListener {
    ...
}
```
- __Register the Listeners:__ Register the listener instances with the appropriate views.
```
Button myButton = findViewById(R.id.myButton);
myButton.setOnClickListener(this);
```

- __Override the Listener Methods:__ Implement the required methods of the listener interfaces which will contain the logic that you want to execute when the corresponding events occur.
```
@Override
public void onClick(View view) {
    ...
}
```
__Boilerplate:__
```
public class MainActivity extends AppCompatActivity implements View.OnClickListener {

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    Button myButton = findViewById(R.id.myButton);
    myButton.setOnClickListener(this);
  }

  @Override
  public void onClick(View view) {
    if(v.getId()==R.id.myButton){
      myText.setText("Button is clicked");
    }
  }
}
```

### Inner Class
- __Instantiate the Inner Class and Set the Listener:__ Instantiate an object of the inner class and set it as the listener for the view using the `setOnClickListener` method.
```
myButton.setOnClickListener(new MyButtonClickListener());
```
- __Define the Inner Class:__ Define an inner class within your activity class. It will implement the interface corresponding to the event you want to handle. In this case, we're handling click events, so the inner class implements View.OnClickListener.
```
private class MyButtonClickListener implements View.OnClickListener {
    @Override
    public void onClick(View view) {
        ...
    }
}

```

__Boilerplate:__
```
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        ...
        myButton.setOnClickListener(new MyButtonClickListener());
    }

    private class MyButtonClickListener implements View.OnClickListener {
        @Override
        public void onClick(View view) {
            if(v.getId()==R.id.myButton){
                myText.setText("Button is clicked");
            }
        }
    }
}

```

### Event Handler in XML
__XML:__
```
<Button ... android:onClick="onButtonClick" />
```
__JAVA:__
```
public void onButtonClick(View view) {
  Toast.makeText(this, "Button clicked", Toast.LENGTH_SHORT).show();
}
```

### View Methods
- `setText()`, `setTextColor()`, `setTextSize()`, `getText()`, `getTextSize()`, `getCurrentTextColor()` - methods works by following their name
- `setOnClickListener()`- sets a listener to be invoked when the TextView is clicked.
- `setTypeface()` - set the font
- `getId()` - gets the view ID

# Logging
It allow developers to track the flow of their application, debug issues, and monitor behavior during runtime. Android provides a built-in logging framework through the `android.util.Log` class, which allows developers to output log messages of varying severity levels.

### Log Levels
1. __Verbose:__ The least important level, typically used for providing detailed information during debugging.
2. __Debug:__ Used for debugging messages. These messages are useful during development but should be disabled in production builds.
3. __Info:__ Used for informational messages that highlight the progress of the application. These messages can be useful for tracking significant application events.
4. __Warning:__ Used to indicate potential issues that do not prevent the application from functioning but should be addressed.

5. __Error:__ Used to log error conditions that might cause the application to crash or behave unexpectedly.

6. __Assert:__ Used to log assertions, indicating conditions that should never occur. This level is typically used for critical errors.

### Logging Methods

`Log.v()`,`Log.d()`,`Log.i()`,`Log.w()`,`Log.e()`,`Log.wtf()` is used for verbose, debug, informational,  warning, error, assertion message respectively. Each method required a tag and log message.

# Activity
Activity is a single screen with UI
<pre>
                onCreate -> onStart -> onResume 
                         <b>OTHER ACTIVITY</b> 
                        onPause -> onStop
                            <b>REOPEN</b> 
               onRestart -> onStart -> onResume
                    <b>CLOSE APP, BACK BUTTON</b>
                onPause -> onStop -> onDestroy
</pre>
Let's see the 7 lifecycle methods of android activity.
<img src="https://static.javatpoint.com/images/androidimages/Android-Activity-Lifecycle.png">

### Navigate Activity
Intent class is used to navigate through activity. Intent class accept two parameter, first one is current activity, and another one is navigated activity.
```
Intent intent = new Intent(this, SecondActivity.class);
startActivity(intent);
```

### Pass Data Between Activity
__Send__

`intent.putExtra()` - is used to send extra data with key value pair
```
intent.putExtra("EXTRA_MESSAGE", "Hello from MainActivity!");
```
__Recieve__

`getIntent()` and `getStringExtra()` - is used to retreive data from activity
```
Intent intent = getIntent();
String message = intent.getStringExtra("EXTRA_MESSAGE");
```

### Navigation
1. Declare Activities in `AndroidManifest.xml`:
```
<application ... >
    <activity android:name=".MainActivity">...</activity>
    <activity android:name=".SecondActivity" />
</application>
```
2. Handle `MainActivity`:

__XML File:__
```
<EditText android:id="@+id/inputBox" .../>
<Button android:id="@+id/myButton" onClick="handleNext" .../>
<TextView android:id="@+id/myView" .../>
```
__Java File:__
```
public class MainActivity extends AppCompatActivity {
    ...
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        ...
        myButton=findViewById(R.id.myButton);
        inputBox=findViewById(R.id.inputBox);
        myView=findViewById(R.id.myView);

        Intent intent = getIntent();
        String message = intent.getStringExtra("ACTIVITY_MESSAGE");
        if(message!=null){
            myView.setText("From Second Activity: "+message);
        }

    }

    public void handleNext(View v){
        if(v.getId()==R.id.myButton){
            Intent intent = new Intent(this, SecondActivity.class);
            intent.putExtra("ACTIVITY_MESSAGE", inputBox.getText().toString());
            startActivity(intent);
        }
    }
}
```
3. Handle `SecondActivity`:

__XML File:__
```
<EditText android:id="@+id/inputSecondBox" .../>
<Button android:id="@+id/mySecondButton" android:onClick="handlePrev" .../>
<TextView android:id="@+id/mySecondView" .../>
```
__Java File:__
```
public class SecondActivity extends AppCompatActivity {
    ...
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        ...
        mySecondView=findViewById(R.id.mySecondView);
        inputSecondBox=findViewById(R.id.inputSecondBox);
        mySecondButton=findViewById(R.id.mySecondButton);

        Intent intent = getIntent();
        String message = intent.getStringExtra("ACTIVITY_MESSAGE");
        if(message!=null){
            mySecondView.setText("From Main Activity: "+message);
        }

    }

    public void handlePrev(View v){
        if(v.getId()==R.id.mySecondButton){
            Intent intent = new Intent(this, MainActivity.class);
            intent.putExtra("ACTIVITY_MESSAGE", inputSecondBox.getText().toString());
            startActivity(intent);
        }
    }
}
```

`onCreate`, `onStart`, `onResume`, `onPause`, `onStop`, `onRestart`, `onDestroy` all are the instances of activity class. As you use onCreate method for initial rendering.

# Database
## SharedPreferences
It is used for storing small amounts of primitive data in key-value pairs. You can use it for storing user setting, last score, location caching

__Store Data:__
```
SharedPreferences.Editor editor = sharedPreferences.edit();
editor.putString("key", "value");
editor.putInt("key", 123);
editor.apply();  // or editor.commit();
```
__Retrieve Data:__
```
SharedPreferences sharedPreferences = getSharedPreferences("MyPreferences", Context.MODE_PRIVATE);
if(sharedPreferences.contains("key")){
  String value = sharedPreferences.getString("key", "default_value");
  int number = sharedPreferences.getInt("key",123);
}
```
## Internal Storage - File
Use internal storage to store private data within the device's internal memory.

__Store Data:__
```
String filename = "myfile.txt";
String fileContents = "Hello World!";
FileOutputStream fos = openFileOutput(filename, Context.MODE_PRIVATE);
fos.write(fileContents.getBytes());
fos.close();
```
__Retrieve Data:__
```
String filename = "myfile.txt";
FileInputStream fis = openFileInput(filename);
InputStreamReader isr = new InputStreamReader(fis);
BufferedReader bufferedReader = new BufferedReader(isr);
StringBuilder sb = new StringBuilder();
String line;
while ((line = bufferedReader.readLine()) != null) {
    sb.append(line);
}
String fileContents = sb.toString();
```
