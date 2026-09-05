# 📱 Practical-3 — Implicit & Explicit Intent

> **Aim:** Develop an Android application demonstrating the use of **Implicit Intent** and **Explicit Intent**.

---

## 🎯 Objective

This practical implements an Android application in Kotlin that uses Intents to perform different Android operations.

The project demonstrates:

- Opening a URL in a browser
- Opening the phone dialer with a supplied number
- Opening the Call Log
- Opening the Gallery/Image picker
- Opening the Camera
- Opening the Alarm application
- Opening another Activity using an Explicit Intent

The project contains two Activities:

```text
MainActivity
     │
     └── Explicit Intent ──► LoginActivity
```

---

## 📂 Project Structure

```text
24012011180_MAD_PRACTICAL3/
│
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/a24012011180_mad_practical_3/
│   │   │   │   ├── MainActivity.kt
│   │   │   │   └── LoginActivity.kt
│   │   │   ├── res/
│   │   │   │   └── ...
│   │   │   └── AndroidManifest.xml
│   │   └── ...
│   └── build.gradle.kts
│
├── gradle/
├── .gitignore
├── build.gradle.kts
├── gradle.properties
├── gradlew
├── gradlew.bat
├── settings.gradle.kts
└── README.md
```

---

# 🔗 What is an Intent?

An **Intent** is used to request an action from another Android component or application.

This project demonstrates two categories:

### 1. Implicit Intent

An implicit intent does not directly name the component that should handle the request. Android determines a suitable application/component.

Examples used in this project:

- Browser
- Dialer
- Call Log
- Gallery
- Camera
- Alarm application

### 2. Explicit Intent

An explicit intent identifies the Activity that should be opened.

This project uses an explicit intent to open:

```text
LoginActivity
```

from `MainActivity`.

---

# 🧩 Implicit Intent Operations

## 🌐 1. Browse URL

The `Browse` button reads the URL entered by the user and creates an `ACTION_VIEW` intent.

```kotlin
Intent(
    Intent.ACTION_VIEW,
    Uri.parse(findViewById<EditText>(R.id.url_text).text.toString())
)
```

The intent is then started using:

```kotlin
startActivity(it)
```

This allows a compatible browser application to handle the URL.

---

## 📞 2. Dial a Phone Number

The `Call` button reads a number from the input field and opens the phone dialer.

```kotlin
val intent = Intent(Intent.ACTION_DIAL)
intent.setData("tel:$number".toUri())
startActivity(intent)
```

`ACTION_DIAL` opens the dialer with the number prepared for dialing.

---

## 📋 3. Call Log

The application opens the device Call Log using:

```kotlin
Intent(
    Intent.ACTION_VIEW,
    Uri.parse("content://call_log/calls")
)
```

The intent is started with:

```kotlin
startActivity(intent)
```

---

## 🖼️ 4. Gallery

The Gallery/Image picker is opened using:

```kotlin
val intent = Intent(Intent.ACTION_PICK)
intent.type = "image/*"
startActivity(intent)
```

The `image/*` MIME type restricts the picker request to image content.

---

## 📷 5. Camera

The Camera application is opened using:

```kotlin
Intent(MediaStore.ACTION_IMAGE_CAPTURE)
```

The project then starts the intent:

```kotlin
startActivity(it)
```

---

## ⏰ 6. Alarm

The Alarm application is opened using Android's `AlarmClock` provider:

```kotlin
Intent(AlarmClock.ACTION_SHOW_ALARMS)
```

This displays the available alarms on the device.

---

# 🔐 Explicit Intent — Login Activity

The `Login` button demonstrates explicit Activity navigation.

```kotlin
Intent(
    this,
    LoginActivity::class.java
)
```

The intent is started with:

```kotlin
startActivity(it)
```

This directly opens `LoginActivity`.

---

# 🔄 Application Flow

```text
                  ┌─────────────────┐
                  │   MainActivity  │
                  └────────┬────────┘
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
       Browse            Call           Call Log
          │                │                │
          ▼                ▼                ▼
       Browser           Dialer         Call Log

          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
       Gallery           Camera           Alarm
          │                │                │
          ▼                ▼                ▼
       Image Picker     Camera App      Alarm App

                           │
                           ▼
                    ┌───────────────┐
                    │ Login Button  │
                    └───────┬───────┘
                            │
                     Explicit Intent
                            │
                            ▼
                    ┌───────────────┐
                    │ LoginActivity │
                    └───────────────┘
```

---

# 🧱 MainActivity

`MainActivity.kt` contains the main Intent implementation.

The Activity:

1. Enables edge-to-edge display.
2. Loads `activity_main`.
3. Applies system-bar insets.
4. Calls `implicitIntent()`.
5. Calls `explicitIntent()`.

```kotlin
implicitIntent()
explicitIntent()
```

---

# ⚙️ `implicitIntent()` Function

The function attaches click listeners to the following buttons:

```text
Browse
Call
Call Log
Gallery
Camera
Alarm
```

Each button creates and starts the appropriate Android Intent.

### Implemented APIs

| Operation | Android API |
|---|---|
| Browser | `Intent.ACTION_VIEW` |
| Dialer | `Intent.ACTION_DIAL` |
| Call Log | `Intent.ACTION_VIEW` |
| Gallery | `Intent.ACTION_PICK` |
| Camera | `MediaStore.ACTION_IMAGE_CAPTURE` |
| Alarm | `AlarmClock.ACTION_SHOW_ALARMS` |

---

# 🔐 `explicitIntent()` Function

The explicit intent is implemented separately.

```kotlin
fun explicitIntent() {
    findViewById<Button>(R.id.Login).setOnClickListener {
        Intent(this, LoginActivity::class.java).also {
            startActivity(it)
        }
    }
}
```

This keeps the external application operations separate from Activity-to-Activity navigation.

---

# 🧩 LoginActivity

`LoginActivity.kt` is the second Activity in the project.

Its main purpose in this practical is to provide a destination for the Explicit Intent from `MainActivity`.

The Activity:

- Extends `AppCompatActivity`
- Enables edge-to-edge display
- Loads `activity_login`
- Applies system-bar insets

```kotlin
setContentView(R.layout.activity_login)
```

---

# 📚 Concepts Covered

| Concept | Demonstration |
|---|---|
| Intent | Requesting an Android action |
| Implicit Intent | Opening external apps/services |
| Explicit Intent | Opening `LoginActivity` |
| `startActivity()` | Starting an Intent |
| `ACTION_VIEW` | Browser and Call Log |
| `ACTION_DIAL` | Phone dialer |
| `ACTION_PICK` | Image picker |
| `ACTION_IMAGE_CAPTURE` | Camera |
| `AlarmClock.ACTION_SHOW_ALARMS` | Alarm application |
| `Uri` | URL, telephone and Call Log data |
| MIME Type | `image/*` |
| Activity Navigation | Main → Login |
| Edge-to-Edge | Window display configuration |

---

# 🛠️ Development Steps

1. Create an Android Studio project.
2. Create the Main Activity layout.
3. Add input fields for URL and phone number.
4. Add buttons for Browse, Call, Call Log, Gallery, Camera, Alarm and Login.
5. Create a second `LoginActivity`.
6. Implement the implicit Intent operations.
7. Implement the explicit Intent for `LoginActivity`.
8. Run the application on an emulator or Android device.
9. Test each button individually.
10. Verify that the requested Android application/activity opens.

---

## ▶️ How to Run

1. Open the project in **Android Studio**.
2. Allow Gradle synchronization to complete.
3. Select an emulator or connected Android device.
4. Build the application.
5. Run the application.
6. Enter a URL and press **Browse**.
7. Enter a phone number and press **Call**.
8. Test **Call Log**, **Gallery**, **Camera** and **Alarm**.
9. Press **Login** to open `LoginActivity`.

> Some operations depend on the applications/services available on the Android device or emulator.

---

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

---

## 📌 Important Source Files

### Kotlin

- `MainActivity.kt`
- `LoginActivity.kt`

### Android

- `activity_main.xml`
- `activity_login.xml`
- `AndroidManifest.xml`

---

## ✅ Result

The Android application was successfully developed to demonstrate **Implicit Intent** and **Explicit Intent** operations, including browser, dialer, Call Log, Gallery, Camera, Alarm and Activity-to-Activity navigation.
