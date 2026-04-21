<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,14,24&height=200&section=header&text=AuraWeather%20🌤️&fontSize=50&fontColor=fff&animation=twinkling&fontAlignY=36&desc=Real-time%20weather%2C%20beautifully%20presented&descAlignY=56&descSize=18" width="100%"/>

[![Kotlin](https://img.shields.io/badge/Kotlin-1.9+-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)](https://kotlinlang.org)
[![Jetpack Compose](https://img.shields.io/badge/Jetpack%20Compose-UI-4285F4?style=for-the-badge&logo=jetpackcompose&logoColor=white)](https://developer.android.com/jetpack/compose)
[![Retrofit](https://img.shields.io/badge/Retrofit-Networking-48B983?style=for-the-badge&logo=square&logoColor=white)](https://square.github.io/retrofit/)
[![Material3](https://img.shields.io/badge/Material%203-Design-757575?style=for-the-badge&logo=materialdesign&logoColor=white)](https://m3.material.io/)
[![Android](https://img.shields.io/badge/Android-API%2026+-3DDC84?style=for-the-badge&logo=android&logoColor=white)](https://developer.android.com)
[![WeatherAPI](https://img.shields.io/badge/WeatherAPI-Live%20Data-00BFFF?style=for-the-badge&logo=cloudflare&logoColor=white)](https://www.weatherapi.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blueviolet?style=for-the-badge)](https://opensource.org/licenses/MIT)

> *Live weather data. Clean UI. Zero compromise.*

[✨ Features](#-features) · [🎬 Demo](#-demo) · [🛠 Tech Stack](#-tech-stack) · [⚙️ Setup](#%EF%B8%8F-setup) · [🔗 API](#-api-integration) · [📁 Structure](#-project-structure) · [👤 Author](#-author)

</div>

---

## 📖 Overview

**AuraWeather** is a beautifully designed real-time weather app built with **Kotlin** and **Jetpack Compose**. It fetches live weather data from the [WeatherAPI](https://www.weatherapi.com/) using **Retrofit** for fast, reliable network communication.

The app delivers an instant, glanceable view of current conditions with rich detail — temperature, humidity, wind, pressure, cloud cover, visibility and more — all wrapped in a clean Material 3 UI.

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 🌡️ Live Weather Updates
Get **real-time current conditions** for any city, updated on demand. No stale data — every request hits the live API.

</td>
<td width="50%">

### 🔍 City Search
Search any city worldwide by name. Results appear instantly with full condition data pulled directly from WeatherAPI.

</td>
</tr>
<tr>
<td width="50%">

### 📊 Detailed Weather Data
A rich set of weather attributes displayed in a structured **Lazy Grid** layout:

| Metric | Details |
|---|---|
| 🌡️ Temperature | Celsius / Fahrenheit toggle |
| 💧 Humidity | Relative % |
| 🌬️ Wind | Speed + direction |
| 🔵 Pressure | hPa reading |
| ☁️ Cloud Cover | % coverage |
| 🌧️ Rainfall | mm |
| 👁️ Visibility | km |

</td>
<td width="50%">

### 🎨 Clean Compose UI
Built entirely with **Jetpack Compose** and **Material 3** design:

- Responsive layout that adapts to any screen size
- Glassmorphism-inspired weather cards
- Smooth loading states & error handling
- Dark-mode ready

</td>
</tr>
</table>

---

## 🎬 Demo

https://github.com/user-attachments/assets/d6decea9-ae1b-4a8a-9e8b-55e8b140bf9a

---

## 🛠 Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| **Language** | Kotlin 1.9+ | Modern, concise Android development |
| **UI** | Jetpack Compose | Declarative, reactive UI with zero XML |
| **Design System** | Material 3 | Modern, accessible component library |
| **Networking** | Retrofit 2 | Type-safe HTTP client for REST API calls |
| **JSON** | Gson / Moshi | Deserializing API responses to data classes |
| **Async** | Kotlin Coroutines | Non-blocking network requests |
| **Architecture** | MVVM | Clean separation of UI and business logic |
| **Min SDK** | API 26 (Android 8.0) | Wide device compatibility |

---

## ⚙️ Setup

### Prerequisites

- **Android Studio** Hedgehog (2023.1.1) or later
- **Android SDK** API 26+
- A free API key from [WeatherAPI.com](https://www.weatherapi.com/) (sign up takes 1 minute)

### Clone & Configure

```bash
# 1. Clone the repository
git clone https://github.com/Divyansh5070/AuraWeather.git
cd AuraWeather
```

2. Open the project in **Android Studio** and let Gradle sync

3. Add your API key — navigate to `app/src/main/java/.../utils/Constants.kt` and replace:
   ```kotlin
   const val API_KEY = "YOUR_API_KEY_HERE"
   ```
   with your actual key from [weatherapi.com](https://www.weatherapi.com/my/)

4. Select a device or emulator (**API 26+**) and hit **Run** (`⇧F10`)

> 💡 The free WeatherAPI tier gives 1 million calls/month — more than enough for development and personal use.

---

## 🔗 API Integration

This app uses **Retrofit** to communicate with the [WeatherAPI](https://www.weatherapi.com/) REST endpoint.

### Retrofit Service Interface

```kotlin
interface WeatherApiService {

    @GET("v1/current.json")
    suspend fun getCurrentWeather(
        @Query("key") apiKey: String,
        @Query("q") city: String
    ): Response<CurrentWeatherResponse>
}
```

### Sample JSON Response (abbreviated)
```json
{
  "location": { "name": "London", "country": "UK" },
  "current": {
    "temp_c": 14.0,
    "feelslike_c": 12.5,
    "humidity": 72,
    "wind_kph": 18.4,
    "wind_dir": "WSW",
    "pressure_mb": 1012.0,
    "cloud": 50,
    "vis_km": 10.0,
    "precip_mm": 0.0,
    "condition": { "text": "Partly cloudy" }
  }
}
```

---

## 📁 Project Structure

```
AuraWeather/
├── app/
│   └── src/main/java/com/divyansh/auraweather/
│       ├── model/
│       │   ├── CurrentWeatherResponse.kt   ← Gson data classes
│       │   ├── Location.kt
│       │   └── Current.kt
│       ├── network/
│       │   ├── WeatherApiService.kt        ← Retrofit interface
│       │   └── RetrofitInstance.kt         ← Singleton client setup
│       ├── repository/
│       │   └── WeatherRepository.kt        ← Data layer
│       ├── ui/
│       │   ├── screens/
│       │   │   └── WeatherScreen.kt        ← Main Compose screen
│       │   ├── components/
│       │   │   ├── WeatherCard.kt          ← Condition display card
│       │   │   └── WeatherDetailGrid.kt    ← Lazy grid attributes
│       │   └── theme/
│       │       ├── Color.kt
│       │       ├── Theme.kt
│       │       └── Type.kt
│       ├── utils/
│       │   └── Constants.kt               ← API key & base URL
│       └── MainActivity.kt
├── build.gradle.kts
├── settings.gradle.kts
└── README.md
```

---

## 🗺 Roadmap

- [x] Real-time current weather via WeatherAPI
- [x] City search by name
- [x] Celsius / Fahrenheit toggle
- [x] Detailed lazy grid (humidity, wind, pressure, visibility…)
- [x] Material 3 UI with Jetpack Compose
- [ ] 7-day forecast view
- [ ] GPS auto-location on launch
- [ ] Hourly forecast chart
- [ ] Multiple saved cities
- [ ] Home screen weather widget
- [ ] Offline caching with Room

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

```bash
# Fork → clone → create branch
git checkout -b feature/your-feature-name

# Make your changes, then commit
git commit -m "feat: add your feature description"

# Push and open a PR
git push origin feature/your-feature-name
```

---

## 👤 Author

<div align="center">

**Divyansh Sharma**  
BTech CSE · Chandigarh University

[![GitHub](https://img.shields.io/badge/GitHub-Divyansh5070-181717?style=for-the-badge&logo=github)](https://github.com/Divyansh5070)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Divyansh%20Sharma-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/divyansh-sharma-12a52028a)

</div>

---

## 📝 Acknowledgements

- [WeatherAPI.com](https://www.weatherapi.com/) — for providing fast, reliable real-time weather data
- [Square / Retrofit](https://square.github.io/retrofit/) — making REST API integration a joy
- The Android & Jetpack Compose community for incredibly thorough documentation

---

## 📄 License

This project is open source under the [MIT License](LICENSE).

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,14,24&height=100&section=footer" width="100%"/>

*Built with ❤️ using Kotlin & Jetpack Compose*

⭐ If you found this useful, please consider giving it a star!

</div>
