# @react-hooks-10/use-fullscreen

React Hook to make any element go FullScreen

## Installation

#### yarn

`yarn add @react-hooks-10/use-fullscreen`

#### npm

`npm i @react-hooks-10/use-fullscreen`

## Usage

```js
import React from "react";
import useFullScreen from "@react-hooks-10/use-fullscreen";

function App() {
  const onChange = isFull =>
    console.log(isFull ? "We are in FullScreen" : "We are not in FullScreen");
  const { element, triggerFull, exitFull } = useFullScreen(onChange);
  return (
    <div ref={element}>
      <h1>Hello</h1>
      <button onClick={triggerFull}>Make this FullScreen</button>
      <button onClick={exitFull}>Exit FullScreen</button>
    </div>
  );
}
```

### Arguments

| Argument | Type     | Description                                                       | Arguments        | Required |
| -------- | -------- | ----------------------------------------------------------------- | ---------------- | -------- |
| onChange | function | Function to be called when the screen goes FullScreen or exits is | isFull : Boolean | no       |

### Return

`useFullscreen` returns an object containing the following:

| Return value | Type      | Description                                                |
| ------------ | --------- | ---------------------------------------------------------- |
| element      | React Ref | Ref to add to the element that you want to make fullscreen |
| triggerFull  | Function  | Function to make the element enter fullscreen              |
| exitFull     | Function  | Function to make the document exit fullscreen              |