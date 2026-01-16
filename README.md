# Minimal Weather App

A clean and minimal Flutter application that displays the current weather based on your GPS location using the WeatherAPI service. The app features animated weather icons and a simple UI layout.

## Features

- Detects your current city using device GPS
- Fetches live weather data (temperature, humidity, UV index)
- Shows Air Quality Index (US-EPA scale 1–6)
- Dynamic Lottie weather animations
- Clean card-style UI design
- Simple architecture and easy to understand
- API key stored in `.env` (create this)

## Tech Stack

**Framework**
- Flutter

**Packages**
- http
- geolocator
- geocoding
- lottie
- flutter_dotenv

## Project Structure

```
lib/
│
├── main.dart
├── pages/
│   └── weather_page.dart
├── models/
│   └── weather_model.dart
└── services/
    └── weather_service.dart
```

## Setup Instructions

### 1. Clone the repo

```sh
git clone https://github.com/YOUR-USERNAME/MinimalWeatherApp.git
cd MinimalWeatherApp
```

### 2. Install dependencies

```sh
flutter pub get
```

### 3. Create `.env` file in the project root

```
WEATHER_API_KEY=your_api_key_here
```

### 4. Add assets to `pubspec.yaml`

```yaml
flutter:
  uses-material-design: true

  assets:
    - images/
    - .env
```

### 5. Run the app

```sh
flutter run
```

## Permissions

Android requires location permissions. Make sure your `AndroidManifest.xml` includes:

```xml
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```

The app will request permission at runtime.

## How It Works

- `WeatherPage` builds the UI and calls `_fetchWeather()`
- `_fetchWeather()` gets the current city name using `Geolocator` + `placemarkFromCoordinates`
- `WeatherService.getWeather()` calls WeatherAPI
- Response JSON is converted into a `Weather` object
- UI updates with the received data using `setState`
- `getWeatherAnimation()` returns the correct Lottie animation based on the condition string

## Weather Animations

The app uses Lottie designs:

- cloudy.json
- rain.json
- snow.json
- thunder.json
- clear.json (default)

Animation changes are based on keyword matching (`"rain"`, `"cloud"`, `"clear"`, etc.).

## Future Improvements

- Search by city name
- Forecast (5-day / hourly)
- Dark mode
- Persistent recent searches
- Custom animated icons
- Favorite locations
- Offline caching

## Credits

- Weather data from **OpenWeather.com**
- Animations by **Lottie**
- Built with Flutter

## 📄 License

MIT License
