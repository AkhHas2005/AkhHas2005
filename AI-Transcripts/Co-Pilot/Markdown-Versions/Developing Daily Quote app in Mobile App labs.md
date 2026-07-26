# Developing Daily Quote app in Mobile App labs  

## Me
I'm a university student studying app development in Android Studio using Java. The Android studio version is `Ladybug 2024.2.1`. How can I start creating a **daily quote app** that use the `Zen api` to retrieve quotes and displays a different quote each day  

## Co-Pilot
That's a great project idea, Hasan! A **daily quote app** using the **ZenQuotes API** is a perfect way to practice working with APIs, UI design, and scheduling tasks in Android. Here's a step-by-step guide to help you get started:  

### 🛠️ Step 1: Set Up Your Android Studio Project  

1. **Create a new project** in Android Studio.
2. Choose **"Empty Activity"**.
3. Set the language to **Java**.
4. Name your app (e.g., `DailyQuoteApp`).  

### 🌐 Step 2: Add Internet Permission  

In your `AndroidManifest.xml`, add:  

```xml
<uses-permission android:name="android.permission.INTERNET" />
```  

### 🔌 Step 3: Use ZenQuotes API  

ZenQuotes provides a **free API** for quotes. The endpoint for a random quote is:  

    https://zenquotes.io/api/today  

This returns a **JSON array** with one quote for the day.  

### 📦 Step 4: Add Dependencies  

To make HTTP requests, use **Volley** or **OkHttp**. Here's how to add Volley:  

In `build.gradle` (`Module: app`):  

```gradle
dependencies {
    implementation 'com.android.volley:volley:1.2.1'
}
```

### 🧠 Step 5: Create a Quote Model

```Java
public class Quote {
    private String q; // Quote text
    private String a; // Author

    public String getQuote() { return q; }
    public String getAuthor() { return a; }
}
```

### 🌄 Step 6: Fetch and Display the Quote  

In your `MainActivity.java`:  

```Java
RequestQueue queue = Volley.newRequestQueue(this);
String url = "https://zenquotes.io/api/today";

JsonArrayRequest request = new JsonArrayRequest(Request.Method.GET, url, null,
    response -> {
        try {
            JSONObject quoteObj = response.getJSONObject(0);
            String quote = quoteObj.getString("q");
            String author = quoteObj.getString("a");

            TextView quoteText = findViewById(R.id.quoteText);
            TextView authorText = findViewById(R.id.authorText);

            quoteText.setText("\"" + quote + "\"");
            authorText.setText("- " + author);
        } catch (JSONException e) {
            e.printStackTrace();
        }
    },
    error -> Log.e("API_ERROR", "Failed to fetch quote", error)
);

queue.add(request);
```

### 🕒 Step 7: Show a New Quote Daily  

You can use **SharedPreferences** to store the last fetch date and only call the API if the date has changed.  

### 🖼️ Step 8: Design the UI

Use a simple layout like:  

```xml
<LinearLayout ... >
    <TextView android:id="@+id/quoteText" ... />
    <TextView android:id="@+id/authorText" ... />
</LinearLayout>
```  

Would you like help with:  

- The full **Java code** for `MainActivity`?
- Setting up `SharedPreferences` for daily refresh?
- Adding a splash screen or animations?

Let me know how you'd like to expand the app!  

## Me
If I select "empty Activity" when I create the app, it defaults to using Kotlin and not java, how can I do it if I create the appp using "no activity"  

## Co-Pilot
Great question, Hasan! If you want to use **Java** and you're selecting **"No Activity"** when creating your project in Android Studio, you can still set everything up manually. Here's how to do it step by step:  

### ✅ Step 1: Create a New Project with "No Activity"  

1. Open Android Studio.
2. Select **"New Project" > "No Activity"**.
3. Choose **Java** as the language (you may need to click "More Settings" to change it).
4. Finish creating the project.  

### 🧱 Step 2: Manually Add an Activity

Since "No Activity" gives you a blank slate, you need to create your own `MainActivity`.  

#### 1. Create a Java class:  

- Right-click app > `java > your.package.name`
- Select **New > Java Class**
- Name it `MainActivity`  

Paste this code:  

```Java
package your.package.name;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
```  

Replace `your.package.name` with your actual package name.  

### 🧩 Step 3: Create the Layout File  

1. Go to `res > layout`
2. Right-click > **New > Layout Resource File**
3. Name it `activity_main.xml`  

Add a simple layout like:  

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp">

    <TextView
        android:id="@+id/quoteText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Quote will appear here"
        android:textSize="18sp"
        android:textAlignment="center" />

    <TextView
        android:id="@+id/authorText"
        android:layout_width="wrap_content"
        android:layout_height="        android:text="- Author"
        android:textSize="16sp"
        android:layout_marginTop="8dp"
        android:textAlignment="center" />
</LinearLayout>
```

### ⚙️ Step 4: Register the Activity in `AndroidManifest.xml`  

```xml
<application
    ... >
    <activity android:name=".MainActivity">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />
            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
</application>
```  

Now you have a working Java-based app with a custom activity and layout!  

Would you like me to help you:  

- Add the quote-fetching logic next?
- Set up the project structure for MVVM or keep it simple?
- Add a button to refresh the quote manually?  

Let me know how you'd like to proceed!  

## Me
what about integrating the zen quotes API?  

## Co-Pilot
To integrate the **ZenQuotes API** into your Java-based Android app, you'll need to make a network request to their endpoint and display the result in your UI. Here's a complete guide to help you do that:  

### 🔗 ZenQuotes API Endpoint  

For the **quote of the day**, use:  

    https://zenquotes.io/api/today    

This returns a **JSON array** with one object like:  

```json
[
  {
    "q": "Your time is limited, so don’t waste it living someone else’s life.",
    "a": "Steve Jobs"
  }
]
```

### 🧰 Step-by-Step Integration Using Java and Volley  

#### 1. Add Internet Permission  

In `AndroidManifest.xml`:  

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

#### 2. Add Volley Dependency  

In `build.gradle` (`Module: app`):  

```gradle
dependencies {
    implementation 'com.android.volley:volley:1.2.1'
}
```  

Sync your project after adding this.  

#### 3. Update Your Layout   

In `activity_main.xml`, add:  

```xml
<TextView
    android:id="@+id/quoteText"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Loading quote..."
    android:textSize="18sp"
    android:padding="16dp" />

<TextView
    android:id="@+id/authorText"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text=""
    android:textSize="16sp"
    android:padding="8dp" />
```

#### 4. Fetch and Display the Quote in Java  

In `MainActivity.java`:  

```Java
package your.package.name;

import android.os.Bundle;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
import com.android.volley.Request;
import com.android.volley.RequestQueue;
import com.android.volley.toolbox.JsonArrayRequest;
import com.android.volley.toolbox.Volley;
import org.json.JSONArray;
import org.json.JSONObject;

public class MainActivity extends AppCompatActivity {

    TextView quoteText, authorText;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        quoteText = findViewById(R.id.quoteText);
        authorText = findViewById(R.id.authorText);

        fetchQuoteOfTheDay();
    }

    private void fetchQuoteOfTheDay() {
        String url = "https://zenquotes.io/api/today";
        RequestQueue queue = Volley.newRequestQueue(this);

        JsonArrayRequest request = new JsonArrayRequest(Request.Method.GET, url, null,
            response -> {
                try {
                    JSONObject quoteObj = response.getJSONObject(0);
                    String quote = quoteObj.getString("q");
                    String author = quoteObj.getString("a");

                    quoteText.setText("\"" + quote + "\"");
                    authorText.setText("- " + author);
                } catch (Exception e) {
                    quoteText.setText("Error parsing quote.");
                    authorText.setText("");
                }
            },
            error -> {
                quoteText.setText("Failed to load quote.");
                authorText.setText("");
            });

        queue.add(request);
    }
}
```  

### 🕒 Optional: Show a New Quote Only Once Per Day  

You can use `SharedPreferences` to store the last fetch date and only call the API if the date has changed. I can help you add that logic if you'd like!  

Would you like me to:  

- Add the SharedPreferences logic for daily refresh?
- Help you add a refresh button or animation?
- Package this into a reusable class or MVVM structure?

Let me know how you'd like to expand it!  

## Me
This is my `androidManifest`, how can I update it to include the new main activity:  

```xml
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
        android:theme="@style/Theme.DailyQuoteApp"
        tools:targetApi="31" />

</manifest>
```  

## Co-Pilot
Thanks for sharing your `AndroidManifest.xml`, Hasan! Since you selected **"No Activity"** when creating your project, your manifest doesn't yet include a `MainActivity`. Here's how to update it properly:  

### ✅ Updated `AndroidManifest.xml` with `MainActivity`  

Make sure your manifest looks like this:  

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="your.package.name">

    <uses-permission android:name="android.permission.INTERNET" />

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.DailyQuoteApp"
        tools:targetApi="31">

        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>

</manifest>
```  

🔁 Replace `your.package.name` with your actual package name (e.g., `com.example.dailyquoteapp`).  

### 🧪 What This Does:  

- Adds **internet permission** for API access.
- Registers `MainActivity` as the **launcher activity** (the one that opens when the app starts).  

Would you like help verifying your package name or checking if your `MainActivity.java` is set up correctly? I can also help you test the API call or add a refresh button next!  

## Me
This is my project structure, however it says that "mainActivity" isn't a class that can be found in the manifest  

[![download-(1).jpg](https://i.postimg.cc/15NQCWC4/download-(1).jpg)](https://postimg.cc/fJZpkvhh)  

## Co-Pilot
To resolve the issue, update your `AndroidManifest.xml` to include the correct package and activity reference:  

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="uk.ac.bradford.has.akh.dailyquoteapp">

    <uses-permission android:name="android.permission.INTERNET" />

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.DailyQuoteApp"
        tools:targetApi="31">

        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>

</manifest>
```  

This ensures the manifest matches your actual package structure and correctly registers `MainActivity`.  

## Me
This is my `build.gradle.kts`, how should I update it to include the new dependencies required for the zen quotes api?  

```gradle
plugins {
    alias(libs.plugins.android.application)
}

android {
    namespace = "uk.ac.bradford.has_akh.dailyquoteapp"
    compileSdk = 34

    defaultConfig {
        applicationId = "uk.ac.bradford.has_akh.dailyquoteapp"
        minSdk = 24
        targetSdk = 34
        versionCode = 1
        versionName = "1.0"

        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            isMinifyEnabled = false
            proguardFiles(
                getDefaultProguardFile("proguard-android-optimize.txt"),
                "proguard-rules.pro"
            )
        }
    }
    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_1_8
        targetCompatibility = JavaVersion.VERSION_1_8
    }
}

dependencies {

    implementation(libs.appcompat)
    implementation(libs.material)
    testImplementation(libs.junit)
    androidTestImplementation(libs.ext.junit)
    androidTestImplementation(libs.espresso.core)
}  
```  

## Copilot
Thanks for sharing your `build.gradle.kts` file! To integrate the **ZenQuotes API** using **Volley** in a Kotlin DSL (`.kts`) Gradle file, you need to add the Volley library to your dependencies.  

### ✅ Step-by-Step Update for `build.gradle.kts`  

Add this line inside the dependencies block:  

```gradle
implementation("com.android.volley:volley:1.2.1")
```  

So your updated `dependencies` block will look like this:  

```kotlin
dependencies {
    implementation(libs.appcompat)
    implementation(libs.material)

    // ✅ Add this for ZenQuotes API integration using Volley
    implementation("com.android.volley:volley:1.2.1")

    testImplementation(libs.junit)
    androidTestImplementation(libs.ext.junit)
    androidTestImplementation(libs.espresso.core)
}
```

### 🔄 After Updating  

1. Click **"Sync Now"** when prompted by Android Studio.
2. Once synced, you can start using Volley in your Java code to make network requests to **ZenQuotes**.  

Would you like help adding a refresh button or storing the quote locally so it only updates once per day?  

## Me
Ok so now I have the strings that are storing the quote and author in my `strings.xml`:  

```xml
<resources>
    <string name="app_name">DailyQuoteApp</string>
    <string name="author">- Author</string>
    <string name="quote">Quote will appear here</string>
</resources>
```  

And at the moment this is my java code:  

```java
package uk.ac.bradford.has_akh.dailyquoteapp;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
```  

How can I update the **java code** so that the quote can be fetched from the api and displayed?  

## Copilot
Perfect! Now that you have your `strings.xml` set up and your `MainActivity.java` created, let's update your Java code to:  

1. **Fetch the quote from the ZenQuotes API** using Volley.
2. **Display the quote and author** in the `TextViews` using the strings from `strings.xml`.  

### ✅ Step-by-Step Update to `MainActivity.java`  

Here’s the full code you can use:  

```Java
package uk.ac.bradford.has_akh.dailyquoteapp;

import android.os.Bundle;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

import com.android.volley.Request;
import com.android.volley.RequestQueue;
import com.android.volley.toolbox.JsonArrayRequest;
import com.android.volley.toolbox.Volley;

import org.json.JSONArray;
import org.json.JSONObject;

public class MainActivity extends AppCompatActivity {

    private TextView quoteText;
    private TextView authorText;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Link TextViews to layout
        quoteText = findViewById(R.id.quoteText);
        authorText = findViewById(R.id.authorText);

        // Set default text from strings.xml
        quoteText.setText(getString(R.string.quote));
        authorText.setText(getString(R.string.author));

        // Fetch quote from ZenQuotes API
        fetchQuoteOfTheDay();
    }

    private void fetchQuoteOfTheDay() {
        String url = "https://zenquotes.io/api/today";
        RequestQueue queue = Volley.newRequestQueue(this);

        JsonArrayRequest request = new JsonArrayRequest(Request.Method.GET, url, null,
            response -> {
                try {
                    JSONObject quoteObj = response.getJSONObject(0);
                    String quote = quoteObj.getString("q");
                    String author = quoteObj.getString("a");

                    quoteText.setText("\"" + quote + "\"");
                    authorText.setText("- " + author);
                } catch (Exception e) {
                    quoteText.setText("Error parsing quote.");
                    authorText.setText("");
                }
            },
            error -> {
                quoteText.setText("Failed to load quote.");
                authorText.setText("");
            });

        queue.add(request);
    }
}
```  

### 🧪 Make Sure Your Layout Has These IDs

In `activity_main.xml`, make sure you have:  

```xml
<TextView
    android:id="@+id/quoteText"
    ... />

<TextView
    android:id="@+id/authorText"
    ... />
```  

Would you like to:  

- Add a refresh button to get a new quote manually?
- Store the quote locally so it only updates once per day?
- Add a loading animation while the quote is being fetched?  

Let me know how you'd like to enhance it!  

## Me
How can I add a refresh button that retrieves a new quote and also a "Show daily Quote" button that makes the daily quote reappear. Just guide me for this, don't give me the code - I want to try it myself  

## Copilot
That's a great approach, Hasan — building it yourself will help you learn much more deeply! Here's a **guided breakdown** of how to implement both buttons:  

### 🔁 1. Refresh Button – Get a New Quote  

**Goal**: When the user taps this button, it should fetch a new quote from the ZenQuotes API.  

#### Steps:  

- Add a **Button** to your `activity_main.xml` layout (e.g., `id="refreshButton"`).
- In `MainActivity.java`, use `findViewById()` to reference the button.
- Set an `OnClickListener` on the button.
- Inside the listener, call your `fetchQuoteOfTheDay()` method again.  

> 💡 Tip: You can also show a loading message or spinner while the quote is being fetched.

### 📅 2. Show Daily Quote Button – Re-display the Stored Daily Quote  

**Goal**: When tapped, this button should show the quote that was fetched earlier in the day (not a new one).  

#### Steps:  

- Use **SharedPreferences** to store the quote and author when it's first fetched.
- Add another **Button** to your layout (e.g., `id="dailyQuoteButton"`).
- In `MainActivity.java`, reference this button and set an `OnClickListener`.
- Inside the listener, retrieve the stored quote and author from **SharedPreferences**.
- Set the text of your `TextViews` to the stored values.  

> 💡 Tip: You can store the date along with the quote to ensure it's only updated once per day.

Would you like a checklist or diagram to help you track your progress as you build it? Let me know how it's going — I’d love to see what you come up with!  

## Me
How can I find the daily quote online so that I can check if my app is working properly?  

## Copilot
To check if your app is working properly and compare the quote it displays with the actual **daily quote from ZenQuotes**, you can visit their official API page directly:  

👉 [ZenQuotes.io – Daily Inspirational Quotes](https://zenquotes.io/)  

Once you're there:  

- Scroll to the **"Quote of the Day"** section.
- You’ll see the current daily quote (it updates at **00:00 UTC**).
- Compare this with what your app is showing.  

You can also test the API manually by visiting this endpoint in your browser:

    https://zenquotes.io/api/today  

It will return a JSON response like:  

```json
[
  {
    "q": "There is no greatness where there is not simplicity, goodness, and truth.",
    "a": "Leo Tolstoy"
  }
]
```  

Let me know if you'd like help parsing this manually or testing it with a tool like Postman or curl!  

## Me
Can you give me an example of a OnClickListener for a button and how I can integrate it into my onCreate method  

## Copilot
Absolutely, Hasan! Here's a **guided explanation** of how to create and integrate an `OnClickListener` for a button inside your `onCreate()` method:  

### 🧩 Step-by-Step Guide to Using `OnClickListener`  

#### 1. Add a Button to Your Layout  

In your `activity_main.xml`, define a button like:  

```xml
<Button
    android:id="@+id/refreshButton"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Refresh Quote" />
```  

You can also add another button for "Show Daily Quote" with a different ID.  

#### 2. Reference the Button in Java  

Inside your `onCreate()` method in `MainActivity.java`, use:  

```Java
Button refreshButton = findViewById(R.id.refreshButton);
```  

#### 3. Set an `OnClickListener`  

Use this pattern:  

```Java
refreshButton.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        // Your code to refresh the quote goes here
    }
});
```  

You can also use a lambda if you're comfortable with Java 8:  

```Java
refreshButton.setOnClickListener(v -> {
    // Your code here
});
```  

#### 4. Inside the Listener  

Call your method that fetches the quote (e.g., `fetchQuoteOfTheDay()`), or retrieve the stored quote from **SharedPreferences** for the "Show Daily Quote" button.  

### 🧠 Tips  

- Make sure your **button IDs** in XML match what you're referencing in Java.
- You can reuse the same method (`fetchQuoteOfTheDay()`) for both buttons if needed, or create a separate method for showing the stored quote.  

Let me know if you'd like help debugging your listener or testing the button behavior!  

*End of this Conversation*
