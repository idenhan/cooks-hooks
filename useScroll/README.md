# @react-hooks-10/use-scroll

React Hook to get X/Y coordinates of current position of the scroll.

## Installation

#### yarn

`yarn add @react-hooks-10/use-scroll`

#### npm

`npm i @react-hooks-10/use-scroll`

## Usage

```js
import React from "react";
import useScroll from "@react-hooks-10/use-scroll";

function App() {
  const { x, y } = useScroll();
  return (
    <h1>
      We are in: {x} / {y}
    </h1>
  );
}
```

### Return

| Return value | Type   | Description                                                             | Default value |
| ------------ | ------ | ----------------------------------------------------------------------- | ------------- |
| Coords       | Object | An object containing the x/y coordinates of the current scroll position | `{x:0, y:0}`  |