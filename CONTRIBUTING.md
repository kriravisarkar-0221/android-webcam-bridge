# Contributing to Android Webcam Bridge

Thank you for your interest in contributing! This document provides guidelines and instructions for contributing to the project.

## 📋 Code of Conduct

This project is committed to providing a welcoming and inclusive environment. Please be respectful and constructive in all interactions.

---

## 🚀 Getting Started

### Prerequisites

#### Android Development
- Android Studio 2021.1+
- JDK 11+
- Android SDK 31+
- Gradle 7.0+

#### Windows Development
- Visual Studio 2019+ or VS Code
- .NET 6.0 SDK
- Windows 10+ (for testing)

### Setup Development Environment

```bash
# Clone the repository
git clone https://github.com/kriravisarkar-0221/android-webcam-bridge.git
cd android-webcam-bridge

# Android setup
cd android-app
./gradlew clean build

# Windows setup
cd ../windows-client
dotnet restore
dotnet build
```

---

## 📝 Development Workflow

### 1. Fork and Branch

```bash
# Fork on GitHub, then:
git clone https://github.com/YOUR_USERNAME/android-webcam-bridge.git
cd android-webcam-bridge
git checkout -b feature/your-feature-name
# or
git checkout -b fix/your-bug-fix
```

### 2. Commit Guidelines

```bash
# Good commit messages
git commit -m "feat: add H.264 encoding support"
git commit -m "fix: resolve WiFi connection timeout"
git commit -m "docs: update OBS integration guide"
git commit -m "test: add unit tests for VideoEncoder"

# Format: <type>: <description>
# Types: feat, fix, docs, test, refactor, perf, style, chore
```

### 3. Push and Create PR

```bash
git push origin feature/your-feature-name
# Create PR on GitHub with clear description
```

---

## 🎯 Areas for Contribution

### High Priority
1. **HEVC Codec Support** - Add H.265 encoding
2. **Noise Cancellation** - Implement audio denoising
3. **Bluetooth Support** - Add Bluetooth streaming
4. **Performance** - Optimize latency and battery usage

### Medium Priority
1. **Documentation** - Platform-specific guides
2. **Testing** - Add unit and integration tests
3. **UI/UX** - Improve user interface
4. **Community Support** - Help answer issues

### Good for Beginners
1. **Documentation improvements**
2. **UI fixes and enhancements**
3. **Test coverage**
4. **Code refactoring**

---

## 💻 Code Style

### Kotlin (Android)

```kotlin
// Use standard Kotlin conventions
// - camelCase for variables/functions
// - PascalCase for classes
// - UPPER_CASE for constants

class VideoEncoder {
    companion object {
        private const val TAG = "VideoEncoder"
        private const val TARGET_BITRATE = 5000000 // bits per second
    }
    
    fun encodeFrame(image: Image): ByteArray {
        // Implementation
    }
}

// Document public functions
/**
 * Encodes the given image frame using H.264 codec.
 *
 * @param image The camera frame to encode
 * @return Encoded byte array or null if encoding fails
 */
fun encodeFrame(image: Image): ByteArray? {
    // ...
}
```

### C# (.NET)

```csharp
// Use standard C# conventions
// - camelCase for variables/methods
// - PascalCase for classes/properties

public class VirtualCameraDriver
{
    private const string TAG = "VirtualCameraDriver";
    private const int TargetBitrate = 5000000;
    
    public byte[] EncodeFrame(Image image)
    {
        // Implementation
    }
}

/// <summary>
/// Encodes the given image frame using H.264 codec.
/// </summary>
/// <param name="image">The camera frame to encode</param>
/// <returns>Encoded byte array or null if encoding fails</returns>
public byte[] EncodeFrame(Image image)
{
    // ...
}
```

---

## 🧪 Testing

### Android Tests

```bash
# Run all tests
cd android-app
./gradlew test

# Run specific test
./gradlew test --tests "com.example.webcambridge.VideoEncoderTest"

# Run instrumented tests
./gradlew connectedAndroidTest
```

### Windows Tests

```bash
cd windows-client
dotnet test
dotnet test --filter "Category=Integration"
```

### Test Requirements

- Tests for all new features
- Minimum 80% code coverage
- Both unit and integration tests
- Clear test descriptions

---

## 📚 Documentation

### When to Update Docs

1. **New Features** - Add to relevant guide
2. **API Changes** - Update API.md
3. **Bug Fixes** - Add troubleshooting tip if needed
4. **Configuration** - Update setup guides

### Documentation Template

```markdown
## Feature Name

### Description
Clear explanation of what this is and why it's useful.

### How to Use
Step-by-step instructions.

### Configuration
Any configurable options.

### Examples
Real-world examples.

### Troubleshooting
Common issues and solutions.
```

---

## 🐛 Bug Fixes

### Process

1. **Create an issue** describing the bug
2. **Discuss** if it needs clarification
3. **Create a branch** for the fix
4. **Write a test** that reproduces the bug
5. **Fix the code**
6. **Verify the test** now passes
7. **Create a PR** with the fix

### Example

```kotlin
// Test (shows the bug)
@Test
fun videoEncoder_shouldEncodeWithCorrectBitrate() {
    val encoder = VideoEncoder(bitrate = 5000000)
    val frame = createTestFrame()
    
    val encoded = encoder.encode(frame)
    
    // This test fails before the fix
    assertEquals(5000000, encoder.actualBitrate)
}

// Fix
class VideoEncoder(val bitrate: Int) {
    var actualBitrate = bitrate
    
    fun encode(frame: Image): ByteArray {
        // Apply the bitrate correctly
        configureCodec(bitrate)
        actualBitrate = bitrate
        return encodeFrame(frame)
    }
}
```

---

## ✨ New Features

### Process

1. **Discuss in an issue** first
2. **Get feedback** from maintainers
3. **Design and plan** the implementation
4. **Implement** with tests
5. **Update documentation**
6. **Create a PR** with the feature

### Requirements

- ✅ Tests covering the feature
- ✅ Updated documentation
- ✅ No breaking changes (or discussed)
- ✅ Performance impact analyzed
- ✅ Works on target platforms

---

## 🔍 PR Review Process

### What We Look For

- ✅ Code quality and style
- ✅ Test coverage
- ✅ Documentation updates
- ✅ No breaking changes
- ✅ Performance considerations
- ✅ Platform compatibility

### Review Timeline

- Simple changes: 1-3 days
- Medium changes: 3-7 days
- Large changes: 1-2 weeks

### Addressing Feedback

1. Read all comments
2. Discuss disagreements respectfully
3. Make requested changes
4. Push new commits (don't force-push)
5. Comment when ready for re-review

---

## 📦 Release Process

### Versioning

Follows semantic versioning: `MAJOR.MINOR.PATCH`

- `MAJOR`: Breaking changes
- `MINOR`: New features (backward compatible)
- `PATCH`: Bug fixes

### Release Timeline

- Every 2 weeks: Patch releases
- Monthly: Minor releases
- Quarterly: Major releases

### Release Checklist

- [ ] All tests pass
- [ ] Documentation updated
- [ ] CHANGELOG updated
- [ ] Version bumped
- [ ] Tag created
- [ ] Release notes written

---

## 📞 Communication

### For Questions

- **GitHub Discussions**: General questions and ideas
- **GitHub Issues**: Specific bugs or features
- **Pull Requests**: Code changes

### Response Times

- Issues/PRs: 24-48 hours
- Discussions: 2-3 days

### Getting Help

1. Check existing issues/discussions
2. Read documentation
3. Create an issue with details
4. Ask in discussions

---

## 🎁 Recognition

Contributors will be recognized in:
- README.md contributors section
- Release notes
- Project website

---

## ⚖️ License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

## 📋 Checklist Before Submitting PR

- [ ] I've read CONTRIBUTING.md
- [ ] My code follows style guidelines
- [ ] I've tested thoroughly
- [ ] I've added/updated tests
- [ ] I've updated documentation
- [ ] I've committed with clear messages
- [ ] My PR has a clear description
- [ ] No unrelated changes included

---

## 🙏 Thank You!

We appreciate your contributions to making Android Webcam Bridge better for everyone!

**Questions?** Open an issue or start a discussion.

**Ready to contribute?** Pick an issue and get started! 🚀

---

**Happy coding! 💻**
