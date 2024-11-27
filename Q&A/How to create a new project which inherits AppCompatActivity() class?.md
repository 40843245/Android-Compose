# How to create a new project which inherits AppCompatActivity() class?
## Answer from Microsoft Bing
To create a new project in Android Studio that inherits from AppCompatActivity, follow these steps:

1. Open Android Studio: Start by launching Android Studio.

2. Create a New Project:

3. Click on "Start a new Android Studio project".
4. Choose a project template. For example, you can select "Empty Activity".
5. Click "Next".
6. Configure Your Project:

  1. Enter the name of your application.
  2. Specify the package name and save location.
  3. Choose the language (Java or Kotlin).
  4. Set the minimum API level.
  5. Click "Finish".
  6. Modify the MainActivity:

    By default, the MainActivity will extend AppCompatActivity.
    If it doesn't, open MainActivity.java or MainActivity.kt and ensure it extends AppCompatActivity:

    ```
    public class MainActivity extends AppCompatActivity {
        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_main);
        }
    }
  ```

  7. Update the Manifest:

  Ensure your AndroidManifest.xml file includes the MainActivity and uses a compatible theme:

  ```
  <application
      android:theme="@style/Theme.AppCompat.Light.NoActionBar">
      <activity android:name=".MainActivity">
          <intent-filter>
              <action android:name="android.intent.action.MAIN" />
              <category android:name="android.intent.category.LAUNCHER" />
          </intent-filter>
      </activity>
  </application>
  ```

This setup ensures your project uses `AppCompatActivity`, which provides compatibility support for older Android versions.
