# balatroShader

![visitors](https://visitor-badge.laobi.icu/badge?page_id=Azkun.balatroShader)

Recreation of Balatro’s background shader on a website using basic WebGL and Javascript

### Support Balatro by buying it on [Steam](https://store.steampowered.com/app/2379780/Balatro)

The shader itself was created using WebGL and a series of transformations to generate the visual effect. Each pixel’s position is calculated relative to the center, then rotated based on the trigonometric functions, with multiple iterations to add complexity. Everything is rendered on the GPU, and different parameters are adjustable like colors, speed, spin amount, and other visual parameters...

# Usage

## Preamble

Before I decided to update the repository, you had to study my example HTML file and manually import lines of code while trying to understand how everything worked. The issue was that your code could easily end up being hundreds of lines long, and you couldn’t always grasp WebGL’s behavior entirely, especially for newer developers.

## Import

Now, you can use the project by importing `balatroShader.js` into your project, and by creating a component in your javascript file. You can choose the target element with its id, and you can change every parameter the way you like.

```html
    <script src="balatroShader.js"></script>
    <script>
    const fx = new BalatroShader({
        container: "#loader", // the ID of the target element
        colours: { c1: "#00e0ff", c2: "#ffffff", c3: "#000000" },
        speed: 1.4,
        contrast: 1.2,
        spinAmount: 0.5,
        pixelSizeFac: 1000, 
        spinEase: 0.5       
    });
    </script>
```

## API / Methods

### Constructor

```js
const fx = new BalatroShader(options);
```

| Option         | Type      | Default                                      | Description                                                              |                                                                                 |
| -------------- | --------- | -------------------------------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------- |
| `container`    | `string` or `HTMLElement`                                 | `document.body`                                                          | element where the shader is rendered. can be a CSS selector or an HTML element. |
| `colours`      | `object`  | `{c1:"#FF1919", c2:"#FFFFFF", c3:"#000000"}` | colors of the shader effect. use hex values.                             |                                                                                 |
| `speed`        | `number`  | `1.0`                                        | overall animation speed multiplier.                                      |                                                                                 |
| `spinAmount`   | `number`  | `0.5`                                        | amount of spinning applied to the effect (0–1).                          |                                                                                 |
| `contrast`     | `number`  | `1.2`                                        | controls the contrast of the shader colors.                              |                                                                                 |
| `pixelSizeFac` | `number`  | `700.0`                                      | determines the size of the “pixel blocks” in the shader. higher = smaller pixels, finer detail. |                                                                                 |
| `spinEase`     | `number`  | `0.5`                                        | controls smoothness of spin animation.                                   |                                                                                 |
| `zoom`         | `number`  | `30.0`                                       | zoom for the pattern.                                         |                                                                                 |
| `offsetX`      | `number`  | `-0.12`                                      | horizontal offset for the pattern.                                       |                                                                                 |
| `offsetY`      | `number`  | `0.0`                                        | vertical offset for the pattern.                                         |                                                                                 |
| `enableSpin`   | `boolean` | `true`                                       | toggle spinning on/off.                                                  |                                                                                 |
| `autoResize`   | `boolean` | `true`                                       | resize canvas automatically on window resize.                            |                                                                                 |
| `opacity`      | `number`  | `1.0`                                        | opacity of the canvas (0–1).                                             |                                                                                 |
| `maxFPS`       | `number`  | `60`                                         | maximum fps to render.                                     |                                                                                 |

Default parameters are the ones that seem to be the most coherent for me (except colors).

### Methods

| Method      | Description                                                    |
| ----------- | -------------------------------------------------------------- |
| `pause()`   | pauses the animation.                                   |
| `resume()`  | resumes the animation (if paused).                        |
| `destroy()` | stops the animation and removes the canvas from the container. |


### Example usage


```html
<body id="loader">
    <script src="balatroShader.js"></script>
    <script>
        const fx = new BalatroShader({
            container: "#loader",
            colours: { c1: "#DE443B", c2: "#006BB4", c3: "#162325" },
            speed: 1.4,
            contrast: 2,
            spinAmount: 0.5,
            pixelSizeFac: 1000,
            spinEase: 0.5
        });

    // Here, imagine you need to pause / resume / destroy the shader

        fx.pause();

        fx.resume();

        fx.destroy();
     </script>

</body>
```

Feel free to refer to [this example file](https://github.com/Azkun/balatroShader/blob/main/example.html) in case you want a concrete file example using the shader as a wallpaper. 

### Video showcasing the shader

https://github.com/user-attachments/assets/85d91e27-8d70-4ef6-8180-1a8f73e7b325


# Legal Disclaimer

> [!IMPORTANT]
> This project is in no way affiliated with, endorsed by, or representative of Playstack, Inc. or LocalThunk. “Playstack”, “LocalThunk” and “Balatro” are the property of Playstack, Inc., and are registered trademarks and copyright-protected.