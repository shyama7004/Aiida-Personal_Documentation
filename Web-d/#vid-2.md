## Your first html website
### HTML Introduction

Today, I'm writing this tutorial to create a resource that will help you learn HTML in less than 30 days. Here's a recommended timeline for learning HTML, based on your educational background:

- High School students and younger: Around 25 days
- Those beyond High School: Around 20 days
- College students and above: Around 10-20 days

You may be wondering why I'm discussing these timelines. It's important for me to set expectations before you start your journey of learning html with me.


### What is HTML?
HTML (HyperText Markup Language) was created by `Tim Berners-Lee in 1991` as a standard for creating web pages. It's a markup language used to structure content on the web, defining elements like headings, paragraphs, links, and images. HTML forms the backbone of web content. In layman's terms, HTML is like the skeleton of a website. It's a set of instructions that tells a web browser how to display text, images, videos, and other elements on a webpage. Think of it as the building blocks that create the structure and look of a website, similar to how bricks and mortar are used to build a house.

### In a nutshell:

- HTML is the language of the web, used to create websites.
- HTML defines the barebone structure or layout of web pages that we see on the Internet.
- HTML consists of a set of tags contained within an HTML document, and the associated files typically have either a `.html` or `.htm`       
  extension.
- There are several versions of HTML, with HTML5 being the most recent version.

### Features of HTML
- It is platform-independent. For example, Chrome displays the same pages identically across 
  different operating systems such as Mac, Linux, and Windows.
- Images, videos, and audio can be added to a web page (For example - YouTube shows videos on 
  their website)
- HTML is a markup language and `not a programming language`.
- It can be integrated with other languages like CSS, JavaScript, etc. to show interactive (or 
  dynamic) web pages
### Why the Term HyperText & Markup Language?
The term `Hypertext Markup Language` is composed of two main words: 'hypertext' and 'markup language.' 'Hypertext' refers to the linking of text with other documents, while 'markup language' denotes a language that utilizes a specific set of tags.

Thus, HTML is the practice of displaying text, graphics, audio, video etc. in a certain way using special tags.

`Note`: Tags are meaningful texts enclosed in angle braces, like `<...>`. For example, the `<head>` tag. Each tag has a unique meaning and significance in building an HTML page, and it can influence the web page in various ways.

### Quick Exercise:
Open a webpage of your choice, right-click on the browser, and select 'View Page Source,' and then you will see the HTML code for that page.

[Video](https://cwh-full-next-space.fra1.cdn.digitaloceanspaces.com/tutorial/html-home/view-page-source.mp4)
  

This is the code that the server sent to display the page you're currently viewing. In this tutorial, we'll learn how to write this type of code using HTML.

### A beautiful analogy to understand HTML, CSS, and JavaScript:
<img src="https://media.licdn.com/dms/image/D4D22AQHT1UrScknrBA/feedshare-shrink_2048_1536/0/1714834822376?e=2147483647&v=beta&t=d6J8h-ZdoipoEhdQpJoHYcYs_KXHyj89KRlAMZsbQX8">

In building a webpage, think of HTML, CSS, and JavaScript as different parts of a car. HTML is like the car's skeleton, forming the basic structure and frame. CSS adds the paint and finishing touches, making the car look appealing with color, style, and design. JavaScript is similar to the engine and mechanical parts, infusing the car with functionality, movement, and interactive features. Similarly, when developing a website, HTML lays out the structure, CSS enhances its visual appeal, and JavaScript provides interactivity and dynamic content

### History of HTML:
- In 1989, Tim Berners-Lee established the World Wide Web (www), and in 1991, he created the first version of HTML.
- From 1995 to 1997, further work was done to develop and refine different versions of HTML.
- In 1999, a committee was organized that standardized HTML 4.0, a version still used by many today.
- The latest and most stable version of HTML is 5, also known as HTML5.

### Creating 3 Files in VSCode.
1. index.html
2. script.js
3. style.css

#### Some Important extensions in VScode:
- VScode icons.
- jellyfish themes, github theme etc, `use any one`.
- Prettier
- ES7
- Live Preview(To see your code in website)

### Getting started with HTML

Now that your file is ready, copy the following code and paste it into your "index.html" file.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    Hello World
</body>
</html>
```
### Going Live using the "live server" extension
To see your webpage in action, locate the "Go Live" icon at the bottom-right corner of your VS Code window and click it. If you don't see this icon, you probably haven't installed the Live Server extension, which we discussed in a previous tutorial.
<img src="https://raw.githubusercontent.com/microsoft/vscode-livepreview/main/img/browser-demo.gif">

#### Embedded Preview
A preview is available in-editor for the files hosted by the server.<br>

<img src="https://raw.githubusercontent.com/microsoft/vscode-livepreview/main/img/browser-demo.gif">

The simple embedded browser features the following:

- Page history tracking
- URL bar for address-based navigation
- Expandable menu, allowing users to:
  - Preview the current page in browser
  - Perform a page search
      - Tip: You can also use CTRL+F to open the find box and Enter to go to the next result
  - Open the editor's webview DevTools<br>
  
<img src="https://raw.githubusercontent.com/microsoft/vscode-livepreview/main/img/find-demo.gif">

### Style.css

```css
body{
    backgroung-color: red;
    )
```
`You will not get any red color`.
<br>
`Reason`:We haven't linked 
<br>
### You can add this to link:
```html
<link rel = "stylesheet" href="style.css">
```
### How to change text color

<script src="https://codepen.io/web-dot-dev/pen/oNymmWw></script>

