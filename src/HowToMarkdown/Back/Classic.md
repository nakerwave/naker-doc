# Naker Back Viewer
#### A standalone library to add 3D backgrounds on your website

## Getting Started

Import the Javascript Back Viewer in the header of your website :

```html
<script data-who='💎 Made with naker.io 💎' src='https://d23jutsnau9x47.cloudfront.net/back/v1.0.2/viewer.js' ></script>
```

This line will import the `nakerback` global variable to your website.

## Usage

You then need to choose the html element which will be used to draw the background. You can just select this node by its `id` like this :
```javascript
var container = document.getElementById('container');
```

Use the render function of the viewer and your background options in order to automatically create your 3D illustration like so :

```javascript
nakerback.render({
  container: document.getElementById('container'),
});
```

## Options
You must also add some options to the render function.
Type rgbArray:[r, g, b] and Vector3:{x:_number_, y:_number_, z:_number_}

### Particle

| Name           | Type            | Description                                    |
| :------------- | :----------:    | -----------------------------------------------|
| texture        | _string_        | The texture of particles                       |
| number         | _number_        | The number of particle to draw                 |
| colorStart     | _rgbArray_      | Color of particle when it appears              |
| colorEnd       | _rgbArray_      | Color of particle when it desappears           |
| sizeStart      | _number_        | Size of particle when it appears               |
| sizeEnd        | _number_        | Size of particle when it desappears            |
| life           | _number_        | Size of particle when it desappears            |
| direction1     | _Vector3_       | Direction of the particle when it appears      |
| direction2     | _Vector3_       | Second direction of the particle when it appears |

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
nakerback.render({
    container: document.getElementById('container'),
    particle:{
        direction1:{x:0,y:0,z:0},
        direction2:{x:0,y:0,z:0},
        life:0,
        texture:"https://d2uret4ukwmuoe.cloudfront.net/particle/sparks.png",
        number:819,
        colorStart:[255,255,255,1],
        colorEnd:[255,255,255,1],
        sizeStart:0.18,
        sizeEnd:0.36,
        delay:0
    },
    environment:{
        sensitivity:0.96,
        colorStart:[0,0,0,1],
        colorEnd:[234,0,255,1],
        gradient: 'vertical'
    }
});
```

Note that the container object will need to have a position style defined, as we use absolute position of the canvas which draw the back, without a position on the container the canvas could go outside.

Plus if you need specific options, we are open to it. Send us an email to support@naker.io

## Examples

To see it in action, follow this link:  
[Back viewer](https://codepen.io/pichou/pen/QegLbG)  
