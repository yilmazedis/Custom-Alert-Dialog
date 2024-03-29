# Custom-Alert-Dialog

Custom view as you desire, then pass it through showAlertDialog.

```swift
//
//  ViewController.swift
//  CustomAlertDialog
//
//  Created by Yilmaz Edis on 2022/4/9.
//

import UIKit
import WebKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
    }

    @IBAction func showAlertDialog(_ sender: UIButton) {


        let webView = WKWebView()
        //webView.autoresizingMask = [.flexibleWidth, .flexibleHeight]
        let url = URL(string: "https://www.google.com")!
        webView.load(URLRequest(url: url))
        webView.allowsBackForwardNavigationGestures = true

        showAlertDialog(text: "Custom Alert Dialog", view: webView)
    }
    
    /*func showAlertDialog(_ sender: UIButton) {

        let subView = UIView()

        let imageView = UIImageView(frame: subView.bounds)
        imageView.image = UIImage(named: "batman")
        imageView.autoresizingMask = [.flexibleHeight, .flexibleWidth]
        subView.addSubview(imageView)

        showAlertDialogView(text: "Custom Alert Dialog", view: subView)
    }*/

    func showAlertDialog(text: String,
                       view: UIView) {

        let showAlert = UIAlertController(title: text, message: nil, preferredStyle: .alert)

        view.translatesAutoresizingMaskIntoConstraints = false

        let webViewConstraints = [
            view.topAnchor.constraint(equalTo: showAlert.view.topAnchor, constant: 50),
            view.leadingAnchor.constraint(equalTo: showAlert.view.leadingAnchor, constant: 20),
            view.trailingAnchor.constraint(equalTo: showAlert.view.trailingAnchor, constant: -20),
            view.bottomAnchor.constraint(equalTo: showAlert.view.bottomAnchor, constant: -45),
            view.heightAnchor.constraint(equalToConstant: 480),
            view.widthAnchor.constraint(equalToConstant: 250)
        ]

        showAlert.view.addSubview(view)
        showAlert.view.addConstraints(webViewConstraints)

        showAlert.addAction(UIAlertAction(title: "OK", style: .default, handler: { action in
            // your actions here...
        }))
        showAlert.addAction(UIAlertAction(title: "Cancel", style: .default, handler: { action in
            // your actions here...
        }))
        self.present(showAlert, animated: true, completion: nil)
    }
}
```
Appearance         
:-------------------------:
<img src="example.png" height="800">

