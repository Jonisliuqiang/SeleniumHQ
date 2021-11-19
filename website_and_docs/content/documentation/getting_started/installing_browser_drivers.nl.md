---
title: "Installing browser drivers"
linkTitle: "Installing browser drivers"
weight: 2
description: >
  Setting up your browser to be automated.
aliases: 
        [
          "/documentation/nl/selenium_installation/installing_webdriver_binaries/",
          "/documentation/nl/webdriver/driver_requirements/"
        ]
---

{{% pageinfo color="warning" %}}
<p class="lead">
   <i class="fas fa-language display-4"></i> 
   Page being translated from 
   English to Dutch. Do you speak Dutch? Help us to translate
   it by sending us pull requests!
</p>
{{% /pageinfo %}}

Through WebDriver, Selenium supports all major browsers on the market
such as Chrom(ium), Firefox, Internet Explorer, Edge, Opera, and Safari.
Where possible, WebDriver drives the browser
using the browser's built-in support for automation,
although not all browsers have official support for remote control.

WebDriver's aim is to emulate a real user's interaction
with the browser as closely as possible.
This is possible at varying levels in different browsers.

Even though all the drivers share a single user-facing interface
for controlling the browser,
they have slightly different ways of setting up browser sessions.
Since many of the driver implementations are provided by third parties,
they are not included in the standard Selenium distribution.

Driver instantiation, profile management, and various browser specific settings
are examples of parameters that have different requirements depending on the browser.
This section explains the basic requirements
for getting you started with the different browsers.

### Adding Executables to your `PATH`
Most drivers require an extra executable for Selenium to communicate
with the browser. You can manually specify where the executable lives
before starting WebDriver, but this can make your tests less portable,
as the executables will need to be in the same place on every machine,
or included within your test code repository.

By adding a folder containing WebDriver's binaries to your system's
path, Selenium will be able to locate the additional binaries without
requiring your test code to locate the exact location of the driver.

* Create a directory to place the executables in, like 
_C:\WebDriver\bin_ or _/opt/WebDriver/bin_
* Add the directory to your PATH:
  * On Windows - Open a command prompt as administrator
     and the run the following command
     to permanently add the directory to your path
     for all users on your machine:

```shell
setx PATH "%PATH%;C:\WebDriver\bin"
```
  * Bash users on macOS and Linux - In a terminal:

```shell
export PATH=$PATH:/opt/WebDriver/bin >> ~/.profile
```

* You are now ready to test your changes.
  Close all open command prompts and open a new one.
  Type out the name of one of the binaries
  in the folder you created in the previous step,
  e.g: 

  ```shell
  chromedriver
  ```
* If your `PATH` is configured correctly,
you will see some output relating to the startup of the driver:

```text
Starting ChromeDriver 2.25.426935 (820a95b0b81d33e42712f9198c215f703412e1a1) on port 9515
Only local connections are allowed.
```

You can regain control of your command prompt by pressing <kbd>Ctrl + C</kbd>


### Quick reference

| Browser | Supported OS | Maintained by | Download | Issue Tracker |
| ------- | ------------ | ------------- | -------- | ------------- |
| Chromium/Chrome | Windows/macOS/Linux | Google | [Downloads](//chromedriver.storage.googleapis.com/index.html) | [Issues](//bugs.chromium.org/p/chromedriver/issues/list) |
| Firefox | Windows/macOS/Linux | Mozilla | [Downloads](//github.com/mozilla/geckodriver/releases) | [Issues](//github.com/mozilla/geckodriver/issues) |
| Edge | Windows 10 | Microsoft | [Downloads](//developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) | [Issues](//developer.microsoft.com/en-us/microsoft-edge/platform/issues/?page=1&amp;q=webdriver) |
| Internet Explorer | Windows | Selenium Project | [Downloads](/downloads) | [Issues](//github.com/SeleniumHQ/selenium/labels/D-IE) |
| Safari | macOS El Capitan and newer | Apple | Built in | [Issues](//bugreport.apple.com/logon) |
| Opera | Windows/macOS/Linux | Opera | [Downloads](//github.com/operasoftware/operachromiumdriver/releases) | [Issues](//github.com/operasoftware/operachromiumdriver/issues) |


### Chromium/Chrome

To drive Chrome or Chromium, you have to download
[chromedriver](//sites.google.com/a/chromium.org/chromedriver/downloads)
and put it in a folder that is on your system's path.

On Linux or macOS, this means modifying
the `PATH` environmental variable.
You can see what directories, separated by a colon,
make up your system's path by executing the following command:

```shell
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

To include chromedriver on the path if it isn't already,
make sure you include the chromedriver binary's parent directory.
The following line will set the `PATH` environmental variable
its current content, plus an additional path added after the colon:

```shell
$ export PATH="$PATH:/path/to/chromedriver"
```

When chromedriver is available on your path,
you should be able to execute the _chromedriver_ executable from any directory.

To instantiate a Chrome/Chromium session, you can do the following:

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

WebDriver driver = new ChromeDriver();
  {{< /tab >}}
  {{< tab header="Python" >}}
#Simple assignment
from selenium.webdriver import Chrome

driver = Chrome()

#Or use the context manager
from selenium.webdriver import Chrome

with Chrome() as driver:
    #your code inside this indent
  {{< /tab >}}
  {{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;

IWebDriver driver = new ChromeDriver();
  {{< /tab >}}
  {{< tab header="Ruby" >}}
require "selenium-webdriver"

driver = Selenium::WebDriver.for :chrome
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder} = require('selenium-webdriver');

(async function myFunction() {
    let driver = await new Builder().forBrowser('chrome').build();
    //your code inside this block
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
import org.openqa.selenium.WebDriver
import org.openqa.selenium.chrome.ChromeDriver

val driver: WebDriver = ChromeDriver()
  {{< /tab >}}
{{< /tabpane >}}

Remember that you have to set the path to the chromedriver executable.
This is possible using the following line:

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
System.setProperty("webdriver.chrome.driver", "/path/to/chromedriver");
  {{< /tab >}}
  {{< tab header="Python" >}}
Chrome(executable_path='/path/to/chromedriver')
  {{< /tab >}}
  {{< tab header="CSharp" >}}
new ChromeDriver("/path/to/chromedriver");
  {{< /tab >}}
  {{< tab header="Ruby" >}}
Selenium::WebDriver::Chrome.driver_path = "/path/to/chromedriver"
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
chrome.setDefaultService(new chrome.ServiceBuilder('path/to/chromedriver').build());
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
System.setProperty("webdriver.chrome.driver", "/path/to/chromedriver")
  {{< /tab >}}
{{< /tabpane >}}

The chromedriver is implemented as a WebDriver remote server
that by exposing Chrome's internal automation proxy interface
instructs the browser what to do.


### Firefox

Starting with Selenium 3, Mozilla has taken over implementation of
Firefox Driver, with [geckodriver](//github.com/mozilla/geckodriver).
The new driver for Firefox is called geckodriver and works with Firefox
48 and newer. Since the Firefox WebDriver is under development, the
newer the Firefox version the better the support.

As geckodriver is the new default way of launching Firefox, you can
instantiate Firefox in the same way as Selenium 2:

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;

WebDriver driver = new FirefoxDriver();
  {{< /tab >}}
  {{< tab header="Python" >}}
#Simple assignment
from selenium.webdriver import Firefox

driver = Firefox()
#Or use the context manager
from selenium.webdriver import Firefox

with Firefox() as driver:
   #your code inside this indent
  {{< /tab >}}
  {{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.Firefox;

IWebDriver driver = new FirefoxDriver();
  {{< /tab >}}
  {{< tab header="Ruby" >}}
require "selenium-webdriver"

driver = Selenium::WebDriver.for :firefox
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder} = require('selenium-webdriver');

(async function myFunction() {
   let driver = await new Builder().forBrowser('firefox').build();
   //your code inside this block
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
import org.openqa.selenium.WebDriver
import org.openqa.selenium.Firefox.FirefoxDriver

val driver: WebDriver = FirefoxDriver()
  {{< /tab >}}
{{< /tabpane >}}

If you prefer not to set geckodriver's location using PATH,
set the geckodriver binary location programmatically:

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
System.setProperty("webdriver.gecko.driver", "/path/to/geckodriver");
  {{< /tab >}}
  {{< tab header="Python" >}}
Firefox(executable_path='/path/to/geckodriver')
  {{< /tab >}}
  {{< tab header="CSharp" >}}
new FirefoxDriver("/path/to/geckodriver");
  {{< /tab >}}
  {{< tab header="Ruby" >}}
Selenium::WebDriver::Firefox.driver_path = "/path/to/geckodriver"
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const firefox = require('selenium-webdriver/firefox');

const serviceBuilder = new firefox.ServiceBuilder("/path/to/geckodriver");

(async function myFunction() {
    let driver = await new Builder()
        .forBrowser('firefox')
        .setFirefoxService(serviceBuilder)
        .build();
        //your code inside this block
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
System.setProperty("webdriver.gecko.driver", "/path/to/geckodriver")
  {{< /tab >}}
{{< /tabpane >}}

It is also possible to set the property at run time:

```shell
mvn test -Dwebdriver.gecko.driver=/path/to/geckodriver
```

It is currently possible to revert to the older, more feature complete
Firefox driver, by installing Firefox [47.0.1](//ftp.mozilla.org/pub/firefox/releases/47.0.1/)
or [45 ESR](//ftp.mozilla.org/pub/firefox/releases/45.0esr/)
and specifying a desired capability of **marionette** as
**false**. Later releases of Firefox are no longer compatible.


### Edge

Edge is Microsoft's newest browser, included with Windows 10 and Server 2016.
Updates to Edge are bundled with major Windows updates,
so you'll need to download a binary which matches the build number of your 
currently installed build of Windows.
The [Edge Developer site](//developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/)
contains links to all the available binaries. Bugs against the EdgeDriver 
implementation can be raised with 
[Microsoft](//developer.microsoft.com/en-us/microsoft-edge/platform/issues/?page=1&q=webdriver). 
If you'd like to run tests against Edge, but aren't running Windows 10, Microsoft
offer free VMs for testers on the [Edge Developer site](//developer.microsoft.com/en-us/microsoft-edge/tools/vms/).

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.edge.EdgeDriver;

WebDriver driver = new EdgeDriver();
  {{< /tab >}}
  {{< tab header="Python" >}}
#Simple assignment
from selenium.webdriver import Edge

driver = Edge()
#Or use the context manager
from selenium.webdriver import Edge

with Edge() as driver:
   #your code inside this indent
  {{< /tab >}}
  {{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;

IWebDriver driver = new EdgeDriver();
  {{< /tab >}}
  {{< tab header="Ruby" >}}
require "selenium-webdriver"

driver = Selenium::WebDriver.for :edge
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder} = require('selenium-webdriver');

(async function myFunction() {
   let driver = await new Builder().forBrowser('MicrosoftEdge').build();
   //your code inside this block
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
import org.openqa.selenium.WebDriver
import org.openqa.selenium.edge.EdgeDriver

val driver: WebDriver = EdgeDriver()
  {{< /tab >}}
{{< /tabpane >}}

If Edge driver is not present in your path, you can set the path using 
the following line:

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
System.setProperty("webdriver.edge.driver", "C:/path/to/MicrosoftWebDriver.exe");
  {{< /tab >}}
  {{< tab header="Python" >}}
Edge(executable_path='/path/to/MicrosoftWebDriver.exe')
  {{< /tab >}}
  {{< tab header="CSharp" >}}
new EdgeDriver("/path/to/MicrosoftWebDriver.exe");
  {{< /tab >}}
  {{< tab header="Ruby" >}}
Selenium::WebDriver::Edge.driver_path = "C:/path/to/MicrosoftWebDriver.exe"
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder} = require("selenium-webdriver");
const edge = require('selenium-webdriver/edge');
let service = new edge.ServiceBuilder("/path/to/msedgedriver.exe");
(async function test() {
    let driver = await new Builder()
                .setEdgeService(service)
                .forBrowser('MicrosoftEdge')
                .build();
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
System.setProperty("webdriver.edge.driver", "C:/path/to/MicrosoftWebDriver.exe")
  {{< /tab >}}
{{< /tabpane >}}

### Internet Explorer
Internet Explorer was Microsoft's default browser until Windows 10, although it 
is still included in Windows 10. Internet Explorer Driver is the only driver 
The Selenium project aims to support the same releases
[Microsoft considers current](//support.microsoft.com/en-gb/help/17454/lifecycle-support-policy-faq-internet-explorer).
Older releases may work, but will be unsupported. 

While the Selenium project provides binaries for both the 32-bit and 64-bit 
versions of Internet Explorer, there are some 
[limitations](//jimevansmusic.blogspot.co.uk/2014/09/screenshots-sendkeys-and-sixty-four.html)
with Internet Explorer 10 & 11 with the 64-bit driver, but using the 32-bit 
driver continues to work well. It should be noted that as Internet Explorer
preferences are saved against the logged in user's account, some 
[additional setup is required](//github.com/SeleniumHQ/selenium/wiki/InternetExplorerDriver#required-configuration).

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.ie.InternetExplorerDriver;

WebDriver driver = new InternetExplorerDriver();
  {{< /tab >}}
  {{< tab header="Python" >}}
#Simple assignment
from selenium.webdriver import Ie

driver = Ie()
#Or use the context manager
from selenium.webdriver import Ie

with Ie() as driver:
   #your code inside this indent
  {{< /tab >}}
  {{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.IE;

IWebDriver driver = new InternetExplorerDriver();
  {{< /tab >}}
  {{< tab header="Ruby" >}}
require "selenium-webdriver"

driver = Selenium::WebDriver.for :internet_explorer
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder} = require('selenium-webdriver');

(async function myFunction() {
   let driver = await new Builder().forBrowser('internet explorer').build();
   //your code inside this block
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
import org.openqa.selenium.WebDriver
import org.openqa.selenium.ie.InternetExplorerDriver

val driver: WebDriver = InternetExplorerDriver()
  {{< /tab >}}
{{< /tabpane >}}

If Internet Explorer driver is not present in your path, you can set the path 
using the following line:

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
System.setProperty("webdriver.ie.driver", "C:/path/to/IEDriver.exe");
  {{< /tab >}}
  {{< tab header="Python" >}}
Ie(executable_path='/path/to/IEDriverServer.exe')
  {{< /tab >}}
  {{< tab header="CSharp" >}}
new InternetExplorerDriver("/path/to/geckodriver");
  {{< /tab >}}
  {{< tab header="Ruby" >}}
Selenium::WebDriver::IE.driver_path = "C:\path\to\IEDriver.exe"
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder} = require("selenium-webdriver");
const ie = require('selenium-webdriver/ie');
let service = new ie.ServiceBuilder("/path/to/IEDriverServer.exe");
(async function test() {
    let driver = await new Builder()
                .setIeService(service)
                .forBrowser('internet explorer')
                .build();
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
System.setProperty("webdriver.ie.driver", "C:/path/to/IEDriver.exe")
  {{< /tab >}}
{{< /tabpane >}}

Microsoft also offer a WebDriver binary for
[Internet Explorer 11 on Windows 7 & 8.1](//www.microsoft.com/en-gb/download/details.aspx?id=44069). 
It has not been updated since 2014 and is based of a draft version of the 
W3 specification. [Jim Evans](//jimevansmusic.blogspot.co.uk/2014/09/using-internet-explorer-webdriver.html)
has an excellent writeup on Microsoft's implementation.


### Opera

Current releases of Opera are built on top of the Chromium engine,
and WebDriver is now supported via the closed-source
[Opera Chromium Driver](//github.com/operasoftware/operachromiumdriver/releases),
which can be [added to your PATH](#adding-executables-to-your-path) or as a 
system property.

Instantiating a driver session is similar to Firefox and Chromium:

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.opera.OperaDriver;

WebDriver driver = new OperaDriver();
  {{< /tab >}}
  {{< tab header="Python" >}}
#Simple assignment
from selenium.webdriver import Opera

driver = Opera()
#Or use the context manager
from selenium.webdriver import Opera

with Opera() as driver:
   #your code inside this indent
  {{< /tab >}}
  {{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.Opera;

IWebDriver driver = new OperaDriver();
  {{< /tab >}}
  {{< tab header="Ruby" >}}
require "selenium-webdriver"

driver = Selenium::WebDriver.for :opera
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder} = require("selenium-webdriver");
const opera = require('selenium-webdriver/opera');
(async function test() {
    let driver = await new Builder()
        .forBrowser('opera')
        .build();
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
import org.openqa.selenium.WebDriver
import org.openqa.selenium.opera.OperaDriver

val driver: WebDriver = OperaDriver()
  {{< /tab >}}
{{< /tabpane >}}

### Safari

High Sierra and later:
* Run the following command from the terminal for the first
time and type your password at the prompt to authorise WebDriver
```shell
safaridriver --enable
```

El Capitan and Sierra:

* Enable the Developer menu from Safari preferences
* Check the _Allow Remote Automation_ option from with 
the Develop menu
* Run the following command from the terminal for the first
time and type your password at the prompt to authorise WebDriver

```shell
/usr/bin/safaridriver -p 1337</
```

You can then start a driver session using:

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.safari.SafariDriver;

WebDriver driver = new SafariDriver();
  {{< /tab >}}
  {{< tab header="Python" >}}
#Simple assignment
from selenium.webdriver import Safari

driver = Safari()
#Or use the context manager
from selenium.webdriver import Safari

with Safari() as driver:
   #your code inside this indent
  {{< /tab >}}
  {{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.Safari;

IWebDriver driver = new SafariDriver();
  {{< /tab >}}
  {{< tab header="Ruby" >}}
require "selenium-webdriver"

driver = Selenium::WebDriver.for :safari
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder} = require('selenium-webdriver');

(async function myFunction() {
   let driver = await new Builder().forBrowser('safari').build();
   //your code inside this block
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
import org.openqa.selenium.WebDriver
import org.openqa.selenium.safari.SafariDriver

val driver: WebDriver = SafariDriver()
  {{< /tab >}}
{{< /tabpane >}}


Those looking to automate Safari on iOS should look to the 
[Appium project](//appium.io/). Whilst Safari was previously
available for Windows, Apple has long since dropped support, making it
a poor choice of test platform.


## Mock browsers


### HtmlUnit

HtmlUnit is a "GUI-Less browser for Java programs". It models HTML documents 
and provides an API that allows you to invoke pages, fill out forms, click
links, etc. It has JavaScript support and is able to work with AJAX libraries,
simulating Chrome, Firefox or Internet Explorer depending on the configuration
used. It has been moved to a 
[new location](http://htmlunit.sourceforge.net/gettingStarted.html). 
The source is maintained on svn.


### PhantomJS

PhantomJS is a headless browser based on Webkit, albeit a version much older 
than that used by Google Chrome or Safari. Whilst historically a popular 
choice, it would now be wise to avoid PhantomJS. The project has been 
unmaintained 
[since the 5th of August](//groups.google.com/forum/#!topic/phantomjs/9aI5d-LDuNE), 
so whilst the web will continue to change, PhantomJS will not be updated. 
This was after Google announced the ability to run Chrome headlessly, 
something also now offered by Mozilla's Firefox.

