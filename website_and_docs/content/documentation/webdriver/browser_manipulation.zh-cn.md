---
title: "操控浏览器"
linkTitle: "操控浏览器"
weight: 2
aliases: ["/documentation/zh-cn/webdriver/browser_manipulation/"]
---


## Ruby

默认情况下，Ruby 没有安装在 Windows 上。下载最新[版本](//rubyinstaller.org/downloads)
并运行安装程序。你可以保留所有设置的默认值，除要勾选 _安装位置和可选任务_ 屏幕上
_将 Ruby 可执行程序添加到您的系统路径_ 复选框外。想要驱动任何浏览器，你必须安装 `selenium-webdriver`
Ruby gem. 打开命令提示符并输入以下命令来安装它:

```shell
gem install selenium-webdriver
```

如果你使用 [Bundler](//bundler.io)，添加这一行到你的应用程序的 Gemfile 中:

```ruby
gem "selenium-webdriver"
```

然后在命令提示符中执行以下命令：

```shell
bundle install
```


## Internet Explorer

IE 浏览器默认安装在 Windows 上，不需要再次安装。要在 Windows 上驱动 IE，您必须下载最新的
[Internet Explorer 驱动程序](https://selenium.dev/downloads/) 并将文件放入 `PATH`
路径中的文件夹中。要查看 `PATH` 路径中的目录，在命令提示符中键入 `echo %PATH%`。

```bat
$ echo %PATH%
C:\Ruby200\bin;C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem
```

`C:\Ruby200\bin` 看起来是个不错的位置。解压 IEDriverServer 文件并将 IEDriverServer.exe 移动进去。

这将打开一个新的 IE 浏览器窗口:

```ruby
require "selenium-webdriver"
driver = Selenium::WebDriver.for :internet_explorer
```

## 浏览器导航

### 打开网站

启动浏览器后你要做的第一件事就是打开你的网站。这可以通过一行代码实现:

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 简便的方法
driver.get("https://selenium.dev");

// 更长的方法
driver.navigate().to("https://selenium.dev");
{{< /tab >}}
{{< tab header="Python" >}}
driver.get("https://selenium.dev")
{{< /tab >}}
{{< tab header="CSharp" >}}
driver.Navigate().GoToUrl(@"https://selenium.dev");
{{< /tab >}}
{{< tab header="Ruby" >}}
# 简便的方法
driver.get 'https://selenium.dev'

# 更长的方法
driver.navigate.to 'https://selenium.dev'
{{< /tab >}}
{{< tab header="JavaScript" >}}
await driver.get('https://selenium.dev');
{{< /tab >}}
{{< tab header="Kotlin" >}}
// 简便的方法
driver.get("https://selenium.dev")

// 更长的方法
driver.navigate().to("https://selenium.dev")
{{< /tab >}}
{{< /tabpane >}}

### 获取当前 URL

您可以从浏览器的地址栏读取当前的 URL，使用:

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.getCurrentUrl();{{< /tab >}}
{{< tab header="Python" >}}driver.current_url{{< /tab >}}
{{< tab header="CSharp" >}}driver.Url;{{< /tab >}}
{{< tab header="Ruby" >}}driver.current_url{{< /tab >}}
{{< tab header="JavaScript" >}}await driver.getCurrentUrl();{{< /tab >}}
{{< tab header="Kotlin" >}}driver.currentUrl{{< /tab >}}
{{< /tabpane >}}

### 后退

按下浏览器的后退按钮:

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.navigate().back();{{< /tab >}}
{{< tab header="Python" >}}driver.back(){{< /tab >}}
{{< tab header="CSharp" >}}driver.Navigate().Back();{{< /tab >}}
{{< tab header="Ruby" >}}driver.navigate.back{{< /tab >}}
{{< tab header="JavaScript" >}}await driver.navigate().back();{{< /tab >}}
{{< tab header="Kotlin" >}}driver.navigate().back() {{< /tab >}}
{{< /tabpane >}}


### 前进
按下浏览器的前进键:

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.navigate().forward();{{< /tab >}}
{{< tab header="Python" >}}driver.forward(){{< /tab >}}
{{< tab header="CSharp" >}}driver.Navigate().Forward();{{< /tab >}}
{{< tab header="Ruby" >}}driver.navigate.forward{{< /tab >}}
{{< tab header="JavaScript" >}}await driver.navigate().forward();{{< /tab >}}
{{< tab header="Kotlin" >}}driver.navigate().forward(){{< /tab >}}
{{< /tabpane >}}

### 刷新
刷新当前页面:

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.navigate().refresh();{{< /tab >}}
{{< tab header="Python" >}}driver.refresh(){{< /tab >}}
{{< tab header="CSharp" >}}driver.Navigate().Refresh();{{< /tab >}}
{{< tab header="Ruby" >}}driver.navigate.refresh{{< /tab >}}
{{< tab header="JavaScript" >}}await driver.navigate().refresh();{{< /tab >}}
{{< tab header="Kotlin" >}}driver.navigate().refresh(){{< /tab >}}
{{< /tabpane >}}

### 获取标题

从浏览器中读取当前页面的标题:

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.getTitle();{{< /tab >}}
{{< tab header="Python" >}}driver.title{{< /tab >}}
{{< tab header="CSharp" >}}driver.Title;{{< /tab >}}
{{< tab header="Ruby" >}}driver.title{{< /tab >}}
{{< tab header="JavaScript" >}}await driver.getTitle();{{< /tab >}}
{{< tab header="Kotlin" >}}driver.title{{< /tab >}}
{{< /tabpane >}}


## 窗口和标签页

WebDriver 没有区分窗口和标签页。如果你的站点打开了一个新标签页或窗口，Selenium 将允许您使用窗口句柄来处理它。
每个窗口都有一个唯一的标识符，该标识符在单个会话中保持持久性。你可以使用以下方法获得当前窗口的窗口句柄:

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.getWindowHandle();{{< /tab >}}
{{< tab header="Python" >}}driver.current_window_handle{{< /tab >}}
{{< tab header="CSharp" >}}driver.CurrentWindowHandle;{{< /tab >}}
{{< tab header="Ruby" >}}driver.window_handle{{< /tab >}}
{{< tab header="JavaScript" >}}await driver.getWindowHandle();{{< /tab >}}
{{< tab header="Kotlin" >}}driver.windowHandle{{< /tab >}}
{{< /tabpane >}}

### 切换窗口或标签页


单击在 <a href="https://seleniumhq.github.io"target="_blank">新窗口</a> 中打开链接，
则屏幕会聚焦在新窗口或新标签页上，但 WebDriver 不知道操作系统认为哪个窗口是活动的。
要使用新窗口，您需要切换到它。 如果只有两个选项卡或窗口被打开，并且你知道从哪个窗口开始，
则你可以遍历 WebDriver， 通过排除法可以看到两个窗口或选项卡，然后切换到你需要的窗口或选项卡。

不过，Selenium 4 提供了一个新的 api [NewWindow](#创建新窗口或新标签页并且切换)
它创建一个新选项卡 (或) 新窗口并自动切换到它。

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 存储原始窗口的 ID
String originalWindow = driver.getWindowHandle();

// 检查一下，我们还没有打开其他的窗口
assert driver.getWindowHandles().size() == 1;

// 点击在新窗口中打开的链接
driver.findElement(By.linkText("new window")).click();

// 等待新窗口或标签页
wait.until(numberOfWindowsToBe(2));

// 循环执行，直到找到一个新的窗口句柄
for (String windowHandle : driver.getWindowHandles()) {if(!originalWindow.contentEquals(windowHandle)) {driver.switchTo().window(windowHandle);
break;
}
}

// 等待新标签完成加载内容
wait.until(titleIs("Selenium documentation"));
{{< /tab >}}
{{< tab header="Python" >}}
from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# 启动驱动程序
with webdriver.Firefox() as driver:
# 打开网址
driver.get("https://seleniumhq.github.io")

    # 设置等待
    wait = WebDriverWait(driver, 10)

    # 存储原始窗口的 ID
    original_window = driver.current_window_handle

    # 检查一下，我们还没有打开其他的窗口
    assert len(driver.window_handles) == 1

    # 单击在新窗口中打开的链接
    driver.find_element(By.LINK_TEXT, "new window").click()

    # 等待新窗口或标签页
    wait.until(EC.number_of_windows_to_be(2))

    # 循环执行，直到找到一个新的窗口句柄
    for window_handle in driver.window_handles:
        if window_handle != original_window:
            driver.switch_to.window(window_handle)
            break

    # 等待新标签页完成加载内容
    wait.until(EC.title_is("SeleniumHQ Browser Automation"))
{{< /tab >}}
{{< tab header="CSharp" >}}
// 存储原始窗口的 ID
string originalWindow = driver.CurrentWindowHandle;

// 检查一下，我们还没有打开其他的窗口
Assert.AreEqual(driver.WindowHandles.Count, 1);

// 单击在新窗口中打开的链接
driver.FindElement(By.LinkText("new window")).Click();

// 等待新窗口或标签页
wait.Until(wd => wd.WindowHandles.Count == 2);

// 循环执行，直到找到一个新的窗口句柄
foreach(string window in driver.WindowHandles)
{if(originalWindow != window)
{driver.SwitchTo().Window(window);
break;
}
}
// 等待新标签页完成加载内容
wait.Until(wd => wd.Title == "Selenium documentation");
{{< /tab >}}
{{< tab header="Ruby" >}}
# 存储原始窗口的 ID
original_window = driver.window_handle

#检查一下，我们还没有打开其他的窗口
assert(driver.window_handles.length == 1,'Expected one window')

#点击在新窗口中打开的链接
driver.find_element(link:'new window').click

#等待新窗口或标签页
wait.until {driver.window_handles.length == 2}

#循环执行，直到找到一个新的窗口句柄
driver.window_handles.each do |handle|
if handle != original_window
driver.switch_to.window handle
break
end
end

#等待新标签页完成加载内容
wait.until {driver.title =='Selenium documentation'}
{{< /tab >}}
{{< tab header="JavaScript" >}}
// 存储原始窗口的 ID
const originalWindow = await driver.getWindowHandle();

// 检查一下，我们还没有打开其他的窗口
assert((await driver.getAllWindowHandles()).length === 1);

// 点击在新窗口中打开的链接
await driver.findElement(By.linkText('new window')).click();

// 等待新窗口或标签页
await driver.wait(async () => (await driver.getAllWindowHandles()).length === 2,
10000
);

// 循环执行，直到找到一个新的窗口句柄
const windows = await driver.getAllWindowHandles();
windows.forEach(async handle => {if (handle !== originalWindow) {await driver.switchTo().window(handle);
}
});

// 等待新标签页完成加载内容
await driver.wait(until.titleIs('Selenium documentation'), 10000);
{{< /tab >}}
{{< tab header="Kotlin" >}}
// 存储原始窗口的 ID
val originalWindow = driver.getWindowHandle()

// 检查一下，我们还没有打开其他的窗口
assert(driver.getWindowHandles().size() === 1)

// 点击在新窗口中打开的链接
driver.findElement(By.linkText("new window")).click()

// 等待新窗口或标签页
wait.until(numberOfWindowsToBe(2))

// 循环执行，直到找到一个新的窗口句柄
for (windowHandle in driver.getWindowHandles()) {
if (!originalWindow.contentEquals(windowHandle)) {
driver.switchTo().window(windowHandle)
break
}
}

// 等待新标签页完成加载内容
wait.until(titleIs("Selenium documentation"))

{{< /tab >}}
{{< /tabpane >}}

### 创建新窗口(或)新标签页并且切换

创建一个新窗口 (或) 标签页，屏幕焦点将聚焦在新窗口或标签在上。您不需要切换到新窗口 (或) 标签页。如果除了新窗口之外，
您打开了两个以上的窗口 (或) 标签页，您可以通过遍历 WebDriver 看到两个窗口或选项卡，并切换到非原始窗口。

_注意: 该特性适用于 Selenium 4 及其后续版本。_

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 打开新标签页并切换到新标签页
driver.switchTo().newWindow(WindowType.TAB);

// 打开一个新窗口并切换到新窗口
driver.switchTo().newWindow(WindowType.WINDOW);
{{< /tab >}}
{{< tab header="Python" >}}
# 打开新标签页并切换到新标签页
driver.switch_to.new_window('tab')

# 打开一个新窗口并切换到新窗口
driver.switch_to.new_window('window')
{{< /tab >}}
{{< tab header="CSharp" >}}
// 打开新标签页并切换到新标签页
driver.SwitchTo().NewWindow(WindowType.Tab)

// 打开一个新窗口并切换到新窗口
driver.SwitchTo().NewWindow(WindowType.Window)
{{< /tab >}}
{{< tab header="Ruby" >}}
# 注意：ruby 中的 new_window 只打开一个新标签页(或)窗口，不会自动切换
# 用户必须切换到新选项卡 (或) 新窗口

# 打开新标签页并切换到新标签页
driver.manage.new_window(:tab)

# 打开一个新窗口并切换到新窗口
driver.manage.new_window(:window)
{{< /tab >}}
{{< tab header="JavaScript" >}}
// 打开新标签页并切换到新标签页
await driver.switchTo().newWindow('tab');

// 打开一个新窗口并切换到新窗口
await driver.switchTo().newWindow('window');

{{< /tab >}}
{{< tab header="Kotlin" >}}
// 打开新标签页并切换到新标签页
driver.switchTo().newWindow(WindowType.TAB)

// 打开一个新窗口并切换到新窗口
driver.switchTo().newWindow(WindowType.WINDOW)
{{< /tab >}}
{{< /tabpane >}}

### 关闭窗口或标签页

当你完成了一个窗口或标签页的工作时，_并且_它不是浏览器中最后一个打开的窗口或标签页时，你应该关闭它并切换回你之前使用的窗口。
假设您遵循了前一节中的代码示例，您将把前一个窗口句柄存储在一个变量中。把这些放在一起，你会得到:

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
//关闭标签页或窗口
driver.close();

//切回到之前的标签页或窗口
driver.switchTo().window(originalWindow);
{{< /tab >}}
{{< tab header="Python" >}}
#关闭标签页或窗口
driver.close()

#切回到之前的标签页或窗口
driver.switch_to.window(original_window)
{{< /tab >}}
{{< tab header="CSharp" >}}
//关闭标签页或窗口
driver.Close();

//切回到之前的标签页或窗口
driver.SwitchTo().Window(originalWindow);
{{< /tab >}}
{{< tab header="Ruby" >}}
#关闭标签页或窗口
driver.close

#切回到之前的标签页或窗口
driver.switch_to.window original_window
{{< /tab >}}
{{< tab header="JavaScript" >}}
//关闭标签页或窗口
await driver.close();

//切回到之前的标签页或窗口
await driver.switchTo().window(originalWindow);
{{< /tab >}}
{{< tab header="Kotlin" >}}
//关闭标签页或窗口
driver.close()

//切回到之前的标签页或窗口
driver.switchTo().window(originalWindow)

{{< /tab >}}
{{< /tabpane >}}

如果在关闭一个窗口后忘记切换回另一个窗口句柄，WebDriver 将在当前关闭的页面上执行，并触发一个
**No Such Window Exception 无此窗口异常**。必须切换回有效的窗口句柄才能继续执行。

### 在会话结束时退出浏览器

当你完成了浏览器会话，你应该调用 quit 退出，而不是 close 关闭:
{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.quit();{{< /tab >}}
{{< tab header="Python" >}}driver.quit(){{< /tab >}}
{{< tab header="CSharp" >}}driver.Quit();{{< /tab >}}
{{< tab header="Ruby" >}}driver.quit{{< /tab >}}
{{< tab header="JavaScript" >}}await driver.quit();{{< /tab >}}
{{< tab header="Kotlin" >}}driver.quit(){{< /tab >}}
{{< /tabpane >}}

* 退出将会
  * 关闭所有与 WebDriver 会话相关的窗口和选项卡
  * 结束浏览器进程
  * 结束后台驱动进程
  * 通知 Selenium Grid 浏览器不再使用，以便可以由另一个会话使用它(如果您正在使用 Selenium Grid)

调用 quit() 失败将留下额外的后台进程和端口运行在机器上，这可能在以后导致一些问题。

有的测试框架提供了一些方法和注释，您可以在测试结束时放入 teardown() 方法中。

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
/**
* 使用 JUnit 的例子
* https://junit.org/junit5/docs/current/api/org/junit/jupiter/api/AfterAll.html
  */
  @AfterAll
  public static void tearDown() {driver.quit();
  }
  {{< /tab >}}
  {{< tab header="Python" >}}
# unittest teardown
# https://docs.python.org/3/library/unittest.html?highlight=teardown#unittest.TestCase.tearDown
def tearDown(self):
self.driver.quit()
{{< /tab >}}
{{< tab header="CSharp" >}}
/*
使用 Visual Studio 的 UnitTesting 的例子
https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.testtools.unittesting.aspx
*/
[TestCleanup]
public void TearDown()
{driver.Quit();
}
{{< /tab >}}
{{< tab header="Ruby" >}}
# UnitTest Teardown
# https://www.rubydoc.info/github/test-unit/test-unit/Test/Unit/TestCase
def teardown
@driver.quit
end
{{< /tab >}}
{{< tab header="JavaScript" >}}
/**
* 使用 Mocha 的例子
* https://mochajs.org/#hooks
  */
  after('Tear down', async function () {await driver.quit();
  });
  {{< /tab >}}
  {{< tab header="Kotlin" >}}

/**
* 使用 JUnit 的例子
* https://junit.org/junit5/docs/current/api/org/junit/jupiter/api/AfterAll.html
  */
  @AfterAll
  fun tearDown() {driver.quit()
  }
  {{< /tab >}}
  {{< /tabpane >}}

如果不在测试上下文中运行 WebDriver，您可以考虑使用 `try / finally`，这是大多数语言都提供的，
这样一个异常处理仍然可以清理 WebDriver 会话。

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
try {//WebDriver 代码…} finally {driver.quit();
}
{{< /tab >}}
{{< tab header="Python" >}}
try:
#WebDriver 代码…
finally:
driver.quit()
{{< /tab >}}
{{< tab header="CSharp" >}}
try {//WebDriver 代码…} finally {driver.Quit();
}
{{< /tab >}}
{{< tab header="Ruby" >}}
begin
#WebDriver 代码…
ensure
driver.quit
end
{{< /tab >}}
{{< tab header="JavaScript" >}}
try {//WebDriver 代码…} finally {await driver.quit();
}
{{< /tab >}}
{{< tab header="Kotlin" >}}
try {//WebDriver 代码…} finally {driver.quit()
}
{{< /tab >}}
{{< /tabpane >}}

Python 的 WebDriver 现在支持 Python 上下文管理器，当使用 with 关键字时，可以在执行结束时自动退出驱动程序。

```python
with webdriver.Firefox() as driver:
  # WebDriver 代码…

# 在此缩进位置后 WebDriver 会自动退出
```

## Frames and Iframes

框架是一种现在已被弃用的方法，用于从同一域中的多个文档构建站点布局。除非你使用的是 HTML5
之前的 webapp，否则你不太可能与他们合作。内嵌框架允许插入来自完全不同领域的文档，并且仍然经常使用。


如果您需要使用框架或 iframe, WebDriver 允许您以相同的方式使用它们。考虑 iframe 中的一个按钮。
如果我们使用浏览器开发工具检查元素，我们可能会看到以下内容:

```html
<div id="modal">
  <iframe id="buttonframe"name="myframe"src="https://seleniumhq.github.io">
   <button>Click here</button>
 </iframe>
</div>
```

如果不是 iframe，我们可能会使用如下方式点击按钮:

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 这不会工作
driver.findElement(By.tagName("button")).click();
{{< /tab >}}
{{< tab header="Python" >}}
# 这不会工作
driver.find_element(By.TAG_NAME, 'button').click()
{{< /tab >}}
{{< tab header="CSharp" >}}
// 这不会工作
driver.FindElement(By.TagName("button")).Click();
{{< /tab >}}
{{< tab header="Ruby" >}}
# 这不会工作
driver.find_element(:tag_name,'button').click
{{< /tab >}}
{{< tab header="JavaScript" >}}
// 这不会工作
await driver.findElement(By.css('button')).click();
{{< /tab >}}
{{< tab header="Kotlin" >}}
// 这不会工作
driver.findElement(By.tagName("button")).click()
{{< /tab >}}
{{< /tabpane >}}

但是，如果 iframe 之外没有按钮，那么您可能会得到一个 _no such element 无此元素_ 的错误。
这是因为 Selenium 只知道顶层文档中的元素。为了与按钮进行交互，我们需要首先切换到框架，
这与切换窗口的方式类似。WebDriver 提供了三种切换到帧的方法。

### 使用 WebElement

使用 WebElement 进行切换是最灵活的选择。您可以使用首选的选择器找到框架并切换到它。

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 存储网页元素
WebElement iframe = driver.findElement(By.cssSelector("#modal>iframe"));

// 切换到 frame
driver.switchTo().frame(iframe);

// 现在可以点击按钮
driver.findElement(By.tagName("button")).click();
{{< /tab >}}
{{< tab header="Python" >}}
# 存储网页元素
iframe = driver.find_element(By.CSS_SELECTOR, "#modal > iframe")

# 切换到选择的 iframe
driver.switch_to.frame(iframe)

# 单击按钮
driver.find_element(By.TAG_NAME, 'button').click()
{{< /tab >}}
{{< tab header="CSharp" >}}
// 存储网页元素
IWebElement iframe = driver.FindElement(By.CssSelector("#modal>iframe"));

// 切换到 frame
driver.SwitchTo().Frame(iframe);

// 现在可以点击按钮
driver.FindElement(By.TagName("button")).Click();
{{< /tab >}}
{{< tab header="Ruby" >}}
# Store iframe web element
iframe = driver.find_element(:css,'#modal> iframe')

# 切换到 frame
driver.switch_to.frame iframe

# 单击按钮
driver.find_element(:tag_name,'button').click
{{< /tab >}}
{{< tab header="JavaScript" >}}
// 存储网页元素
const iframe = driver.findElement(By.css('#modal> iframe'));

// 切换到 frame
await driver.switchTo().frame(iframe);

// 现在可以点击按钮
await driver.findElement(By.css('button')).click();
{{< /tab >}}
{{< tab header="Kotlin" >}}
// 存储网页元素
val iframe = driver.findElement(By.cssSelector("#modal>iframe"))

// 切换到 frame
driver.switchTo().frame(iframe)

// 现在可以点击按钮
driver.findElement(By.tagName("button")).click()
{{< /tab >}}
{{< /tabpane >}}

### 使用 name 或 id

如果您的 frame 或 iframe 具有 id 或 name 属性，则可以使用该属性。如果名称或 id 在页面上不是唯一的，
那么将切换到找到的第一个。

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 使用 ID
driver.switchTo().frame("buttonframe");

// 或者使用 name 代替
driver.switchTo().frame("myframe");

// 现在可以点击按钮
driver.findElement(By.tagName("button")).click();
{{< /tab >}}
{{< tab header="Python" >}}
# 通过 id 切换框架
driver.switch_to.frame('buttonframe')

# 单击按钮
driver.find_element(By.TAG_NAME, 'button').click()
{{< /tab >}}
{{< tab header="CSharp" >}}
// 使用 ID
driver.SwitchTo().Frame("buttonframe");

// 或者使用 name 代替
driver.SwitchTo().Frame("myframe");

// 现在可以点击按钮
driver.FindElement(By.TagName("button")).Click();
{{< /tab >}}
{{< tab header="Ruby" >}}
# Switch by ID
driver.switch_to.frame 'buttonframe'

# 单击按钮
driver.find_element(:tag_name,'button').click
{{< /tab >}}
{{< tab header="JavaScript" >}}
// 使用 ID
await driver.switchTo().frame('buttonframe');

// 或者使用 name 代替
await driver.switchTo().frame('myframe');

// 现在可以点击按钮
await driver.findElement(By.css('button')).click();
{{< /tab >}}
{{< tab header="Kotlin" >}}
// 使用 ID
driver.switchTo().frame("buttonframe")

// 或者使用 name 代替
driver.switchTo().frame("myframe")

// 现在可以点击按钮
driver.findElement(By.tagName("button")).click()
{{< /tab >}}
{{< /tabpane >}}

### 使用索引

还可以使用frame的索引，
例如可以使用JavaScript中的
_window.frames_ 进行查询.

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 切换到第 2 个框架
driver.switchTo().frame(1);
{{< /tab >}}
{{< tab header="Ruby" >}}
# 切换到第 2 个框架
driver.switch_to.frame(1)
{{< /tab >}}
{{< tab header="CSharp" >}}
// 切换到第 2 个框架
driver.SwitchTo().Frame(1);
{{< /tab >}}
{{< tab header="Python" >}}
# 基于索引切换到第 2 个 iframe
iframe = driver.find_elements_by_tag_name('iframe')[1]

# 切换到选择的 iframe
driver.switch_to.frame(iframe)
{{< /tab >}}
{{< tab header="JavaScript" >}}
// 切换到第 2 个框架
await driver.switchTo().frame(1);
{{< /tab >}}
{{< tab header="Kotlin" >}}
// 切换到第 2 个框架
driver.switchTo().frame(1)
{{< /tab >}}
{{< /tabpane >}}


### 离开框架

离开 iframe 或 frameset，切换回默认内容，如下所示:

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 回到顶层
driver.switchTo().defaultContent();
{{< /tab >}}
{{< tab header="Python" >}}
# 切回到默认内容
driver.switch_to.default_content()
{{< /tab >}}
{{< tab header="CSharp" >}}
// 回到顶层
driver.SwitchTo().DefaultContent();
{{< /tab >}}
{{< tab header="Ruby" >}}
# 回到顶层
driver.switch_to.default_content
{{< /tab >}}
{{< tab header="JavaScript" >}}
// 回到顶层
await driver.switchTo().defaultContent();
{{< /tab >}}
{{< tab header="Kotlin" >}}
// 回到顶层
driver.switchTo().defaultContent()
{{< /tab >}}
{{< /tabpane >}}

## 窗口管理

屏幕分辨率会影响 web 应用程序的呈现方式，因此 WebDriver 提供了移动和调整浏览器窗口大小的机制。

### 获取窗口大小
获取浏览器窗口的大小(以像素为单位)。

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 分别获取每个尺寸
int width = driver.manage().window().getSize().getWidth();
int height = driver.manage().window().getSize().getHeight();

// 或者存储尺寸并在以后查询它们
Dimension size = driver.manage().window().getSize();
int width1 = size.getWidth();
int height1 = size.getHeight();
{{< /tab >}}
{{< tab header="Python" >}}
# 分别获取每个尺寸
width = driver.get_window_size().get("width")
height = driver.get_window_size().get("height")

# 或者存储尺寸并在以后查询它们
size = driver.get_window_size()
width1 = size.get("width")
height1 = size.get("height")
{{< /tab >}}
{{< tab header="CSharp" >}}
// 分别获取每个尺寸
int width = driver.Manage().Window.Size.Width;
int height = driver.Manage().Window.Size.Height;

// 或者存储尺寸并在以后查询它们
System.Drawing.Size size = driver.Manage().Window.Size;
int width1 = size.Width;
int height1 = size.Height;
{{< /tab >}}
{{< tab header="Ruby" >}}
# 分别获取每个尺寸
width = driver.manage.window.size.width
height = driver.manage.window.size.height

# 或者存储尺寸并在以后查询它们
size = driver.manage.window.size
width1 = size.width
height1 = size.height
{{< /tab >}}
{{< tab header="JavaScript" >}}
// 分别获取每个尺寸
const {width, height} = await driver.manage().window().getRect();

// 或者存储尺寸并在以后查询它们
const rect = await driver.manage().window().getRect();
const width1 = rect.width;
const height1 = rect.height;
{{< /tab >}}
{{< tab header="Kotlin" >}}
// 分别获取每个尺寸
val width = driver.manage().window().size.width
val height = driver.manage().window().size.height

// 或者存储尺寸并在以后查询它们
val size = driver.manage().window().size
val width1 = size.width
val height1 = size.height
{{< /tab >}}
{{< /tabpane >}}

### 设置窗口大小

恢复窗口并设置窗口大小。
{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.manage().window().setSize(new Dimension(1024, 768));{{< /tab >}}
{{< tab header="Python" >}}driver.set_window_size(1024, 768){{< /tab >}}
{{< tab header="CSharp" >}}driver.Manage().Window.Size = new Size(1024, 768);{{< /tab >}}
{{< tab header="Ruby" >}}driver.manage.window.resize_to(1024,768){{< /tab >}}
{{< tab header="JavaScript" >}}await driver.manage().window().setRect({width: 1024, height: 768});{{< /tab >}}
{{< tab header="Kotlin" >}}driver.manage().window().size = Dimension(1024, 768){{< /tab >}}
{{< /tabpane >}}

### 得到窗口的位置

获取浏览器窗口左上角的坐标。

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 分别获取每个尺寸
int x = driver.manage().window().getPosition().getX();
int y = driver.manage().window().getPosition().getY();

// 或者存储尺寸并在以后查询它们
Point position = driver.manage().window().getPosition();
int x1 = position.getX();
int y1 = position.getY();
{{< /tab >}}
{{< tab header="Python" >}}
# 分别获取每个尺寸
x = driver.get_window_position().get('x')
y = driver.get_window_position().get('y')

# 或者存储尺寸并在以后查询它们
position = driver.get_window_position()
x1 = position.get('x')
y1 = position.get('y')
{{< /tab >}}
{{< tab header="CSharp" >}}
// 分别获取每个尺寸
int x = driver.Manage().Window.Position.X;
int y = driver.Manage().Window.Position.Y;

// 或者存储尺寸并在以后查询它们
Point position = driver.Manage().Window.Position;
int x1 = position.X;
int y1 = position.Y;
{{< /tab >}}
{{< tab header="Ruby" >}}
#Access each dimension individually
x = driver.manage.window.position.x
y = driver.manage.window.position.y

# Or store the dimensions and query them later
rect  = driver.manage.window.rect
x1 = rect.x
y1 = rect.y
{{< /tab >}}
{{< tab header="JavaScript" >}}
// 分别获取每个尺寸
const {x, y} = await driver.manage().window().getRect();

// 或者存储尺寸并在以后查询它们
const rect = await driver.manage().window().getRect();
const x1 = rect.x;
const y1 = rect.y;
{{< /tab >}}
{{< tab header="Kotlin" >}}
// 分别获取每个尺寸
val x = driver.manage().window().position.x
val y = driver.manage().window().position.y

// 或者存储尺寸并在以后查询它们
val position = driver.manage().window().position
val x1 = position.x
val y1 = position.y

{{< /tab >}}
{{< /tabpane >}}

## 设置窗口位置

将窗口移动到设定的位置。

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// 将窗口移动到主显示器的左上角
driver.manage().window().setPosition(new Point(0, 0));
{{< /tab >}}
{{< tab header="Python" >}}
# 将窗口移动到主显示器的左上角
driver.set_window_position(0, 0)
{{< /tab >}}
{{< tab header="CSharp" >}}
// 将窗口移动到主显示器的左上角
driver.Manage().Window.Position = new Point(0, 0);
{{< /tab >}}
{{< tab header="Ruby" >}}
driver.manage.window.move_to(0,0)
{{< /tab >}}
{{< tab header="JavaScript" >}}
// 将窗口移动到主显示器的左上角
await driver.manage().window().setRect({x: 0, y: 0});
{{< /tab >}}
{{< tab header="Kotlin" >}}
// 将窗口移动到主显示器的左上角
driver.manage().window().position = Point(0,0)
{{< /tab >}}
{{< /tabpane >}}

### 最大化窗口

扩大窗口。对于大多数操作系统，窗口将填满屏幕，而不会阻挡操作系统自己的菜单和工具栏。

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.manage().window().maximize();{{< /tab >}}
{{< tab header="Python" >}}driver.maximize_window(){{< /tab >}}
{{< tab header="CSharp" >}}driver.Manage().Window.Maximize();{{< /tab >}}
{{< tab header="Ruby" >}}driver.manage.window.maximize{{< /tab >}}
{{< tab header="JavaScript" >}}await driver.manage().window().maximize();{{< /tab >}}
{{< tab header="Kotlin" >}}driver.manage().window().maximize(){{< /tab >}}
{{< /tabpane >}}

### 最小化窗口
最小化当前浏览上下文的窗口.
这种命令的精准行为将作用于各个特定的窗口管理器.

最小化窗口通常将窗口隐藏在系统托盘中.

__注意: 此功能适用于Selenium 4以及更高版本.__

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.manage().window().minimize();{{< /tab >}}
{{< tab header="Python" >}}driver.minimize_window(){{< /tab >}}
{{< tab header="CSharp" >}}driver.Manage().Window.Minimize();{{< /tab >}}
{{< tab header="Ruby" >}}driver.manage.window.minimize{{< /tab >}}
{{< tab header="JavaScript" >}}await driver.manage().window().minimize();{{< /tab >}}
{{< tab header="Kotlin" >}}driver.manage().window().minimize(){{< /tab >}}
{{< /tabpane >}}

### 全屏窗口

填充整个屏幕，类似于在大多数浏览器中按下 F11。

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}driver.manage().window().fullscreen();{{< /tab >}}
{{< tab header="Python" >}}driver.fullscreen_window(){{< /tab >}}
{{< tab header="CSharp" >}}driver.Manage().Window.FullScreen();{{< /tab >}}
{{< tab header="Ruby" >}}driver.manage.window.full_screen{{< /tab >}}
{{< tab header="JavaScript" >}}await driver.manage().window().fullscreen();{{< /tab >}}
{{< tab header="Kotlin" >}}driver.manage().window().fullscreen(){{< /tab >}}
{{< /tabpane >}}

### 屏幕截图

用于捕获当前浏览上下文的屏幕截图.
WebDriver端点
[屏幕截图](https://www.w3.org/TR/webdriver/#dfn-take-screenshot)
返回以Base64格式编码的屏幕截图.

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
import org.apache.commons.io.FileUtils;
import org.openqa.selenium.chrome.ChromeDriver;
import java.io.*;
import org.openqa.selenium.*;

public class SeleniumTakeScreenshot {
public static void main(String args[]) throws IOException {
WebDriver driver = new ChromeDriver();
driver.get("http://www.example.com");
File scrFile = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
FileUtils.copyFile(scrFile, new File("./image.png"));
driver.quit();
}
}
{{< /tab >}}
{{< tab header="Python" >}}
from selenium import webdriver

driver = webdriver.Chrome()

# Navigate to url
driver.get("http://www.example.com")

# Returns and base64 encoded string into image
driver.save_screenshot('./image.png')

driver.quit()
{{< /tab >}}
{{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;
using OpenQA.Selenium.Support.UI;

    var driver = new ChromeDriver();
    driver.Navigate().GoToUrl("http://www.example.com");
    Screenshot screenshot = (driver as ITakesScreenshot).GetScreenshot();
    screenshot.SaveAsFile("screenshot.png", ScreenshotImageFormat.Png); // Format values are Bmp, Gif, Jpeg, Png, Tiff
{{< /tab >}}
{{< tab header="Ruby" >}}
require 'selenium-webdriver'
driver = Selenium::WebDriver.for :chrome

begin
driver.get 'https://example.com/'

# Takes and Stores the screenshot in specified path
driver.save_screenshot('./image.png')

end
{{< /tab >}}
{{< tab header="JavaScript" >}}
let {Builder} = require('selenium-webdriver');
let fs = require('fs');

(async function example() {
let driver = await new Builder()
.forBrowser('chrome')
.build();

    await driver.get('https://www.example.com');
    // Returns base64 encoded string
    let encodedString = await driver.takeScreenshot();
    await fs.writeFileSync('./image.png', encodedString, 'base64');
    await driver.quit();
}())
{{< /tab >}}
{{< tab header="Kotlin" >}}
import com.oracle.tools.packager.IOUtils.copyFile
import org.openqa.selenium.*
import org.openqa.selenium.chrome.ChromeDriver
import java.io.File

fun main(){
val driver =  ChromeDriver()
driver.get("https://www.example.com")
val scrFile = (driver as TakesScreenshot).getScreenshotAs<File>(OutputType.FILE)
copyFile(scrFile, File("./image.png"))
driver.quit()
}
{{< /tab >}}
{{< /tabpane >}}

###  元素屏幕截图

用于捕获当前浏览上下文的元素的屏幕截图.
WebDriver端点
[屏幕截图](https://www.w3.org/TR/webdriver/#take-element-screenshot)
返回以Base64格式编码的屏幕截图.

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
import org.apache.commons.io.FileUtils;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import java.io.File;
import java.io.IOException;

public class SeleniumelementTakeScreenshot {
public static void main(String args[]) throws IOException {
WebDriver driver = new ChromeDriver();
driver.get("https://www.example.com");
WebElement element = driver.findElement(By.cssSelector("h1"));
File scrFile = element.getScreenshotAs(OutputType.FILE);
FileUtils.copyFile(scrFile, new File("./image.png"));
driver.quit();
}
}
{{< /tab >}}
{{< tab header="Python" >}}
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()

# Navigate to url
driver.get("http://www.example.com")

ele = driver.find_element(By.CSS_SELECTOR, 'h1')

# Returns and base64 encoded string into image
ele.screenshot('./image.png')

driver.quit()
{{< /tab >}}
{{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;
using OpenQA.Selenium.Support.UI;

    // Webdriver
    var driver = new ChromeDriver();
    driver.Navigate().GoToUrl("http://www.example.com");

    // Fetch element using FindElement
    var webElement = driver.FindElement(By.CssSelector("h1"));

    // Screenshot for the element
    var elementScreenshot = (webElement as ITakesScreenshot).GetScreenshot();
    elementScreenshot.SaveAsFile("screenshot_of_element.png");
{{< /tab >}}
{{< tab header="Ruby" >}}
# Works with Selenium4-alpha7 Ruby bindings and above
require 'selenium-webdriver'
driver = Selenium::WebDriver.for :chrome

begin
driver.get 'https://example.com/'
ele = driver.find_element(:css, 'h1')

# Takes and Stores the element screenshot in specified path
ele.save_screenshot('./image.jpg')
end
{{< /tab >}}
{{< tab header="JavaScript" >}}
const {Builder, By} = require('selenium-webdriver');
let fs = require('fs');

(async function example() {
let driver = await new Builder()
.forBrowser('chrome')
.build();

await driver.get('https://www.example.com');
let ele = await driver.findElement(By.css("h1"));
// Captures the element screenshot
let encodedString = await ele.takeScreenshot(true);
await fs.writeFileSync('./image.png', encodedString, 'base64');
await driver.quit();
}())
{{< /tab >}}
{{< tab header="Kotlin" >}}
import org.apache.commons.io.FileUtils
import org.openqa.selenium.chrome.ChromeDriver
import org.openqa.selenium.*
import java.io.File

fun main() {
val driver = ChromeDriver()
driver.get("https://www.example.com")
val element = driver.findElement(By.cssSelector("h1"))
val scrFile: File = element.getScreenshotAs(OutputType.FILE)
FileUtils.copyFile(scrFile, File("./image.png"))
driver.quit()
}
{{< /tab >}}
{{< /tabpane >}}

### 执行脚本

在当前frame或者窗口的上下文中，执行JavaScript代码片段.

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
//Creating the JavascriptExecutor interface object by Type casting
JavascriptExecutor js = (JavascriptExecutor)driver;
//Button Element
WebElement button =driver.findElement(By.name("btnLogin"));
//Executing JavaScript to click on element
js.executeScript("arguments[0].click();", button);
//Get return value from script
String text = (String) js.executeScript("return arguments[0].innerText", button);
//Executing JavaScript directly
js.executeScript("console.log('hello world')");
{{< /tab >}}
{{< tab header="Python" >}}
# Stores the header element
header = driver.find_element(By.CSS_SELECTOR, "h1")

# Executing JavaScript to capture innerText of header element
driver.execute_script('return arguments[0].innerText', header)
{{< /tab >}}
{{< tab header="CSharp" >}}
//creating Chromedriver instance
	IWebDriver driver = new ChromeDriver();
	//Creating the JavascriptExecutor interface object by Type casting
	IJavaScriptExecutor js = (IJavaScriptExecutor) driver;
	//Button Element
	IWebElement button = driver.FindElement(By.Name("btnLogin"));
	//Executing JavaScript to click on element
	js.ExecuteScript("arguments[0].click();", button);
	//Get return value from script
	String text = (String)js.ExecuteScript("return arguments[0].innerText", button);
	//Executing JavaScript directly
	js.ExecuteScript("console.log('hello world')");
{{< /tab >}}
{{< tab header="Ruby" >}}
# Stores the header element
header = driver.find_element(css: 'h1')

# Get return value from script
result = driver.execute_script("return arguments[0].innerText", header)

# Executing JavaScript directly
driver.execute_script("alert('hello world')")
{{< /tab >}}
{{< tab header="JavaScript" >}}
// Stores the header element
let header = await driver.findElement(By.css('h1'));

// Executing JavaScript to capture innerText of header element
let text = await driver.executeScript('return arguments[0].innerText', header);
{{< /tab >}}
{{< tab header="Kotlin" >}}
// Stores the header element
val header = driver.findElement(By.cssSelector("h1"))

// Get return value from script
val result = driver.executeScript("return arguments[0].innerText", header)

// Executing JavaScript directly
driver.executeScript("alert('hello world')")
{{< /tab >}}
{{< /tabpane >}}

### 打印页面

打印当前浏览器内的页面

_注意: 此功能需要无头模式下的Chromium浏览器_


{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
import org.openqa.selenium.print.PrintOptions;

    driver.get("https://www.selenium.dev");
    printer = (PrintsPage) driver;

    PrintOptions printOptions = new PrintOptions();
    printOptions.setPageRanges("1-2");

    Pdf pdf = printer.print(printOptions);
    String content = pdf.getContent();
{{< /tab >}}
{{< tab header="Python" >}}
from selenium.webdriver.common.print_page_options import PrintOptions

    print_options = PrintOptions()
    print_options.page_ranges = ['1-2']

    driver.get("printPage.html")

    base64code = driver.print_page(print_options)
{{< /tab >}}
{{< tab header="CSharp" >}}
// code sample not available please raise a PR
{{< /tab >}}
{{< tab header="Ruby" >}}
driver.navigate_to 'https://www.selenium.dev'

    base64encodedContent = driver.print_page(orientation: 'landscape')
{{< /tab >}}
{{< tab header="JavaScript" >}}
const {Builder} = require('selenium-webdriver');
const chrome = require('selenium-webdriver/chrome');
let opts = new chrome.Options();
let fs = require('fs');
(async function example() {
let driver = new Builder()
.forBrowser('chrome')
.setChromeOptions(opts.headless())
.build();
await driver.get('https://www.selenium.dev');
try {
let base64 = await driver.printPage({pageRanges:["1-2"]});
await fs.writeFileSync('./test.pdf', base64, 'base64');
} catch (e) {
console.log(e)
}
await driver.quit();
{{< /tab >}}
{{< tab header="Kotlin" >}}
driver.get("https://www.selenium.dev")
val printer = driver as PrintsPage

val printOptions = PrintOptions()
printOptions.setPageRanges("1-2")

val pdf: Pdf = printer.print(printOptions)
val content = pdf.content
{{< /tab >}}
{{< /tabpane >}}