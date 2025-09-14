# 🔋 Wakelock Fixed

[![Pub version](https://img.shields.io/pub/v/wakelock_fixed.svg)](https://pub.dev/packages/wakelock_fixed)
[![GitHub stars](https://img.shields.io/github/stars/boughdiri-dorsaf/wakelock_fixed.svg)](https://github.com/boughdiri-dorsaf/wakelock_fixed)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Flutter](https://img.shields.io/badge/Flutter-02569B?logo=flutter&logoColor=white)](https://flutter.dev)

> **🚀 Enhanced & Fixed Version** of the popular wakelock plugin for Flutter

A robust, cross-platform Flutter plugin that prevents your device screen from sleeping. Perfect for apps that need to keep the display active during presentations, videos, games, or any interactive content.

---

## ✨ Features

- 🎯 **Zero Permissions Required** - Works out of the box on all platforms
- 🌍 **Cross-Platform Support** - Android, iOS, Web, macOS, Windows
- 🔧 **Simple API** - Just a few lines of code to get started
- 🛡️ **Reliable** - Fixed version with improved stability
- ⚡ **Lightweight** - Minimal overhead and dependencies
- 🎨 **Modern Design** - Clean, intuitive interface

## 📱 Supported Platforms

| Platform | Status | Notes |
|----------|--------|-------|
| 🤖 **Android** | ✅ **Fully Supported** | API 16+ |
| 🍎 **iOS** | ✅ **Fully Supported** | iOS 9.0+ |
| 🌐 **Web** | ✅ **Fully Supported** | All modern browsers |
| 🖥️ **macOS** | ✅ **Fully Supported** | macOS 10.11+ |
| 🪟 **Windows** | ✅ **Fully Supported** | Windows 10+ |
| 🐧 **Linux** | 🚧 **Coming Soon** | Planned for future release |

## 🚀 Quick Start

### 1. Add Dependency

Add this to your package's `pubspec.yaml` file:

```yaml
dependencies:
  wakelock_fixed: ^0.6.2
```

### 2. Import & Use

```dart
import 'package:wakelock_fixed/wakelock_fixed.dart';

// Keep screen awake
Wakelock.enable();

// Let screen sleep again
Wakelock.disable();

// Check current status
bool isActive = await Wakelock.enabled;
```

## 💡 Usage Examples

### Basic Usage

```dart
import 'package:flutter/material.dart';
import 'package:wakelock_fixed/wakelock_fixed.dart';

class MyApp extends StatefulWidget {
  @override
  _MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  bool _isWakelockEnabled = false;

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Wakelock Demo'),
          backgroundColor: Colors.deepPurple,
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Icon(
                _isWakelockEnabled ? Icons.battery_charging_full : Icons.battery_std,
                size: 64,
                color: _isWakelockEnabled ? Colors.green : Colors.grey,
              ),
              SizedBox(height: 20),
              Text(
                _isWakelockEnabled ? 'Screen is awake!' : 'Screen can sleep',
                style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
              ),
              SizedBox(height: 30),
              ElevatedButton.icon(
                onPressed: () async {
                  if (_isWakelockEnabled) {
                    await Wakelock.disable();
                  } else {
                    await Wakelock.enable();
                  }
                  setState(() {
                    _isWakelockEnabled = await Wakelock.enabled;
                  });
                },
                icon: Icon(_isWakelockEnabled ? Icons.pause : Icons.play_arrow),
                label: Text(_isWakelockEnabled ? 'Disable Wakelock' : 'Enable Wakelock'),
                style: ElevatedButton.styleFrom(
                  backgroundColor: _isWakelockEnabled ? Colors.red : Colors.green,
                  foregroundColor: Colors.white,
                  padding: EdgeInsets.symmetric(horizontal: 24, vertical: 12),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

### Advanced Usage

```dart
// Toggle wakelock with a boolean
await Wakelock.toggle(enable: true);

// Check if wakelock is currently active
bool isActive = await Wakelock.enabled;

// Enable wakelock and wait for completion
await Wakelock.enable();
print('Wakelock is now active!');

// Disable wakelock
await Wakelock.disable();
print('Wakelock has been disabled!');
```

### Proper Initialization

```dart
void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  
  // Enable wakelock if needed
  await Wakelock.enable();
  
  runApp(MyApp());
}
```

## 🎯 Best Practices

### ✅ Do's

- **Enable wakelock only when needed** (e.g., during video playback)
- **Disable wakelock when not needed** to save battery
- **Check wakelock status** before enabling/disabling
- **Use in specific widgets** rather than globally

### ❌ Don'ts

- **Don't enable wakelock globally** in main()
- **Don't forget to disable** wakelock when done
- **Don't ignore battery impact** on user devices

## 🔧 API Reference

### Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `Wakelock.enable()` | Enables the screen wakelock | `Future<void>` |
| `Wakelock.disable()` | Disables the screen wakelock | `Future<void>` |
| `Wakelock.toggle(enable: bool)` | Toggles wakelock on/off | `Future<void>` |

### Properties

| Property | Description | Type |
|----------|-------------|------|
| `Wakelock.enabled` | Current wakelock status | `Future<bool>` |

## 🆚 What's Fixed?

This is an enhanced version of the original wakelock plugin with the following improvements:

- 🔧 **Fixed Android build issues**
- 🛡️ **Improved error handling**
- ⚡ **Better performance**
- 🎯 **Enhanced reliability**
- 📱 **Updated dependencies**
- 🧪 **Better testing coverage**

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Original wakelock plugin by [creativecreatorormaybenot](https://github.com/creativecreatorormaybenot/wakelock)
- Flutter team for the amazing framework
- All contributors and users

## 📞 Support

If you encounter any issues or have questions:

- 📧 **Issues**: [GitHub Issues](https://github.com/boughdiri-dorsaf/wakelock_fixed/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/boughdiri-dorsaf/wakelock_fixed/discussions)
- 📖 **Documentation**: [Pub.dev](https://pub.dev/packages/wakelock_fixed)

---

<div align="center">

**⭐ Star this repository if you found it helpful!**

Made with ❤️ by [boughdiri-dorsaf](https://github.com/boughdiri-dorsaf)

</div>