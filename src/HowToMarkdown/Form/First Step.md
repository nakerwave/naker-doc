# Naker Form Viewer
#### A standalone library to add interaction to your form

## Getting Started

Import the Javascript Form Viewer in the header of your website :

```html
<script data-who='💎 Made with naker.io 💎' src='https://harbor.naker.io/form/viewer.js' ></script>
```

This line will import the `nakerform` global variable to your website.

## Usage

You then need to choose the html element which will be used to draw the form. You can just select this node by its `id` like this :
```javascript
var container = document.getElementById('container');
```

Same thing with the form which will be linked to the 3D content, let's select it by its tag name :
```javascript
var form = document.getElementByTagName('FORM');
```

Use the render function of the viewer and your form options in order to automatically create your 3D illustration like so :

```javascript
nakerform.render({
    container: document.getElementById('container'),
    form: document.getElementByTagName('FORM')
});
```

## Options
You must also add some options to the render function.
Type rgbArray:[r, g, b] and Vector3:{x:_number_, y:_number_, z:_number_}

### Particle

| Name           | Type            | Description                                    |
| :------------- | :----------:    | -----------------------------------------------|
| url            | _string_        | The image url used to create effect            |
| size           | _number_        | Size of the image                              |
| shape          | _string_        | The shape of the particles (cube, sphere, etc) |
| pieces         | _number_        | The number of particle to draw                 |
| positionFusion | _Vector3_       | Position change when form is filled in         |
| rotationFusion | _Vector3_       | Rotation change when form is filled in         |
| scalingFusion  | _Vector3_       | Scaling change when form is filled in          |
| alphaFusion    | _boolean_       | Alpha change when form is filled in            |
| gravityExplosion | _Vector3_     | Gravity on particle when form validation       |
| powerExplosion | _number_        | Power of particle movement when form validation|

### Environment

| Name           | Type            | Description                                    |
| :------------- | :----------:    | -----------------------------------------------|
| sensitivity    | _number_        | Sensitivity of the camera when the mouse move  |
| colorStart     | _rgbArray_      | Color of the top background                    |
| colorEnd       | _rgbArray_      | Color of the top background                    |
| gradient       | 'horizontal', 'vertical' or 'radial' | The way the gradient is drawn   |

### Result
At the end your render function will work like this:
```javascript
nakerform.render({
    container: document.getElementById('container'),
    particle:{
        url: "https://asset.naker.io/image/main/Logo_Naker_NEW.png",
        shape: "cube",
        pieces: 756,
        size: 20,
        positionFusion: {x: 1,y: 1,z: 1},
        rotationFusion: {x: 1,y: 1,z: 1},
        scalingFusion: {x: -1,y: -1,z: -1},
        alphaFusion: false,
        gravityExplosion: {x: 0,y: 0,z: 0},
        powerExplosion: 0.1
    },
    environment: {
        sensitivity: 0.96,
        colorStart: [0,0,0,1],
        colorEnd: [234,0,255,1],
        gradient: 'vertical'
    }
});
```

Note that the container object will need to have a position style defined, as we use absolute position of the canvas which draw the 3D scene, without a position on the container the canvas could go outside.

Plus if you need specific options, we are open to it. Send us an email to support@naker.io

## Examples

To see it in action, follow this link: 
[Form viewer](https://codepen.io/pichou/pen/eYYVPxX)  
