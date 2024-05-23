
# AEM Sightly (HTL) Detailed Documentation

## What is AEM Sightly (HTL)?

**AEM Sightly**, now known as **HTL (HTML Template Language)**, is a templating language used in Adobe Experience Manager (AEM) for developing component-specific HTML. It is designed to replace JSP (JavaServer Pages) and provide a more secure and maintainable way to write server-side HTML.

## Key Features of HTL

1. **Separation of Concerns**: It ensures a clear separation between the logic and the presentation layers.
2. **Readability and Maintainability**: The syntax is designed to be easy to read and understand, even for those who are not experienced developers.
3. **Secure by Default**: It minimizes the risk of Cross-Site Scripting (XSS) attacks by escaping HTML output by default.
4. **Component-based Development**: Encourages reusable and modular design, aligning with AEM’s component-based architecture.

## Basic Syntax

HTL uses special attributes and expressions within HTML tags to inject dynamic content and logic. Here are some basics:

### Expressions

Insert dynamic data using `${}` syntax.
```html
<div>${message}</div>
```

### Context-Aware Escaping

By default, HTL escapes output to prevent XSS. For example:
```html
<div>${userInput}</div>
```
Here, `userInput` will be automatically escaped to prevent potential XSS attacks.

### Use API

Allows calling Java code and accessing Sling models.
```html
<sly data-sly-use.myComponent="com.example.MyComponent">
  <div>${myComponent.title}</div>
</sly>
```

### Components of HTL

#### Variables

Define variables within the template using `data-sly-use`.
```html
<sly data-sly-use.myVar="42">
  <div>${myVar}</div>
</sly>
```

#### Conditions

Use `data-sly-test` for conditional rendering.
```html
<div data-sly-test="${condition}">This is conditionally rendered</div>
```

#### Looping

Use `data-sly-list` to iterate over collections.
```html
<ul data-sly-list="${items}">
  <li>${item}</li>
</ul>
```

#### Templates

Reusable chunks of HTML that can be invoked multiple times.
```html
<sly data-sly-template.example="${ @ param1, param2 }">
  <div>${param1} - ${param2}</div>
</sly>
```

## Detailed Examples and Use Cases

### Using Sling Models

Sling Models can be integrated with HTL to provide dynamic content.

**Java Code (Sling Model):**
```java
@Model(adaptables = Resource.class)
public class MyModel {
  @Inject
  private String title;

  public String getTitle() {
    return title;
  }
}
```

**HTL Code:**
```html
<sly data-sly-use.model="com.example.MyModel">
  <div>${model.title}</div>
</sly>
```

### Using Global Objects

HTL provides several global objects that can be used within the templates.

#### `properties`
Represents the properties of the current resource.
```html
<div>${properties.title}</div>
```

#### `currentPage`
Provides information about the current page.
```html
<div>${currentPage.title}</div>
```

#### `resource`
Represents the current resource.
```html
<div>${resource.path}</div>
```

#### `sly`
Allows for template logic without generating output.
```html
<sly data-sly-use.var="com.example.MyModel">
  <!-- logic here -->
</sly>
```

### Handling Attributes Dynamically

HTL allows you to handle attributes dynamically.
```html
<a href="${link.url}" target="${link.target}">${link.text}</a>
```

### Custom HTL Functions

You can create custom HTL functions to extend the language.

**Java Code:**
```java
public class CustomFunctions {
  public static String toUpperCase(String input) {
    return input.toUpperCase();
  }
}
```

**HTL Code:**
```html
<sly data-sly-use.custom="com.example.CustomFunctions">
  <div>${custom.toUpperCase('hello')}</div>
</sly>
```

## Learning HTL in Detail

### Official Documentation and Resources

1. **Adobe Documentation**: The official Adobe Experience Manager documentation is the best place to start.
   - [AEM HTL Documentation](https://experienceleague.adobe.com/docs/experience-manager-htl/content.html?lang=en)

2. **HTL Specification**: Detailed specification of the language.
   - [HTL Specification](https://sling.apache.org/documentation/bundles/scripting/scripting-htl.html)

### Tutorials and Courses

1. **Adobe Experience League**: Offers tutorials and courses on AEM and HTL.
   - [Adobe Experience League](https://experienceleague.adobe.com/?lang=en)

2. **Online Learning Platforms**: Websites like Udemy, Pluralsight, and LinkedIn Learning offer AEM courses.
   - [Udemy AEM Courses](https://www.udemy.com/topic/adobe-experience-manager/)

### Books and Blogs

1. **Books**: There are several books on AEM development which include sections on HTL.
   - *Mastering Adobe Experience Manager* by Joey Sabani.
   - *Adobe Experience Manager Quick-Reference Guide* by Shane Closser.

2. **Blogs and Community Forums**: Follow AEM-related blogs and participate in forums.
   - [AEM Blog](https://aem4beginner.blogspot.com/)
   - [AEM Community](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

### Practice

1. **AEM Instances**: Set up a local AEM instance for hands-on practice.
   - Adobe provides trial versions of AEM for developers.
   
2. **Open Source Projects**: Contribute to or study open-source projects using AEM and HTL.
   - GitHub repositories can be a great resource.

3. **Build Projects**: Create your own projects to apply what you've learned. Start with simple components and gradually move to complex ones.

## Conclusion

Learning HTL involves a combination of understanding its syntax, practicing through projects, and staying updated with the latest best practices. Utilize the official Adobe documentation, online courses, community forums, and hands-on practice to become proficient in AEM HTL.

--
```
