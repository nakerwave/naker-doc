# Naker Story Viewer
#### A standalone library to easily add naker intales anywhere online

## Getting Started

Import the Javascript Intale Viewer in the header of your website (current last version v1.0.2) :

```html
<script src="https://d23jutsnau9x47.cloudfront.net/story/v1.0.7/viewer.js"></script>
```

This line will import the `nakerstory` global variable to your website.

## Usage

You then need to choose the html element which will be used to build your naker intale. You can just select this node by its `id` like this :
```javascript
var container = document.getElementById('container');
```

Use the render function of the viewer and your `project id` in order to automatically create your scene like so :

```javascript
nakerstory.render({
  container: document.getElementById('container'),
  project: 'your-project-id',
});
```
You can find your `project id` from the url when you edit it.

## Options

You can also add some options to the render function. Here is the list of the available once :

| Name           | Type         | Default      | Description                                                          |
| :------------- | :----------: | :----------: | -------------------------------------------------------------------- |
| loadervisible  | _boolean_    | `true`       | Choose if text loader is visible                                      |

```javascript
nakerstory.render({
  container: document.getElementById('container'),
  project: 'your-project-id',
  loadervisible: false,
});
```

If you need a specific option for your project, we are open to it. Juste create an issue to share your idea and discuss it.

## Callback

It is possible to add a callback as a second argument of the render function, this function will be called when the intale is completly loaded. The callback returns the intale object with all its parameters :

```javascript
nakerstory.render({
  container: document.getElementById('container'),
  project: 'your-project-id',
}, (intale) => {
  // Intale loaded, do what you need!
});
```

Check the intale to see what you can do with it [**intale Class**](../api/classes/intale.html)

## Examples

To see it in action, follow these links:  
[Intale viewer in the body](https://codepen.io/pichou/pen/jJXpxd)  
[Intale viewer in a div](https://codepen.io/pichou/pen/YgdRKq)
