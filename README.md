# Highlightr

Highlightr is an iOS & macOS syntax highlighter built with Swift. It uses [highlight.js](https://highlightjs.org/) as it core, supports [185 languages and comes with 89 styles](https://highlightjs.org/static/demo/).

Takes your lame string with code and returns a NSAttributtedString with proper syntax highlighting.

![Sample Gif A](https://raw.githubusercontent.com/raspu/Highlightr/master/mix2.gif)
![Sample Gif B](https://raw.githubusercontent.com/raspu/Highlightr/master/coding.gif)

## Installation
### Requirements
- iOS 8.0+
- macOS 10.10+

### SPM
1. Click the **File** menu, select **Add Packages…**
1. Enter `https://github.com/raspu/Highlightr/` into the *Search or Enter Package URL* search field
1. Link **Highlightr** to your application target

Finally, add `import MarkdownUI` to your source code.
 
### CocoaPods & Carthage
CocoaPods & Carthage are no longer supported.

## Usage
Highlightr provides two main classes:

### Highlightr
This is the main endpoint, you can use it to convert code strings into NSAttributed strings.
```Swift
	let highlightr = Highlightr()
	highlightr.setTheme(to: "paraiso-dark")
	let code = "let a = 1"
	// You can omit the second parameter to use automatic language detection.
	let highlightedCode = highlightr.highlight(code, as: "swift") 
	
```
### CodeAttributedString
A subclass of NSTextStorage, you can use it to highlight text on real time.
```Swift
	let textStorage = CodeAttributedString()
	textStorage.language = "Swift"
	let layoutManager = NSLayoutManager()
	textStorage.addLayoutManager(layoutManager)

	let textContainer = NSTextContainer(size: view.bounds.size)
	layoutManager.addTextContainer(textContainer)

	let textView = UITextView(frame: yourFrame, textContainer: textContainer)
```

## JavaScript?

Yes, Highlightr relies on iOS & macOS [JavaScriptCore](https://developer.apple.com/library/ios/documentation/Carbon/Reference/WebKit_JavaScriptCore_Ref/index.html#//apple_ref/doc/uid/TP40004754) to parse the code using highlight.js. This is actually quite fast!

## Performance

It will never be as fast as a native solution, but it's fast enough to be used on a real time editor.

It comes with a custom made HTML parser for creating NSAttributtedStrings, is pre-processing the themes and is preloading the JS libraries. As result it's taking around of 50 ms on my iPhone 6s for processing 500 lines of code.

## Documentation

You can find the documentation for the latest release on [cocoadocs](http://cocoadocs.org/docsets/Highlightr/).

## License

Highlightr is available under the MIT license. See the LICENSE file for more info.

Highlight.js is available under the BSD license. You can find the [license file here](https://github.com/isagalaev/highlight.js/blob/master/LICENSE).
