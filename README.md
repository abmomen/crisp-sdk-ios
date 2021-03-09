![Crisp](./.github/logo.png)

Chat with app users, integrate your favorite tools, and deliver a great customer experience.

# Crisp iOS SDK


<img src="./.github/screenshot.png" width="375" alt="Crisp screenshot">

[![CocoaPods](https://img.shields.io/cocoapods/v/Crisp.svg)](https://cocoapods.org/?q=crisp)
[![Twitter](https://img.shields.io/badge/twitter-@crisp_im-blue.svg?style=flat)](http://twitter.com/crisp_im)


## How to use

### Video tutorial


<p align="left">
  <a href="https://www.youtube.com/watch?v=vb1F23uRkEo">
    <img alt="Play Introduction Video" src="https://img.youtube.com/vi/vb1F23uRkEo/0.jpg" width="560">
  </a>
</p>

### 1. Install Crisp iOS SDK

#### Option 1: Using SwiftPM

To use the Crisp iOS SDK with SPM, add a dependency to your Package.swift file:

```swift
let package = Package(
  dependencies: [
    .package(url: "https://github.com/crisp-im/crisp-sdk-ios.git", ...)
  ]
)
```

#### Option 2: Using [CocoaPods](http://cocoapods.org)

Add Crisp to your Podfile:

```ruby
use_frameworks!

target :YourTargetName do
  pod 'Crisp'
end
```

Then run  `pod install`

#### Option 3: Manual installation

1. Download and extract the [Crisp iOS SDK](https://github.com/crisp-im/crisp-sdk-ios/releases).
2. Drag the `Crisp.xcframework` into your project, select `Copy items if needed` in the following dialog and click `Finish`.

<img src="./.github/manual_install_1.png" width="443" alt="Drag framework to project">
<img src="./.github/manual_install_2.png" width="698" alt="Copy items if needed">

3. Finally, configure the `Crisp.xcframework` to `Embed & Sign` in the `Frameworks, Libraries, and Embedded Content` section of your app's target settings.

<img src="./.github/manual_install_3.png" width="698" alt="Embed and Sign">

### 2. Update your Info.plist

To enable your users to take and upload photos to the chat as well as download photos to their photo library, add the
`Privacy - Camera Usage Description` ([NSCameraUsageDescription](https://developer.apple.com/documentation/bundleresources/information_property_list/nscamerausagedescription)) and `Privacy - Photo Library Additions Usage Description` ([NSPhotoLibraryAddUsageDescription](https://developer.apple.com/documentation/bundleresources/information_property_list/nsphotolibraryaddusagedescription)) to your app's Info.plist.

<img src="./.github/update_info_plist.png" width="900" alt="Update Info.plist">

### 3. Configure the Crisp iOS SDK

Go to your Crisp dashboard (https://app.crisp.chat), copy your website id from the resulting URL and configure the `CrispSDK` in your app's `AppDelegate`.

<img src="./.github/copy_website_id.png" width="900" alt="Copy website id">

<img src="./.github/configure_sdk.png" width="900" alt="Configure CrispSDK">

```Swift
import Crisp

// In your func application()
CrispSDK.configure(websiteID: "YOUR_WEBSITE_ID")
```

### 4. Present the `ChatViewController`

<img src="./.github/present_viewcontroller.png" width="900" alt="Present ChatViewController">

```Swift
import Crisp

class ViewController: UIViewController {
    @IBAction func startChat(_ sender: Any) {
        self.present(ChatViewController(), animated: true)
    }
}
```

## API Usage (Swift):

* `CrispSDK.setTokenID(tokenID: "A_CUSTOM_ID")` Assigns session with a token_id
* `CrispSDK.user.email = "john.doe@gmail.com"` Sets user email
* `CrispSDK.user.nickname = "John Name"` Sets user name
* `CrispSDK.user.phone = "003370123456789"` Sets user phone
* `CrispSDK.user.avatar = URL(string: "https://pbs.twimg.com/profile_images/782474226020200448/zDo-gAo0_400x400.jpg")` Sets user avatar
* `CrispSDK.user.company = Company(name: "Acme", url: nil, companyDescription: nil, employment: nil, geolocation: nil)` Sets user compay

* `CrispSDK.session.setString("custom_value", forKey: "custom_key")` Sets session data string
* `CrispSDK.session.setInt(42, forKey: "custom_key")` Sets session data int
* `CrispSDK.session.pushEvent(SessionEvent(name: "Signup", color: SessionEventColor.blue))` Sets Sends an event
* `CrispSDK.session.segment = "app"` Sets session segment
* `CrispSDK.session.reset()` Reset session

## Credits

Crisp iOS SDK is owned and maintained by [Crisp IM, SARL](https://crisp.chat/en/). You can chat with us on [crisp](https://crisp.chat) or follow us on Twitter at [Crisp_im](http://twitter.com/crisp_im)

## License

Crisp iOS SDK is under Copyright license. see [LICENSE](https://raw.githubusercontent.com/crisp-im/crisp-sdk-ios/master/LICENSE) for more details.
