# Ex_No_4-Display Contact Details Using Content Provider
Develop program to create your own content providers to get contacts details using Android Studio.

# AIM:
To develop a program to create your own content providers to get contacts details using Android Studio.

# EQUIPMENTS REQUIRED:
Android Studio(Min. required Artic Fox)

# ALGORITHM:
Step 1: Open Android Studio and then click on File -> New -> New project.

Step 2: Then type the Application name as Contentprovider and click Next.

Step 3: Select the Minimum SDK below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally, click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Create a button with the name of Get contacts details in .xml File

Step 7: By clicking the button displays the contact details in the output screen using MainActivity File.

Step 8: Save and run the application.

# Program:

Developed by: ARVIND S

RegisterNumber: 212222240012

# MainActivity.java:
```
package com.example.exp4;

import androidx.appcompat.app.AppCompatActivity;
import android.content.ContentValues;
import android.content.Context;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;
import androidx.core.content.ContextCompat;
import android.Manifest;
import android.annotation.SuppressLint;
import android.content.ContentResolver;
import android.content.pm.PackageManager;
import android.database.Cursor;
import android.net.Uri;
import android.os.Bundle;
import android.provider.ContactsContract;
import android.util.Log;
import android.view.View;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
    public void btnGetContacts(View v){
        getPhoneContacts();
    }
    private void getPhoneContacts(){
        if(ContextCompat.checkSelfPermission(this, Manifest.permission.READ_CONTACTS)!= PackageManager.PERMISSION_GRANTED){
            ActivityCompat.requestPermissions(this,new String[]{Manifest.permission.READ_CONTACTS},0);
        }
        ContentResolver contentResolver = getContentResolver();
        Uri uri = ContactsContract.CommonDataKinds.Phone.CONTENT_URI;
        Cursor cursor = contentResolver.query(uri,null,null,null,null,null);
        Log.i("CONTACT_PROVIDER","TOTAL # of CONTACTS ::: "+Integer.toString(cursor.getCount()));

        if(cursor.getCount()>0){
            while(cursor.moveToNext()){
                @SuppressLint("Range") String ContactName = cursor.getString(cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME));
                @SuppressLint("Range") String contactNumber = cursor.getString(cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.NUMBER));
                Log.i("CONTACT_PROVIDER_DEMO","Contact Name ::: "+ ContactName+"ph# ::: "+contactNumber);
            }
        }
    }
}
```
# activity_main.xml:

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/relativeLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="162dp"
        android:layout_marginEnd="158dp"
        android:layout_marginBottom="340dp"
        android:text="Get Contact Details"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.525"
        app:layout_constraintStart_toStartOf="parent"
        android:onClick="btnGetContacts" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
# AndroidManifest.xml

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" package = "com.example.exp4" >
    <uses-permission android:name="android.permission.READ_CONTACTS"/>
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="exp4"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.EXP4"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```
# OUTPUT :
![image](https://github.com/user-attachments/assets/7f7ecc3f-2318-4f28-80f7-eae28ecc4778)

![image](https://github.com/user-attachments/assets/25faa5cf-9543-4948-bec0-f40caa7f674c)

# RESULT :
Thus a Simple Android Application to create your own content providers get contact details using Android Studio was developed and executed successfully.

