# Runes #

Indecipherable symbols that some people claim have actual meaning.

## Installation ##

Note that as of Runes 1.2, [pre-built binaries][releases] will assume Swift
1.2. Runes 1.1.1 is considered stable for long-term use, and `master` is 100%
source compatible with Swift 1.1.

[releases]: https://github.com/thoughtbot/Runes/releases

### [Carthage] ###

[Carthage]: https://github.com/Carthage/Carthage

```
github "thoughtbot/runes"
```

Then run `carthage update`.

Follow the current instructions in [Carthage's README][carthage-installation]
for up to date installation instructions.

[carthage-installation]: https://github.com/Carthage/Carthage#adding-frameworks-to-an-application

### [CocoaPods] ###

[CocoaPods]: http://cocoapods.org

Add the following to your [Podfile](http://guides.cocoapods.org/using/the-podfile.html):

```ruby
pod 'Runes'
```

You will also need to make sure you're opting into using frameworks:

```ruby
use_frameworks!
```

Then run `pod install` with CocoaPods 0.36 or newer.

## What's included? ##

Importing Runes introduces 3 new operators and one global function:

- `<^>` (pronounced "map")
- `<*>` (pronounced "apply")
- `>>-` (pronounced "flatMap") (left associative)
- `-<<` (pronounced "flatMap") (right associative)
- `pure` (pronounced "pure")

We also include default implementations for Optional and Array with the
following type signatures:

```swift
// Optional:
public func <^><T, U>(f: T -> U, a: T?) -> U?
public func <*><T, U>(f: (T -> U)?, a: T?) -> U?
public func >>-<T, U>(a: T?, f: T -> U?) -> U?
public func -<<<T, U>(f: T -> U?, a: T?) -> U?
public func pure<T>(a: T) -> T?

// Array:
public func <^><T, U>(f: T -> U, a: [T]) -> [U]
public func <*><T, U>(fs: [T -> U], a: [T]) -> [U]
public func >>-<T, U>(a: [T], f: T -> [U]) -> [U]
public func -<<<T, U>(f: T -> [U], a: [T]) -> [U]
public func pure<T>(a: T) -> [T]
```
