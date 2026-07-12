## Me
In Android Studio, I'm a using the Medium Phone API 35 in the emulator to run my app. I've create an SQLite database that is at path /data/data/uk.ac.bradford.has_akh.myloginandregister/databases relative to my device. However, where would this be stored in the windows file system, I want to be able to navigate to this path and open the database in DB browser  

## Copilot
Great question, Hasan! When you're running an Android emulator in Android Studio and your app creates an SQLite database, it's stored in the emulated device's internal storage, which is not directly accessible from the Windows file system like a regular folder.

However, you can access it using Android Studio's Device File Explorer. Here's how to locate and export your database so you can open it in DB Browser for SQLite:

🔍 Steps to Access and Export Your SQLite Database:

Open Device File Explorer:

In Android Studio, go to View > Tool Windows > Device File Explorer.
Make sure your emulator is running and selected.

Navigate to Your App's Database Folder:

Go to:
/data/data/uk.ac.bradford.has_akh.myloginandregister/databases/

You should see your .db file here (e.g., mydatabase.db).

Pull the Database File to Your PC:

Right-click the database file and choose "Save As...".
Save it to a location on your Windows system (e.g., Desktop or Documents).

Open in DB Browser for SQLite:

Launch DB Browser.
Click "Open Database" and select the file you just saved.
🛑 Important Notes:
The /data/data/... path is only accessible if your app is running in debug mode and the emulator is rooted (which most Android Studio emulators are).
If you don’t see the database, make sure your app has actually created it and that you're looking in the correct folder.

Would you like help writing a script to export the database programmatically or automate this process?  
