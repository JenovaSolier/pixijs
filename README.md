# PixiJS Animated GIF

[![Node.js CI](https://github.com/pixijs/gif/actions/workflows/nodejs.yml/badge.svg?branch=main)](https://github.com/pixijs/gif/actions/workflows/nodejs.yml)

Plugin to support playback of animated GIF images in PixiJS. Unlike normal GIF playback in the browser, this plugins allows you to stop, loop, change speed, or go to a specific frame.

* [Demo](https://pixijs.io/gif/demo/)
* [API Documentation](https://pixijs.io/gif/docs/)

## Usage

Install the loader for handle GIF images.

```ts
import { AnimatedGIFLoader } from '@pixi/gif';
import { Loader } from '@pixi/loaders';

Loader.registerPlugin(AnimatedGIFLoader);
```

Load an animated GIF image:

```ts
import { Application } from 'pixi.js';

const app = new Application();
app.loader.add('image', 'image.gif');
app.loader.load((loader, resources) => {
    const image = resources.image.animation;
    app.stage.addChild(image);
});
```

To use a gif without Loader:

```ts
import { Application } from 'pixi.js';
import { AnimatedGIF } from '@pixi/gif';

const app = new Application();
fetch('image.gif')
    .then(res => res.arrayBuffer())
    .then(AnimatedGIF.fromBuffer)
    .then(image => app.stage.addChild(image));
```
