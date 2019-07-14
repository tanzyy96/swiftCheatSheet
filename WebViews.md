# WebViews

### 1. Creating a WebView
WKWebView allows us to load web content as well as access HTML!  
Important things:
1. var webView: WKWebView!
2. loadView()
```swift
import UIKit
import WebKit

class DetailViewController: UIViewController {
    var webView: WKWebView!
    var detailItem: Petition?

    override func viewDidLoad() {
        super.viewDidLoad()
        
        guard  let detailItem = detailItem else {return}
        
        title = "SIGNATURES: \(detailItem.signatureCount)"
        
        let html = """
        <html>
        <head>
        <meta name="viewport" content="width=device-width, initial-scale-1">
        <style> body {font-size: 150%; } </style>
        </head>
        <body>
        \(detailItem.body)
        </body>
        </html>
        """
        
        webView.loadHTMLString(html, baseURL: nil)
    }
    
    override func loadView() {
        webView = WKWebView()
        view = webView
    }

}
```
If you want to load web page:
```swift
webView.load(URLRequest(url: myUrl!))
```
Here, myUrl is obviously my own url string.
