# Naker Back Viewer with Frameworks

## Getting Started

When using a framework we have to set the background using the Naker.Back api. 
First if you don't have access to your head tag, you will have to load nakerback script asynchronously. This is how to do it:
```javascript
const script = document.createElement("script");
script.src = "https://d23jutsnau9x47.cloudfront.net/back/v1.0.3/viewer.js";
script.async = true;
document.body.appendChild(script);
```

Reminder, if you do have access to your head tag you can just put in it:
```javascript
<script data-who='💎 Made with naker.io 💎' src='https://d23jutsnau9x47.cloudfront.net/back/v1.0.3/viewer.js' ></script>
```

Then using the api you must call the render function to build the back exactly as explain in the [Classic](./Back/Classic.html) documentation. 

You also have to make sure the element which will contain the back is built before rendering it. Depending on the framework you can make sure of that. 

Plus if you want to make sure the rendering is stopped when changind page or view, you can do:
```javascript
let naker = window.nakerback.render({ 
  // Your Options // 
});

naker.system.stopRender();
```


Here are some exemples depending on the framework you are using:

### Angular 

Put nakerback.render in ngOnInit function:
```javascript
@Component({  
    selector: 'my-App',  
    template: '<div id="container"></div>'  
})  
  
export class AppComponent implements OnInit  {  
    ngOnInit() {
        window.nakerback.render({
            container: document.getElementById('container'),
            particle: {
                direction1: {x: 0,y: 0,z: 0},
                direction2: {x: 0,y: 0,z: 0},
                life: 0,
                texture: "https://d2uret4ukwmuoe.cloudfront.net/particle/sparks.png",
                number: 819,
                colorStart: [255,255,255,1],
                colorEnd: [255,255,255,1],
                sizeStart: 0.18,
                sizeEnd: 0.36,
            },
            environment: {
                sensitivity: 0.96,
                backgroundTop: [0,0,0,1],
                backgroundBottom: [234,0,255,1]
            }
        });
    }
}  
```

Note: As angular is using typescript, you could need to add "// @ts-ignore" before window.nakerback.render so that the compilator works correctly.

### React 
Put nakerback.render in componentDidMount function:

```javascript
class AppComponent extends React.Component {

    componentDidMount() {
        window.nakerback.render({
            container: document.getElementById('container'),
            particle: {
                direction1: {x: 0,y: 0,z: 0},
                direction2: {x: 0,y: 0,z: 0},
                life: 5.3,
                power: 0.5,
                texture: "https://res.cloudinary.com/naker-io/image/upload/v1566560053/circle_02.png",
                number: 0,
                colorStart: [89,173,220,0.63],
                colorEnd: [198,199,230,0.87],
                sizeStart: 2,
                sizeEnd: 4
            },
            environment: {
                sensitivity: 0.8,
                backgroundTop: [80,233,213,0.59],
                backgroundBottom: [16,106,227,0.96]
            }
        });
    }
    ​

    render() {
        return <div id="container"></div>;
    }
}
```

### HyperApp 
Put nakerback.render in oncreate function:

```javascript
const view = (state, actions) => props => (
	  <div oncreate={element => { actions.createBack(element); }}></div>
)
  
const state = {}

const actions = {
    createBack: (element) => (state, actions) => {
        window.nakerback.render({
            container: element,
            particle: {
                direction1: {x: 0,y: 0,z: 0},
                direction2: {x: 0,y: 0,z: 0},
                life: 5.3,
                power: 0.5,
                texture: "https://res.cloudinary.com/naker-io/image/upload/v1566560053/circle_02.png",
                number: 0,
                colorStart: [89,173,220,0.63],
                colorEnd: [198,199,230,0.87],
                sizeStart: 2,
                sizeEnd: 4
            },
            environment: {
                sensitivity: 0.96,
                backgroundTop: [0, 0, 0, 1],
                backgroundBottom: [234, 0, 255, 1]
            }
        });
    },
}
```