<p>
<img src="https://img.shields.io/badge/Swift-5.1-orange.svg" />
<a href="https://swift.org/package-manager">
    <img src="https://img.shields.io/badge/swiftpm-compatible-brightgreen.svg?style=flat" alt="Swift Package Manager" />
</a>
 <img src="https://img.shields.io/badge/platforms-iOS_13.0_+%20tvOS_13.0-brightgreen.svg?style=flat" alt="iOS 13.0 + tvOS 13.0" />
</p>

_Mattt's_ beautiful gist to gain SwiftUI previews for your UIViews turned into Swift Package.

# UIViewPreview Swift Package

Swift Package contains:
* `UIViewPreview`
* `UIViewControllerPreview`


Please read more about the use-cases for `UIViewPreview` in the `NSHipster` blogpost:
[https://nshipster.com/swiftui-previews/](https://nshipster.com/swiftui-previews/)

## Requirements:
* macOS Catalina
* Xcode 11.0 and above
* Swift 5.1 and above
* iOS 13.0 and above
* tvOS 13.0 and above

## Installation
### Swift Package Manager

Add
`.package(url: "https://github.com/bielikb/UIViewPreview.git", from: "1.0.0")`
to your `Package.swift` file's `dependencies`.

If youre using Xcode 11.0 add `UIViewPreview` Swift Package to your target(s) using Xcode.

## PreviewProvider (Official Apple Docs)

```
/// Produces view previews in Xcode.
///
/// Xcode statically discovers types that conform to `PreviewProvider` and
/// generates previews in the canvas for each provider it discovers.
@available(iOS 13.0, OSX 10.15, tvOS 13.0, watchOS 6.0, *)
public protocol PreviewProvider : _PreviewProvider
```

## Example:

```
import UIViewPreview

#if canImport(SwiftUI) && DEBUG
import SwiftUI
@available(iOS 13.0, *)
struct Label_Preview: PreviewProvider {
    static var previews: some View {
        UIViewPreview {
            let label = UILabel()
            label.frame = CGRect(origin: .zero,
                                 size: CGSize(width: 100, height: 100))
            label.text = "Text previewed in SwiftUI Preview"
            return label
        }
    }
}
#endif
```

![Sample](assets/screenshot.png)


## LICENSE
https://unlicense.org
