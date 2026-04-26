# FAQ - Android Webcam Bridge

Frequently Asked Questions about Android Webcam Bridge.

---

## 🔧 Installation & Setup

### Q: Do I need to install ADB separately?
**A:** Yes, ADB (Android Debug Bridge) is required. Download it from [Android Platform Tools](https://developer.android.com/tools/releases/platform-tools). Add it to your PATH for easy access, or use it directly from the downloaded folder.

### Q: How do I enable USB debugging on Android 10?
**A:** 
1. Open Settings
2. Go to **About Phone**
3. Tap **Build Number** 7 times
4. Go to **Developer Options** (now visible in Settings)
5. Enable **USB Debugging**
6. Authorize the connection when prompted

### Q: Can I use WiFi instead of USB?
**A:** Yes! The app supports WiFi streaming. The device must be on the same local network as your PC. WiFi may have higher latency (100-200ms vs 30-50ms on USB).

### Q: What if my device isn't detected?
**A:** 
- Reconnect the USB cable
- Authorize USB debugging on the device
- Run `adb kill-server` and `adb start-server`
- Try a different USB port (USB 3.0 recommended)

---

## 📹 Streaming & Recording

### Q: What resolution and frame rate does it support?
**A:** 
- **USB**: Up to 4K @ 30 FPS (device dependent)
- **WiFi**: Up to 1080p @ 30 FPS (depends on network)
- Default: 1920×1080 @ 30 FPS (adjustable)

### Q: Why is the video quality poor?
**A:** 
- Check your device's camera quality
- Try reducing resolution/frame rate
- USB connection is better than WiFi
- Ensure adequate bandwidth for bitrate

### Q: Can I record while streaming?
**A:** Yes! You can record to MP4 while simultaneously streaming to OBS/Zoom/Teams.

### Q: Where are recordings saved?
**A:** 
- Android: `/sdcard/Android/data/com.example.webcambridge/files/recordings/`
- Windows: `C:\Users\[YourUsername]\Videos\AndroidWebcam\`

### Q: What formats are supported?
**A:** MP4 (H.264 + AAC), MKV (H.264 + FLAC)

---

## 🎥 OBS Studio Integration

### Q: How do I add the virtual camera to OBS?
**A:** 
1. In OBS, click **+** under Sources
2. Select **Video Capture Device**
3. Choose **Android Webcam Bridge** from the dropdown
4. Click OK

### Q: The virtual camera isn't showing up in OBS
**A:** 
- Make sure Windows client is running
- Restart OBS
- Check that device is connected and streaming
- Try `dotnet run` in windows-client folder again

### Q: Can I use both video and audio in OBS?
**A:** Yes! Add the camera as a Video Capture Device, and the microphone will appear under Audio Input Capture.

---

## 🔊 Audio Issues

### Q: There's no audio coming through
**A:** 
- Check microphone permission on Android
- Ensure audio streaming is enabled
- Try restarting the app
- Check Windows audio settings (device might be set to disabled)

### Q: Audio is distorted or laggy
**A:** 
- Lower the recording volume on Android
- Check for other apps using the microphone
- Use USB connection instead of WiFi
- Reduce video quality to free up bandwidth

### Q: Can I use the microphone separately?
**A:** Yes, the virtual microphone will appear as a separate device in Windows sound settings.

---

## 💻 Integration with Apps

### Q: How do I set up Zoom?
**A:** 
1. Open Zoom Settings
2. Go to **Audio/Video**
3. Under **Camera**, select **Android Webcam Bridge**
4. Under **Microphone**, select the virtual mic
5. Do a test meeting to verify

### Q: Does it work with Microsoft Teams?
**A:** Yes! Follow the same steps as Zoom under Settings → Devices.

### Q: What about Discord?
**A:** 
1. Open Discord Settings
2. Go to **Voice & Video**
3. Select the camera and microphone under their respective dropdowns

### Q: Can I use it with multiple apps simultaneously?
**A:** Yes, as long as the app allows you to select a custom camera/microphone device.

---

## ⚡ Performance & Optimization

### Q: The stream is laggy - what can I do?
**A:** 
- Use USB instead of WiFi
- Reduce resolution (1280×720 instead of 1920×1080)
- Reduce frame rate (15 FPS instead of 30 FPS)
- Close other bandwidth-heavy apps
- Check CPU usage on Windows

### Q: Battery drains quickly on my Android
**A:** 
- Streaming consumes ~5-10% per hour
- Keep device plugged in if possible
- Reduce screen brightness
- Close background apps

### Q: What are the minimum PC requirements?
**A:** 
- **Processor**: Dual-core CPU (Intel i5 or equivalent)
- **RAM**: 4GB minimum, 8GB recommended
- **Storage**: 500MB free for app
- **Network**: USB 2.0+ or WiFi 5GHz recommended

### Q: Why is CPU usage high?
**A:** 
- H.264 encoding is CPU-intensive
- Try lower resolution/frame rate
- Close other applications
- Consider upgrading your PC

---

## 🔐 Security & Privacy

### Q: Is my data encrypted during streaming?
**A:** 
- USB: Protected by local connection
- WiFi: Recommended to use on trusted networks only
- Future version will add TLS encryption

### Q: Can others access my camera remotely?
**A:** 
- Local network only (USB or same WiFi)
- Cannot access over internet without VPN
- No cloud connectivity in current version

### Q: Where is my data stored?
**A:** 
- Streams are real-time, not stored
- Recordings stored locally on your devices
- No data sent to cloud services

---

## 🐛 Troubleshooting

### Q: "Connection refused" error
**A:** 
- Check if Android app is running
- Verify USB connection
- Run `adb forward tcp:8080 tcp:8080`
- Restart both apps

### Q: "Device not found"
**A:** 
- Reconnect USB cable
- Enable USB debugging on Android
- Run `adb devices` to verify connection
- Try different USB port

### Q: App crashes on Android
**A:** 
- Update to latest Android version
- Clear app cache: Settings → Apps → Android Webcam Bridge → Storage → Clear Cache
- Reinstall the app
- Check available storage space

### Q: Virtual camera not detected in Windows
**A:** 
- Restart Windows
- Reinstall virtual camera drivers
- Run Windows client as Administrator
- Check Device Manager for unknown devices

---

## 📱 Device Compatibility

### Q: Will this work on Android 8 or 9?
**A:** Current version requires Android 10+. Future versions may support older devices.

### Q: What about older Android 10 devices?
**A:** Should work, but may have performance issues. Please report if you encounter problems.

### Q: Does iOS (iPhone) work?
**A:** Not yet. iOS support is planned for v2.0.

### Q: Can I use multiple Android devices?
**A:** Future versions will support multi-device streaming.

---

## 🆘 Still Having Issues?

1. **Check Documentation**: Read docs/ folder for detailed guides
2. **Search Issues**: Check GitHub Issues for similar problems
3. **Create Issue**: Open a bug report with detailed information
4. **Ask Questions**: Use GitHub Discussions for help

---

## 📞 Getting Help

- **Documentation**: See [docs/](../docs/) folder
- **Troubleshooting**: See [docs/TROUBLESHOOTING.md](../docs/TROUBLESHOOTING.md)
- **GitHub Issues**: Report bugs at [Issues](https://github.com/kriravisarkar-0221/android-webcam-bridge/issues)
- **GitHub Discussions**: Ask questions at [Discussions](https://github.com/kriravisarkar-0221/android-webcam-bridge/discussions)

---

**Can't find your answer?** [Create an issue](https://github.com/kriravisarkar-0221/android-webcam-bridge/issues) or [start a discussion](https://github.com/kriravisarkar-0221/android-webcam-bridge/discussions)!
