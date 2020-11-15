# @react-hooks-10/use-confirm

React Hook to ask the user for a confirmation before executing a function.

## Installation

#### yarn

`yarn add @react-hooks-10/use-confirm`

#### npm

`npm i @react-hooks-10/use-confirm`

## Usage

```js
import React from "react";
import useConfirm from "@react-hooks-10/use-confirm";

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