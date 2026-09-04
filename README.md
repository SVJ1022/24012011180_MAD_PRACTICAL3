# 📱 Practical-3 --- Implicit & Explicit Intent

> **Aim:** Create an Android application which demonstrates implicit &
> explicit Intent.

------------------------------------------------------------------------

## 🎯 Objective

This practical demonstrates the use of **Implicit Intent** and
**Explicit Intent** in an Android application.

The application performs the following operations:

1.  Make call to a specific number
2.  Open specific URL
3.  Open Call Log
4.  Open Gallery
5.  Set Alarm
6.  Open Camera
7.  Open Login Activity

------------------------------------------------------------------------

## 🧩 Intent Types

### 1. Implicit Intent

An **Implicit Intent** is used when an action is requested without
specifying the exact Activity that should handle the operation.

In this practical, implicit intents are used for operations such as:

-   Making a call
-   Opening a URL
-   Opening Call Log
-   Opening Gallery
-   Setting an Alarm
-   Opening Camera

### 2. Explicit Intent

An **Explicit Intent** specifies the Activity that should be opened.

In this practical, an Explicit Intent is used to open the **Login
Activity**.

------------------------------------------------------------------------

## 📋 Operations

  Operation   Function
  ----------- ----------------------------------
  Make Call   Make a call to a specific number
  Open URL    Open a specified website
  Call Log    Open the device Call Log
  Gallery     Open the Gallery
  Set Alarm   Set/open the alarm operation
  Camera      Open the Camera
  Login       Open Login Activity

------------------------------------------------------------------------

## 🔄 Intent Flow

``` text
                    MainActivity
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
        Call            URL          Call Log
          │              │              │
          ├──────────────┼──────────────┤
          │              │              │
          ▼              ▼              ▼
      Gallery         Alarm          Camera
                         │
                         ▼
                  Login Activity
                  (Explicit Intent)
```

------------------------------------------------------------------------

## 🧩 Main Components

### MainActivity

`MainActivity` contains the UI controls for performing all the required
Intent operations.

### Login Activity

A separate Login Activity is created in the project and opened using an
**Explicit Intent**.

### Android Built-in Resources

The practical also studies Android built-in resources and drawable
resources required for the application.

------------------------------------------------------------------------

## 🛠️ Development Steps

1.  Create `MainActivity` according to the required UI.
2.  Add controls for each required operation.
3.  Implement an Intent for making a call to a specific number.
4.  Implement an Intent for opening a specific URL.
5.  Implement an Intent for opening the Call Log.
6.  Implement an Intent for opening the Gallery.
7.  Implement an Intent for setting an Alarm.
8.  Implement an Intent for opening the Camera.
9.  Create the Login Activity.
10. Use an Explicit Intent to open the Login Activity.
11. Test all operations on the device/emulator.

------------------------------------------------------------------------

## 📚 Concepts Covered

-   Intent
-   Implicit Intent
-   Explicit Intent
-   `startActivity()`
-   `Intent.ACTION_DIAL`
-   Call Log
-   Gallery
-   Camera
-   Alarm
-   URL handling
-   Activity navigation
-   Android built-in resources
-   Drawable resources
-   Creating Activity

------------------------------------------------------------------------

## 📁 Updated / Added Files

-   MainActiviy.kt
-   activity_main.xml
-   LoginActivity.kt
-   activity_login.xml
-   guni_pink_logo (added)

------------------------------------------------------------------------

## ▶️ How to Run

1.  Open the project in **Android Studio**.
2.  Build and run the application.
3.  Verify the main screen and its controls.
4.  Test the specific-number call operation.
5.  Test the URL button.
6.  Test the Call Log button.
7.  Test the Gallery button.
8.  Test the Alarm button.
9.  Test the Camera button.
10. Press Login and verify that the Login Activity opens.

------------------------------------------------------------------------

## 🖼️ OUTPUT
<table>
  <tr>
    <td align="center">
      <img width="330" height="600" alt="image" src="https://github.com/user-attachments/assets/bf53336a-ebe9-4034-babf-8441406c262d" />
    </td>
    <td align="center">
      <img width="330" height="600" alt="image" src="https://github.com/user-attachments/assets/ee3d0e84-40b0-4c07-b252-3ab1c89ee3f1" />
    </td>
  </tr>
  <tr>
    <td align="center"><b>Main Page</b></td>
    <td align="center"><b>Login Page</b></td>
  </tr>
</table>
------------------------------------------------------------------------

## ✅ Result

The Android application was successfully developed to demonstrate
**Implicit and Explicit Intents for call, URL, Call Log, Gallery, Alarm,
Camera and Activity navigation operations**.
