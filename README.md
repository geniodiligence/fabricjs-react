# @geniodiligence/fabricjs-react

[![NPM](https://img.shields.io/npm/v/@geniodiligence/fabricjs-react.svg)](https://www.npmjs.com/package/@geniodiligence/fabricjs-react) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

Maintained fork of [fabricjs-react](https://github.com/asotog/fabricjs-react) by [Alejandro Soto](https://github.com/asotog), with up-to-date tooling and support for Fabric.js v7.

## Install

We'll need to install `fabric`, `react` and `react-dom` because are peer dependencies of this library if you haven't yet otherwise install only what you don't have:

```bash
npm install --save @geniodiligence/fabricjs-react fabric react react-dom
```

## Usage

Take a look at sandbox: https://codesandbox.io/s/flamboyant-wind-ff3x8

```tsx
import React from 'react'

import { FabricJSCanvas, useFabricJSEditor } from '@geniodiligence/fabricjs-react'

const App = () => {
  const { editor, onReady } = useFabricJSEditor()
  const onAddCircle = () => {
    editor?.addCircle()
  }
  const onAddRectangle = () => {
    editor?.addRectangle()
  }

  return (
    <div>
      <button onClick={onAddCircle}>Add circle</button>
      <button onClick={onAddRectangle}>Add Rectangle</button>
      <FabricJSCanvas className='sample-canvas' onReady={onReady} />
    </div>
  )
}

export default App
```

## Alternative use cases

### Add image ([#3](https://github.com/asotog/fabricjs-react/issues/3))

For this case, you have to reference the FabricJS dependency to first load the image:

```tsx
import { FabricImage } from "fabric"; // this also installed on your project
import { useFabricJSEditor } from '@geniodiligence/fabricjs-react';

const { selectedObjects, editor, onReady } = useFabricJSEditor();

useEffect(() => {
  const loadImage = async () => {
    const image = await FabricImage.fromURL(
      "https://www.searchenginejournal.com/wp-content/uploads/2019/07/the-essential-guide-to-using-images-legally-online.png"
    );
    editor?.canvas.add(image);
  }
  loadImage()
}, [fabric, editor])

...
```



## License

MIT © 2020 [Alejandro Soto](https://github.com/asotog), © 2026 Genio Diligence. See [LICENSE](LICENSE).

Feel free to collaborate.
