# SensingSelf Urine Reader IOS SDK

# Get Started
​
The Reader SDK for iOS is the easiest way to integrate your iOS app with SensingSelf Test Kit.
​
## Before you Start
​
This procedure assumes you are using the latest version of iOS and Xcode.
​
​
## Request SensingSelf API client key. 
 
Contact contact@sensingself.me.
​
## Step 1: Set Up Your Development Environment
​
- Download the latest Reader SDK from https://github.com/sensingself/SensingSelf-Urine-Reader-IOS-SDK
- Unzip the Reader SDK
- Drag Reader.xcframework to your project.
- Check “Copy items if needed”.
- Click on “Finish”.
 
## Step 2: Configure Your Project
 
In the project settings > General > Framework, Libraries, and Embedded Content:
Choose “Embed & Sign” for Reader.xcframework
 
## Step 3: Set Up Reader Client
 
Import Reader header and initialize ReaderManager with client key & secret.
 
```
Import Reader
 
class ViewController: UIViewController {
 
override func viewDidLoad() {
    super.viewDidLoad()
    // Do any additional setup after loading the view.
    
    ReaderManager.shared.setApiClient(key: "test_apikey1234", secret: "test_secret")
}
}
 
```
​
## Step 3: Connect The App Delegate
 
​Add the following code to your ViewController
 
```
class ViewController: UIViewController, ReaderResultDelegate {
    …
 
	   override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        ReaderManager.shared.setApiClient(key: "test_apikey1234", secret: "test_secret")
        ReaderManager.shared.delegate = self
        // test api 
ReaderManager.shared.analyzeTestKitImage("https://i.ytimg.com/vi/bE31y5HbukA/maxresdefault.jpg")
    }
 
	
   // MARK: - ReaderResultDelegate
    
    func didFindTestStripImage(result:[String, Any]) {
        print("found test strip")
    }
    
    func didFailedToFindTestStripImage(code: String, message: String) {
        print("unable to find test strip")
    }
    
    func didFinishAnalyzingTestStripImage(result:[String, Any]) {
        print("found color blocks")
    }
    
    func didFailedToAnalyzeTestStripImage(code: String, message: String) {
        print("unable to find any color blocks")
    }
}
```
 
​
## Step 4: Build and then run your project in the Simulator
​
In Xcode, select an iOS simulator and click Run. Xcode builds your project and then launches the most recent version of your app running in Simulator.
​
## Step 5: See the Results in Log Output
​
The result should look something like this:
```
{
  "resultId": "C0ACBCF9-D33D-49D6-8C5D-6D027288B815",
  "date": 1613672634,
  "colors": [...],
  "markers": 12,
  "result":
  {"NIT":{"key":0,"value":10},"LEU":{"key":3,"value":101.06000635325},"SG":{"key":6,"value":1.03},"PH":{"key":1,"value":5.5274953043384},"ASC":{"key":4,"value":5},"CA":{"key":0,"value":1},"BLD":{"key":3,"value":50.599326804786},"URO":{"key":0,"value":3.3},"BIL":{"key":0,"value":0},"KET":{"key":3,"value":5.0616185543845},"CRE":{"key":0,"value":0.9},"PRO":{"key":5,"value":20},"ALB":{"key":0,"value":10},"GLU":{"key":0,"value":0}}
}
```

## LICENSE

See the [LICENSE](LICENSE) file.

 
​
