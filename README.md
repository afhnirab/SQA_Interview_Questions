# SQA_Interview_Questions

## 1. What are the differences between `findElement()` and `findElements()`?
<table>
  <tr>
    <th>findElement()</th>
    <th>findElelments()</th>
  </tr>
  <tr>
    <td>Finds the first matching web element based on the locator you provide.</td>
    <td>Finds all matching web elements and returns them as a list (possibly empty).</td>
  </tr>
  <tr>
    <td>Returns a single WebElement.</td>
    <td>Returns a List<WebElement> (which could be empty if no match is found)</td>
  </tr>
  <tr>
    <td>Throws a NoSuchElementException if no element matches the locator.</td>
    <td>Returns an empty list ([]) instead of throwing an exception.</td>
  </tr>
</table>

## 2. How do you handle dynamic web elements in Selenium?
1. Use stable attributes that don't change, such as: name, placeholder etc
2. Use partial attributes such is contains(), starts-with()
3. Instead of absolute paths, use relative locators that depend on nearby static elements.
4. When multiple similar elements exist, identify by index or nearby labels.

## 3. Explain different types of waits used in Selenium.
There are 3 types of waits selenium supports.
1. Implicit wait
    Tells the WebDriver to wait for a certain amount of time when trying to find an element if it’s not immediately available. Applies globally and set only once.
   ```
   driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
   ```
3. Explicit wait
   Waits for a specific condition to be true before continuing (like element visible, clickable, etc).
   ```
   WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
   WebElement element = wait.until(
     ExpectedConditions.visibilityOfElementLocated(By.id("submit"))
   );
   element.click();
   ```
5. Fluent wait
   A more flexible form of Explicit Wait that lets you: define polling frequency, ignnore specific exceptions.
   ```
   Wait<WebDriver> wait = new FluentWait<>(driver).withTimeout(Duration.ofSeconds(20)).pollingEvery(Duration.ofSeconds(2)).ignoring(NoSuchElementException.class);
   WebElement element = wait.until(
     driver -> driver.findElement(By.id("dynamicButton"))
   );
   element.click();
   ```
## 4. What’s the difference between XPath and CSS Selector?
<table>
  <tr>
    <th>XPath</th>
    <th>CSS Selector</th>
  </tr>
  <tr>
    <td>XML Path Language used to locate elements and attributes in an HTML/XML document.</td>
    <td>Uses Cascading Style Sheet syntax to find elements based on styles and structure.</td>
  </tr>
  <tr>
    <td>Syntax example: <code>//input[@id='username']</code></td>
    <td>Syntax example: <code>input[id='username']</code></td>
  </tr>
  <tr>
    <td>Can navigate both downward and upward in the DOM tree (parent, child, ancestor, descendant).</td>
    <td>Can navigate only downward in the DOM (parent → child or descendant).</td>
  </tr>
  <tr>
    <td>Syntax can be longer and more complex,</td>
    <td>Syntax is shorter and cleaner</td>
  </tr>
  <tr>
    <td>Works well for dynamic and complex elements</td>
    <td>Works best for static and straightforward element locators</td>
  </tr>
  <tr>
    <td>Supports searching by visible text using text() (e.g., <code>//button[text()='Login'])</code>.</td>
    <td>Does not support locating elements by text content.</td>
  </tr>
  <tr>
    <td>Allows combining multiple conditions with logical operators like and, or.</td>
    <td>Combines multiple attributes directly (e.g., <code>input[type='text'][name='email'])</code>.</td>
  </tr>
</table>
























