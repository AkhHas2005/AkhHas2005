# Ideas for small app in Mobile App labs  

## Me
I'm a decently experienced android developer in my free time, however we're now learning Android App development at university. It's the first practical labs session today that lasts 2 hours. Can you give me some ideas for a small app that I can build today?  

## Co-Pilot
That's exciting, Hasan! Since you're already a decently experienced Android developer, you can use this lab session to build something small but polished that also shows off your skills. Here are a few **quick app ideas** that you can realistically build or prototype in 2 hours:  

### 🔹 1. Daily Quote App  
- **Features**: Displays a *motivational* or *funny quote* each day.
- **Bonus**: Add a *button* to *copy the quote* or *share it* via other apps.
- **Tech**: Use a *local list* or *fetch* from a *public API* like `ZenQuotes`.  
### 🔹 2. Simple Habit Tracker  
- **Features**: Add a *habit*, mark it as *done for the day*.
- **Bonus**: Use `SharedPreferences` or `Room DB` to persist data.
- **Tech**: `RecyclerView` + basic local storage.  
### 🔹 3. Flashlight App  
- **Features**: Toggle the *device flashlight* on/off.
- **Bonus**: Add a *fun UI* or *sound effect*.
- **Tech**: Use `CameraManager` API.  
### 🔹 4. Currency Converter  
- **Features**: Convert between *currencies* using a *fixed rate or API*.
- **Bonus**: Add a *dropdown* for selecting currencies.
- **Tech**: Simple UI + optional API integration (e.g., `ExchangeRate` API).  
### 🔹 5. To-Do List (Minimalist)  
- **Features**: *Add*, *delete*, and *mark tasks* as done.
- **Bonus**: Swipe to *delete* using `ItemTouchHelper`.
- **Tech**: `RecyclerView` + `Room` or `SharedPreferences`.   
### 🔹 6. Simple Dice Roller  
- **Features**: Tap a *button* to *roll a dice* and show a *random number*.
- **Bonus**: Add *dice images* or *animations*.
- **Tech**: *Random number generation* + basic UI.  

Would you like one of these ideas fleshed out with *starter code* or *layout suggestions*? Or do you want something more advanced to challenge yourself during the lab?  

## Me
How can I make this project using the `ZenQuotes` API:  

### 🔹 1. Daily Quote App  
- **Features**: Displays a *motivational* or *funny quote* each day.
- **Bonus**: Add a *button* to *copy the quote* or *share it* via other apps.
- **Tech**: Use a *local list* or *fetch* from a *public API* like `ZenQuotes`.  

## Co-Pilot
Absolutely! Here’s a step-by-step guide to building a **Daily Quote App** using the `ZenQuotes` API, with the features you mentioned:  

### 1. Project Setup  
- Create **a new Android Studio project** (Empty Activity, Kotlin recommended).
- Name it something like `DailyQuoteApp`.  
### 2. Add Internet Permission  
In your `AndroidManifest.xml`, add:  

```Xml
<uses-permission android:name="android.permission.INTERNET"/>
```

### 3. Design the Layout  
A simple activity_main.xml might look like:  

```Xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:padding="24dp"
    android:gravity="center"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/quoteText"
        android:text="Loading..."
        android:textSize="20sp"
        android:gravity="center"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:padding="16dp"/>

    <Button
        android:id="@+id/btnCopy"
        android:text="Copy Quote"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"/>

    <Button
        android:id="@+id/btnShare"
        android:text="Share Quote"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"/>
</LinearLayout>
```

### 4. Fetch a Quote from `ZenQuotes` API  
ZenQuotes provides a free endpoint:  
> https://zenquotes.io/api/random  
You can use `OkHttp` or `Retrofit` for network calls. Here’s a simple example using `OkHttp`:  
#### Add dependency in `build.gradle`:  

```gradle
implementation 'com.squareup.okhttp3:okhttp:4.9.3'
```  

#### Kotlin code in `MainActivity.kt`:  

```Kotlin
import android.os.Bundle
import android.widget.Button
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import okhttp3.*
import org.json.JSONArray
import java.io.IOException

class MainActivity : AppCompatActivity() {
    private lateinit var quoteText: TextView
    private lateinit var btnCopy: Button
    private lateinit var btnShare: Button
    private var currentQuote: String = ""

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        quoteText = findViewById(R.id.quoteText)
        btnCopy = findViewById(R.id.btnCopy)
        btnShare = findViewById(R.id.btnShare)

        fetchQuote()

        btnCopy.setOnClickListener {
            val clipboard = getSystemService(CLIPBOARD_SERVICE) as android.content.ClipboardManager
            val clip = android.content.ClipData.newPlainText("Quote", currentQuote)
            clipboard.setPrimaryClip(clip)
            Toast.makeText(this, "Copied!", Toast.LENGTH_SHORT).show()
        }

        btnShare.setOnClickListener {
            val shareIntent = android.content.Intent().apply {
                action = android.content.Intent.ACTION_SEND
                putExtra(android.content.Intent.EXTRA_TEXT, currentQuote)
                type = "text/plain"
            }
            startActivity(android.content.Intent.createChooser(shareIntent, "Share via"))
        }
    }

    private fun fetchQuote() {
        val client = OkHttpClient()
        val request = Request.Builder()
            .url("https://zenquotes.io/api/random")
            .build()

        client.newCall(request).enqueue(object : Callback {
            override fun onFailure(call: Call, e: IOException) {
                runOnUiThread {
                    quoteText.text = "Failed to load quote."
                }
            }

            override fun onResponse(call: Call, response: Response) {
                response.body?.string()?.let { body ->
                    val jsonArray = JSONArray(body)
                    val quote = jsonArray.getJSONObject(0).getString("q")
                    val author = jsonArray.getJSONObject(0).getString("a")
                    currentQuote = "\"$quote\"\n\n- $author"
                    runOnUiThread {
                        quoteText.text = currentQuote
                    }
                }
            }
        })
    }
}
```  

### 5. Bonus: Polish & Test  
- Add *error handling* for *network issues*.
- Optionally, add a "Refresh" button to get a *new quote*.
- Test on an *emulator* or *device*.  

### Summary of Features
- **Displays a daily quote** from ZenQuotes.
- **Copy** and **Share** buttons for user interaction.  

Would you like a **starter project** or more advanced features (like saving favorite quotes or using `ViewModel/LiveData`)? Let me know how deep you want to go!  

## Me
I have a problem, so I created the app with package name `uk.ac.bradford.has_akh.dailyquoteapp`, however I want to make it in java and it automatically created a Kotlin version  

## Co-Pilot
No worries, Hasan! This is a common situation. Android Studio sometimes defaults to Kotlin, but you can absolutely create your app in Java. Here’s how you can **switch to Java** or create Java classes in your existing project:  

### Option 1: Create a New Java Activity  
1. **Right-click** on your java package folder (e.g., `uk.ac.bradford.has_akh.dailyquoteapp`).
2. Select **New > Java Class**.
3. Name it `MainActivity`.
4. Copy the code template for a Java activity (see below).  

### Option 2: Create a New Project in Java  
If you prefer a clean start:  

1. Go to **File > New > New Project**.
2. When choosing the template, select **Empty Activity**.
3. On the next screen, **change the language to Java** (there’s a dropdown for Language).
4. Use the same package name if you want.  

### Java Version of MainActivity (with ZenQuotes API)
Here’s a *Java version* of the *main logic* for your app:  

```Java
package uk.ac.bradford.has_akh.dailyquoteapp;

import android.content.ClipData;
import android.content.ClipboardManager;
import android.content.Context;
import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;
import org.json.JSONArray;
import org.json.JSONObject;
import java.io.IOException;
import okhttp3.Call;
import okhttp3.Callback;
import okhttp3.OkHttpClient;
import okhttp3.Request;
import okhttp3.Response;

public class MainActivity extends AppCompatActivity {
    private TextView quoteText;
    private Button btnCopy, btnShare;
    private String currentQuote = "";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        quoteText = findViewById(R.id.quoteText);
        btnCopy = findViewById(R.id.btnCopy);
        btnShare = findViewById(R.id.btnShare);

        fetchQuote();

        btnCopy.setOnClickListener(v -> {
            ClipboardManager clipboard = (ClipboardManager) getSystemService(Context.CLIPBOARD_SERVICE);
            ClipData clip = ClipData.newPlainText("Quote", currentQuote);
            clipboard.setPrimaryClip(clip);
            Toast.makeText(this, "Copied!", Toast.LENGTH_SHORT).show();
        });

        btnShare.setOnClickListener(v -> {
            Intent shareIntent = new Intent(Intent.ACTION_SEND);
            shareIntent.putExtra(Intent.EXTRA_TEXT, currentQuote);
            shareIntent.setType("text/plain");
            startActivity(Intent.createChooser(shareIntent, "Share via"));
        });
    }

    private void fetchQuote() {
        OkHttpClient client = new OkHttpClient();
        Request request = new Request.Builder()
                .url("https://zenquotes.io/api/random")
                .build();

        client.newCall(request).enqueue(new Callback() {
            @Override
            public void onFailure(Call call, IOException e) {
                runOnUiThread(() -> quoteText.setText("Failed to load quote."));
            }

            @Override
            public void onResponse(Call call, Response response) throws IOException {
                if (response.body() != null) {
                    try {
                        String body = response.body().string();
                        JSONArray jsonArray = new JSONArray(body);
                        JSONObject obj = jsonArray.getJSONObject(0);
                        String quote = obj.getString("q");
                        String author = obj.getString("a");
                        currentQuote = "\"" + quote + "\"\n\n- " + author;
                        runOnUiThread(() -> quoteText.setText(currentQuote));
                    } catch (Exception e) {
                        runOnUiThread(() -> quoteText.setText("Error parsing quote."));
                    }
                }
            }
        });
    }
}
```

### Summary  
- You can *mix Java and Kotlin* in the *same project*, but you can also *just use Java*.
- If you want to *remove the Kotlin files*, just *delete* them and *create new* Java files.
- The *above code* is a *direct Java translation* of the *Kotlin example*.  

**Would you like help with the Java layout file, dependencies, or anything else**?  

## Me
After deleting my kotlin file and creating a java one I get this error in my `androidManifest.xml`, how do i fix it:  

`MainActivity must extend android. app. Activity More... (Ctrl+F1)`  

## Co-Pilot
Great catch, Hasan! That error usually happens when Android Studio can't recognize your new `MainActivity` as a proper **AppCompatActivity**. Here's how to fix it:  

### ✅ Fix the Manifest Error  
Make sure your `MainActivity.java` **extends `AppCompatActivity`**, *not just* `Activity`.  

#### ✅ Correct:  

```Java
public class MainActivity extends AppCompatActivity {
    // your code
}
```  

#### ❌ Incorrect:  

```Java
public class MainActivity extends Activity {
    // will cause issues with themes and layouts
}
```

Also, ensure you have the correct import at the top:  

```Java
import androidx.appcompat.app.AppCompatActivity;
```  

### ✅ Update Your `AndroidManifest.xml`  
Make sure your manifest points to the correct class:  

```Xml
<activity android:name=".MainActivity">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```  

If your package is `uk.ac.bradford.has_akh.dailyquoteapp`, and your activity is inside that package, then `.MainActivity` is fine.  

### ✅ Sync and Rebuild  
After making these changes:  
1. **Sync Gradle** (click “Sync Now” if prompted).
2. **Clean and Rebuild** the project:
    - `Build > Clean Project`
    - `Build > Rebuild Project`  

Let me know if you’re still seeing the error or if you'd like help checking your full manifest or Java file!  

## Me
Also the format of my library imports in `build.gradle.kts` is this, how do I update it with the new imports:  

    implementation(libs.androidx.core.ktx)
    implementation(libs.androidx.lifecycle.runtime.ktx)
    implementation(libs.androidx.activity.compose)
    implementation(platform(libs.androidx.compose.bom))
    implementation(libs.androidx.ui)
    implementation(libs.androidx.ui.graphics)
    implementation(libs.androidx.ui.tooling.preview)
    implementation(libs.androidx.material3)
    testImplementation(libs.junit)
    androidTestImplementation(libs.androidx.junit)
    androidTestImplementation(libs.androidx.espresso.core)
    androidTestImplementation(platform(libs.androidx.compose.bom))
    androidTestImplementation(libs.androidx.ui.test.junit4)
    debugImplementation(libs.androidx.ui.tooling)
    debugImplementation(libs.androidx.ui.test.manifest)  

## Co-Pilot
Thanks for sharing your `build.gradle.kts` format! Since you're using the **Kotlin DSL** (.kts), *dependencies are declared* using `libs.<library>` references, which are *typically managed* via a `libs.versions.toml` file.  

To add Java-compatible libraries for your app (like `AppCompatActivity` and `OkHttp`), you’ll need to:  

### ✅ Step 1: Add Required Libraries to `libs.versions.toml`  

If you're using **version catalogs**, open `gradle/libs.versions.toml` and *add entries* like:

```Toml
[versions]
appcompat = "1.6.1"
okhttp = "4.9.3"

[libraries]
androidx-appcompat = { group = "androidx.appcompat", name = "appcompat", version.ref = "appcompat" }
okhttp = { group = "com.squareup.okhttp3", name = "okhttp", version.ref = "okhttp" }
```  

### ✅ Step 2: Add Them to `build.gradle.kts`  
Now in your `build.gradle.kts`, add:  

```Kotlin
implementation(libs.androidx.appcompat)
implementation(libs.okhttp)
```  

### ✅ Optional: If You’re Not Using Version Catalogs  
If you’re not using `libs.versions.toml`, you can *directly add the dependencies* like this:  

```Kotlin
implementation("androidx.appcompat:appcompat:1.6.1")
implementation("com.squareup.okhttp3:okhttp:4.9.3")
```  

### ✅ Bonus: Java Compatibility  
Since you're *writing in Java*, make sure your `compileSdk` and `targetSdk` are set appropriately in `build.gradle.kts`:  

```Gradle
android {
    compileSdk = 34

    defaultConfig {
        applicationId = "uk.ac.bradford.has_akh.dailyquoteapp"
        minSdk = 21
        targetSdk = 34
        // ...
    }

    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_17
        targetCompatibility = JavaVersion.VERSION_17
    }
}
```  

Would you like help checking your `libs.versions.toml` file or adding other useful Java libraries like `Retrofit`, `Gson`, or `Material Components`?  

## Me
I'm trying to write the main activity and layout files from scratch to test myself, but can you give me a bit of guidance?  

## Copilot
Absolutely, Hasan! Here’s some practical guidance to help you write your own `MainActivity.java` and `activity_main.xml` from scratch, while still letting you do the hands-on work:  

### 1. `MainActivity.java`: Key Steps
- **Extend `AppCompatActivity`**.
- **Set the content view** to your layout in `onCreate()`.
- **Find your views** using `findViewById`.
- **Set up your network call** (using `OkHttp` or similar).
- **Update the UI** with the fetched quote.
- **Set up listeners** for copy/share buttons.

#### Skeleton Example:  

```Java
public class MainActivity extends AppCompatActivity {
    // Declare your views (TextView, Buttons)
    // String for the current quote

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize your views with findViewById

        // Call a method to fetch the quote

        // Set onClickListeners for copy and share buttons
    }

    // Method to fetch quote from API (use OkHttp)
    // Method to update UI with the quote
}
```

### 2. `activity_main.xml`: Layout Guidance  
- Use a **vertical LinearLayout** or a **ConstraintLayout**.
- Add a **TextView** for the quote (make it multi-line, centered, and padded).
- Add two **Buttons**: one for "Copy", one for "Share".  

#### Skeleton Example:  

```Xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="24dp"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/quoteText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Loading..."
        android:textSize="20sp"
        android:gravity="center"
        android:padding="16dp"/>

    <Button
        android:id="@+id/btnCopy"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Copy Quote"
        android:layout_marginTop="16dp"/>

    <Button
        android:id="@+id/btnShare"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Share Quote"
        android:layout_marginTop="8dp"/>
</LinearLayout>
```  

### 3. Tips for Each Step
- Network on Main Thread?
    - Don’t do network calls on the main thread! Use `OkHttp’s enqueue()` for async calls.
- UI Updates:
    - Only update UI from the main thread. Use `runOnUiThread()` if updating from a background thread.
- Copy/Share:
    - Use `ClipboardManager` for copying, and an **Intent** for sharing.  
### 4. Debugging Checklist  
- If your app crashes, check for **null pointers** (e.g., `findViewById`).
- If the quote doesn’t show, check your **network permissions** and **API response**.
- Use `Logcat` for debugging!  

Would you like a **step-by-step breakdown** for any specific part (like the network call, or the copy/share logic)? Or do you want to try first and ask for help if you get stuck?  

*End of this Conversation*
