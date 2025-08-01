# React Native Face Detection App

A real-time face detection application built with React Native and Expo, featuring live camera feed analysis with animated face boundary detection and facial attribute tracking.

## 🎯 Features

### Face Detection Capabilities
- **Real-time Face Detection**: Live detection using device's front camera
- **Animated Face Boundaries**: Green animated borders that smoothly track detected faces
- **Facial Attribute Analysis**:
  - **Head Orientation**: Tracks yaw angle (Left/Center/Right)
  - **Pitch Detection**: Monitors head tilt (Up/Center/Down) 
  - **Eye State Monitoring**: Detects if eyes are open or closed
- **Face Counting**: Logs detection events with incremental counter
- **Smooth Animations**: Uses React Native Reanimated for fluid face tracking

### Technical Features
- Built with Expo SDK 53
- TypeScript support
- React Native Vision Camera integration
- ML Kit Face Detection
- Reanimated 3 for smooth animations

## 🚀 Getting Started

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn
- Android Studio (for Android development)
- Xcode (for iOS development, macOS only)
- Physical device or emulator with camera support

### Installation & Setup

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd face-detection
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Android Setup**
   
   Ensure you have:
   - Android SDK installed
   - NDK version 27.1.12297006 or compatible
   - Minimum SDK version 26 (required for face detection library)

4. **iOS Setup** (macOS only)
   ```bash
   cd ios && pod install && cd ..
   ```

### Running the Application

#### Development Server
```bash
# Start the Expo development server
npm start
# or
npx expo start
```

#### Android
```bash
# Run on Android device/emulator
npm run android
# or
npx expo run:android
```

#### iOS (macOS only)
```bash
# Run on iOS device/simulator
npm run ios
# or
npx expo run:ios
```

### Camera Permissions
The app will automatically request camera permissions on first launch. Ensure you grant camera access for the face detection to work properly.

## 📱 How It Works

1. **Camera Initialization**: The app initializes the front-facing camera
2. **Face Detection**: Uses ML Kit to analyze camera frames in real-time
3. **Boundary Drawing**: Draws animated green rectangles around detected faces
4. **Attribute Analysis**: Analyzes and displays:
   - Yaw angle for head rotation (Left/Center/Right)
   - Pitch angle for head tilt (Up/Center/Down)
   - Eye open probability for blink detection
5. **Live Updates**: All data updates in real-time as you move

## 🛠 Technology Stack

- **React Native 0.79.5**
- **Expo SDK 53**
- **TypeScript**
- **React Native Vision Camera** - Camera functionality
- **React Native Vision Camera Face Detector** - ML Kit integration
- **React Native Reanimated 3** - Smooth animations
- **React Native Worklets Core** - High-performance worklets

## 📦 Key Dependencies

```json
{
  "react-native-vision-camera": "^4.6.4",
  "react-native-vision-camera-face-detector": "^1.7.2",
  "react-native-reanimated": "~3.17.4",
  "react-native-worklets-core": "^1.6.0"
}
```

## 🔧 Configuration

### Face Detection Options
The app uses these optimized settings for accurate face detection:

```typescript
{
  performanceMode: 'accurate',
  landmarkMode: 'all',
  contourMode: 'none',
  classificationMode: 'all',
  trackingEnabled: false,
  autoScale: true
}
```

### Customization
You can modify face detection sensitivity by adjusting the angle thresholds in [`App.tsx`](App.tsx):

```typescript
// Yaw angle thresholds (head rotation)
yaw: face.yawAngle > 15 ? "Right" : face.yawAngle < -15 ? "Left" : "Center"

// Pitch angle thresholds (head tilt)  
pitch: face.pitchAngle > 15 ? "Up" : face.pitchAngle < -10 ? "Down" : "Center"

// Eye detection threshold
eye: face.leftEyeOpenProbability > 0.7 && face.rightEyeOpenProbability > 0.7 ? "Open" : "Close"
```

## 🐛 Troubleshooting

### Common Issues

1. **NDK Version Conflicts**
   - Ensure NDK 27.1.12297006 is installed
   - Check that minSdkVersion is set to 26 or higher

2. **Camera Permission Denied**
   - Manually grant camera permissions in device settings
   - Restart the application

3. **Face Detection Not Working**
   - Ensure good lighting conditions
   - Make sure camera is not obstructed
   - Check device compatibility with ML Kit

4. **Build Errors**
   ```bash
   # Clear cache and rebuild
   npx expo install --fix
   npm start -- --clear
   ```

## 📄 License

This project is licensed under the MIT License.

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

If you encounter any issues or have questions, please open an issue on GitHub.

---

Made with ❤️ using React Native and Expo
