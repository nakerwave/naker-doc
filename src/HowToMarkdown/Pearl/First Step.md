# Naker Pearl Viewer
#### A standalone library to add 3D model as illustration on your website

## Getting Started

Import the Javascript Pearl Viewer in the header of your website :

```html
<script data-who='💎 Made with naker.io 💎' src='https://d23jutsnau9x47.cloudfront.net/pearl/v1.0.4/viewer.js' ></script>
```

This line will import the `nakerpearl` global variable to your website.

## Usage

You then need to choose the html element which will be used to draw your model. You can just select this node by its `id` like this :
```javascript
var container = document.getElementById('container');
```

Use the render function of the viewer and your model url in order to automatically create your 3D illustration like so :

```javascript
nakerpearl.render({
  container: document.getElementById('container'),
  model: 'https://asset.naker.io/model/icosphere.gltf',
});
```

## Options

You can also add some options to the render function. Here is the list of the available once :

| Name           | Type         | Default      | Description                                                          |
| :------------- | :----------: | :----------: | -------------------------------------------------------------------- |
| modelFollowMouseRapidity  | _number_    | `1`       | Choose how fast the model rotates when the mouse is moving. Set it to 0 if you don't want it to rotate at all                                      |
| lightFollowMouseRapidity  | _number_    | `0`       | Choose how fast the light moves when the mouse is moving. Set it to 0 if you don't want it to move at all                                      |
| hdr  | _boolean_    | `false`       | Choose if the pearl should use an hdr texture in order to have a lightmap                                      |

```javascript
nakerpearl.render({
  container: document.getElementById('container'),
  model: 'https://asset.naker.io/model/icosphere.gltf',
  modelFollowMouseRapidity: 1,
  lightFollowMouseRapidity: 1,
  hdr: true
});
```

If you need a specific options, we are open to it. Juste create an issue to share your idea and discuss it.

## Callback

It is possible to add a callback as a second argument of the render function, this function will be called when the model is loaded. The callback returns the pearl object :

```javascript
nakerpearl.render({
  container: document.getElementById('container'),
  project: 'your-project-id',
}, (pearl) => {
  // model loaded, do what you need!
});
```

Check the pearl to see what you can do with it [**pearl Class**](../api/classes/pearl.html)

## Examples

To see it in action, follow this link:  
[Pearl viewer](https://codepen.io/pichou/pen/dLaaBW)  
