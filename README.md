

# 🌤️ Real-Time Weather App with Retrofit  

This project is a beautifully designed **Real-Time Weather App** built using **Kotlin** and **Jetpack Compose**. It fetches live weather data from an external API using **Retrofit**, ensuring fast and reliable communication with the server.  

---

## 📱 Features  

- **Live Weather Updates**: Get current weather conditions in real time.  
- **Search Functionality**: Search for any city to view its weather details.  
- **Responsive Design**: A clean and user-friendly interface designed with Jetpack Compose.  
- **Detailed Weather Data**:  
  - Temperature (Celsius/Fahrenheit)  
  - Humidity  
  - Wind speed and direction  
  - Pressure  
  - Cloud cover  
  - Rainfall and visibility  
- **Lazy Grid Display**: View detailed weather attributes in a structured grid layout.  

---

## 🛠️ Technologies Used  

- **Kotlin**  
- **Jetpack Compose**  
- **Retrofit**: For network requests and API integration.  
- **Material3 Design**: For a modern and sleek UI.  

---

## 🏗️ Setup and Installation  

1. Clone this repository:  
   ```bash  
   git clone https://github.com/your-username/your-repository-name.git  
   ```  

2. Open the project in **Android Studio**.  

3. Add your API key to the project:  
   - Navigate to the `Constants.kt` or wherever the API key is being used.  
   - Replace `"YOUR_API_KEY"` with your actual API key from the weather API provider.  

4. Build and run the project on an emulator or a physical device.  

---

## 🔗 API Integration  

This app uses **Retrofit** to fetch weather data from the [WeatherAPI](https://www.weatherapi.com/) (or any other provider you're using).  

### Example API Call:  
```kotlin  
@GET("v1/current.json")  
suspend fun getCurrentWeather(  
    @Query("key") apiKey: String,  
    @Query("q") city: String  
): Response<CurrentWeatherResponse>  
```  

---

## 🎨 Demo 


https://github.com/user-attachments/assets/d6decea9-ae1b-4a8a-9e8b-55e8b140bf9a



---

## 📂 Project Structure  

- **`ui`**: Jetpack Compose UI components.  
- **`network`**: Retrofit API service and related classes.  
- **`model`**: Data classes for parsing JSON responses.  

---

## 🤝 Contribution  

Contributions, issues, and feature requests are welcome! Feel free to fork this repository and make changes.  

1. Fork the repository.  
2. Create your feature branch: `git checkout -b feature/your-feature-name`.  
3. Commit your changes: `git commit -m 'Add some feature'`.  
4. Push to the branch: `git push origin feature/your-feature-name`.  
5. Open a pull request.  

---

## 🛡️ License  

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.  

---

## 📝 Acknowledgements  

- [WeatherAPI](https://www.weatherapi.com/) for providing real-time weather data.  
- The Android development community for their extensive documentation and support.  

---

**🌟 If you like this project, give it a star ⭐ on GitHub!**  

Let me know if you'd like further tweaks! 🚀
