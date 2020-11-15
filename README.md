# cooks-hooks

## Installation

#### yarn

`yarn add cooks-hooks`

#### npm

`npm i cooks-hooks`

## useTitle

React Hook to update your document's title.

### Usage

```js
import React from "react";
import useTitle from "cooks-hooks";

function App() {
  useTitle("Welcome");
  return <h1>Welcome</h1>;
}
```

### Arguments

| Argument | Type   | Description                                | Required |
| -------- | ------ | ------------------------------------------ | -------- |
| title    | string | The title you want to use on your document | yes      |

## useScroll

React Hook to get X/Y coordinates of current position of the scroll.

### Usage

```js
import React from "react";
import useScroll from "cooks-hooks";

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

## usePreventLeave

React Hook to prompt the user for confirmation before leaving the page. Useful when changes haven't been saved.

### Usage

```js
import React from "react";
import usePreventLeave from "cooks-hooks";

function App() {
  const { enablePrevent, disablePrevent } = usePreventLeave();
  const saveChanges = async () => {
    enablePrevent();
    await sendToApi();
    disablePrevent();
  };
  return <button onClick={saveChanges}>Save changes</button>;
}
```

### Return

| Return value | Type   | Description                                                                                                                     |
| ------------ | ------ | ------------------------------------------------------------------------------------------------------------------------------- |
| Functions    | Object | A object containing functions `enablePrevent` and `disablePrevent`, use this functions to enable/disable the leaving prevention |

## useTabs

## useNotification

React Hook to show users a notfication when the notification permission is allowed.

### Usage

```js
import useNotification from "cooks-hooks"

const App = () => {
  const triggerNotif = useNotification('Can i steal your galbi?', {
    body: 'Because I love galbi so much'
  });
  return (
    <div className="App">
      <button onClick={triggerNotif}>Send Notification</button>
    </div>
  );
}
```

## useNetwork

React Hook to listen when the user goes online or offline.

### Usage

```js
import React from "react";
import useNetwork from "cooks-hooks";

function App() {
  const onNetworkChange = isOnline =>
    console.log(isOnline ? "We are back online" : "We just got offline");
  const isOnline = useNetwork(onNetworkChange);
  return <h1>{isOnline ? "We are online" : "We are offline"}</h1>;
}
```

### Arguments

| Argument        | Type     | Description                                           | Arguments          | Required |
| --------------- | -------- | ----------------------------------------------------- | ------------------ | -------- |
| onNetworkChange | function | Function to be called when the network status changes | isOnline : Boolean | no       |

### Return

| Return value | Type    | Description                                         | Default value |
| ------------ | ------- | --------------------------------------------------- | ------------- |
| isOnline     | Boolean | A boolean representing if the user is online or not | true          |

## useInput

### Usage

```js
import useInput from "cooks-hooks"

const App = () => {
  const validator = value => !value.includes("@");
  const name = useInput("Mr. ", validator);
  return (
    <div className="App">
      <h1>Hello</h1>
      <input placeholder="Name" {...name.props} />
    </div>
  );
};
```

## useHover

React Hook to detect a hover on an any React Element

### Usage

```js
import React from "react";
import useHover from "cooks-hooks";

function App() {
  const onHover = () => console.log("Somebody hovered!");
  const markedRef = useClick(onHover);
  return <h1 ref={markedRef}>Hello cooks-hooks</h1>;
}
```

### Arguments

| Argument | Type     | Description                                       | Required |
| -------- | -------- | ------------------------------------------------- | -------- |
| onHover  | function | Function to be called when the element is hovered | yes      |

### Return

| Return value | Type      | Description                                                     | Default value |
| ------------ | --------- | --------------------------------------------------------------- | ------------- |
| ref          | React Ref | A React Ref listening to the hover event, add it to any element | null          |

## useFullScreen

React Hook to make any element go FullScreen

### Usage

```js
import React from "react";
import useFullScreen from "cooks-hooks";

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

## useFadeIn

React Hook to fade in any element.

### Usage

```js
import React from "react";
import useFadeIn from "cooks-hooks";

function App() {
  const fadeIn = useFadeIn(5, 10);
  return <h1 {...fadeIn}>This will fade in</h1>;
}
```

### Arguments

| Argument | Type   | Description                                     | Required | Default value |
| -------- | ------ | ----------------------------------------------- | -------- | ------------- |
| duration | number | Sets the duration of the transition. In seconds | no       | 1             |
| delay    | number | Delays of transition's start. In seconds        | no       | 0             |

### Return

`useScroll` returns an object containing the following:

| Name  | Type      | Description                                                               |
| ----- | --------- | ------------------------------------------------------------------------- |
| ref   | React Ref | A ref created to fadeIn the element                                       |
| style | Object    | Style object containing `{opacity:0}` to give to the element as a default |

It's recommended to just spread the returned object on the element as shown in the Usage section above.

## useAxios

## useConfirm

React Hook to ask the user for a confirmation before executing a function.

### Usage

```js
import React from "react";
import useConfirm from "cooks-hooks";

function App() {
  const deleteWorld = () => console.log("Deleting world...");
  const confirmDelete = useConfirm("Are you sure?", deleteWorld);
  return <button onClick={confirmDelete}>Delete the world</button>;
}
```

### Arguments

| Argument  | Type     | Description                                         | Required |
| --------- | -------- | --------------------------------------------------- | -------- |
| message   | string   | Message to show the user on the confirmation propmt | yes      |
| onConfirm | function | Function to be executed when the user confirms      | yes      |
| onCancel  | function | Function to be executed when the user cancels       | no       |

### Return

| Return value | Type     | Description                                    | Default value |
| ------------ | -------- | ---------------------------------------------- | ------------- |
| function     | function | Function wrapped around the confirmation logic | null          |

## useClick

## useBeforeLeave

React Hook to execute a function when the mouse leaves the page. Useful to show a popup or for analytics.

### Usage

```js
import React from "react";
import useBeforeLeave from "cooks-hooks";

function App() {
  const beforeLeave = () => console.log("User is leaving...");
  useBeforeLeave(beforeLeave);
  return <h1>Hello react-hooks-10</h1>;
}
```

### Arguments

| Argument      | Type     | Description                                              | Required |
| ------------- | -------- | -------------------------------------------------------- | -------- |
| onBeforeLeave | function | Function to be called when the mouse leaves the document | yes      |