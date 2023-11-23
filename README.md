



# Stratox.js - Template library for building user interfaces

Stratox.js, an modern JavaScript library, facilitates the development of templates and user interfaces (UI) with a focus on components and views, offering a flexible and efficient approach to web development.

We encourage developers to prioritize JavaScript and HTML, as they should, instead of grappling with the complexities of new markup and platform-specific functions, which in the end only lead to the burden of unnecessary abstractions. Stratox harnesses JavaScript's core capabilities, promoting a practical and fundamental approach to modern web development.

### Platform-agnostic nature
Stratox.js doesn't discriminate or judge based on the platform you use, and it works seamlessly on all platforms and depends on nothing but it self.


## Installation
```
npm i stratox
```
*Or just download the zip and import Stratox.js file*


## Full documentation
The initial documentation draft is ready.
### [Read the documentation](https://wazabii.se/stratoxjs/)


## Quick guide / Preview
This is just a quick guide to preview how easy it is. Visit the link above for the full documention.

### index.html
Begin by adding an element to the HTML document.
*/examples/index.html*
```html
<div id="ingress"></div>
```

### Configure 
Add the configuration bellow in you main js file, some where it will globally execute.
```js
Stratox.setConfigs({
	directory: "/absolute/path/to/views/",
    cache: false, // Automatically clear cache if is false on dynamic import
    popegation: true // Automatic DOM popegation protection
});
```

**directory:**  Directory path for asynchronously or imported templates. Either specify an absolute directory path or if opting for a relative path, keep in mind it starts from the Stratox.js file location.

### Template files
First, we need to create a template for use. There are multiple ways to do this, but for this example, I'll demonstrate the most straightforward method. More examples will follow.

To begin, create a template file, such as **"/src/views/ingress.js"**. The file name will serve as the template identifier if it's loaded dynamically/asynchronously, which is the default behavior for templates that utilize separate files without pre importing.

#### Example template:
```js
// You can name the function whatever. 
// The important part is that at least one function must be exported
export function ingressComponent(data, container, helper, builder) {

	// In this example I am using Javacript Template literals for a clean look.
	// But as this is regular Javacript you can output it as you want.
	
	let out = `
	<header class="relative">
		<h1 class="title">${data.headline}</h1>
		<p>${data.content}</p>
	</header>
	`;
	return out;
}
```
What's fantastic is that you can create your template using plain JavaScript. I've also provided some handy helper functions to simplify your life. For instance, you can utilize the argument "helper" to access to the StratoxDom library, which offers a range of helpful functions.

###  Lets use the template
Once the template is created we only need to use it.
```js
let stratox = new Stratox("#ingress");

let ingress = stratox.view("ingress", {
    headline: "Lorem ipsum dolor",
    content: "Lorem ipsum dolor sit amet",
    tags: ["Tag 1", "Tag 2", "Tag 3"]
});

stratox.execute(function(observer) {
	// Callback...
});

```
That is it... As you can see it is very easy if you know HTML and javascript.


### Update the information
Want to update the templates information? 
```js
ingress.set({ headline: "Headline updated once!" });
stratox.update();

// Or...
stratox.view("ingress", { headline: "Headline updated twize!" });
stratox.update();

// Or...
stratox.update("ingress", function(obj) {
	obj.data.headline = "Headline updated thrice!";
});
```
The text has been updated three time with different techniques. Super easy. More example is coming when docs site is done.

