# Form Use Case
#### One great way to play with the Naker API is to link it with a form as you can see on the [Naker login page](https://app.naker.io/login)  

## How to do that?

First you need to follow the Intale documentation in order to create a Intale next to your form. As you can see in this documentation you can add a callback and get the Intale object which contains all your scene assets like so:

```javascript
nakerintale.render({
  container: document.getElementById('container'),
  project: 'your-project-id',
}, (intale) => {
  // Intale loaded, now you can play with the Intale object!
});
```

The Intal object contains a lot of properties as you can see in our api documentation [**Intale Class**](../api/classes/intale.html). We will focus on two things: contentsManager and navigation.

## contentsManager

### Physical changes
The contentsManager is the class dealing with all your object in the Intale (image, model, cube, light, etc). This is where you can get any of those content in order to play with it and especially in our link a form's input with a content change.  
First to get a content from your Intale you can use the tag setted in our editor like that:
```javascript
let myContent = contentsManager.getContentByTag('tag_of_your_content');
```
To have the detail of a content you can check it in our api documentation [**Content Class**](../api/classes/content.html). This is the shared Class of all contents but you can also find every specific content detail following those links:

*  [Light Content](../api/classes/lightcontent.html)
*  [Model Content](../api/classes/modelcontent.html)
*  [Shape Content](../api/classes/shapecontent.html)
*  [Image Content](../api/classes/imagecontent.html)
*  [Video Content](../api/classes/videocontent.html)
*  [Heightmap Content](../api/classes/heightmapcontent.html)

#### Example
Here is what you could do for instance to make an Intale react to a form input:
```javascript
nakerintale.render({
  container: document.getElementById('container'),
  project: 'your-project-id',
}, (intale) => {
  // Get the light of the Intale
  let light = intale.contentsManager.getContentByTag('light');
  // Get the form input
  let textinput = window.getElementById('text-input');
  // When input is changed, adjust the light of the Intale
  textinput.oninput = () => {
    light.setIntensity(10);
  }
});
```
Following the documentation you will be able to play with any object in the 3D world.  

### Animation
To go further, you can also choose to animate a content after a user action. As in the editor you can put animation on any content, they all shared another class which is  [**Content Move Class**](../api/classes/animationcontent.html)  
As you can see in there, the contentMove class has the playAnimation function which will launch all the animations of the content. The one animation trigger event which launch it straight forward is the **show**. But show also mean that the nimation will start once the Intale is loaded so in order to avoid that, we will first need to stop it.
#### Example
```javascript
nakerintale.render({
  container: document.getElementById('container'),
  project: 'your-project-id',
}, (intale) => {
  // Get the light of the Intale
  let animatedContent = intale.contentsManager.getContentByTag('animated-content');
  animatedContent.pauseAnimation();
  // Get the form button
  let button = window.getElementById('button-input');
  // When button is clicked, launch the animation
  button.onclick = () => {
    animatedContent.playAnimation();
  }
});
```

This is how you can alter your object Intale and laucnh animation using inputs from a form.

## navigation
Another great interaction you can have between a form and a Naker's Intale is with [**navigation Class**](../api/classes/navigation.html). navigation is managing the journey of the user in an Intale. That class is responsible to launch the animation to go from one point of vue to an other. And that animation can be targeted (this is what we do when you validate the login page of Naker). That way if you have specified different point of view position/rotation/postprocess, you can animate all of that in just one function call.  
In the documentation page you can see the **moveToPointofView** method. That method simply take the name of your point of view as argument and it will make the what is needed to go to a specific point of view.

#### Example
```javascript
nakerintale.render({
  container: document.getElementById('container'),
  project: 'your-project-id',
}, (intale) => {
  // Get the form button
  let button = window.getElementById('button-input');
  // When button is clicked, launch the animation
  button.onclick = () => {
    // Insert the number of the point of view to be reached,
    // 0 is for the first Intale's point of view
    intale.navigation.moveToPointofView('pointofviewname');
  }
});
```
