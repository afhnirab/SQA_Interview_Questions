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

## 3.
