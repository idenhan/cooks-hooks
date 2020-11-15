# @react-hooks-10/use-title

React Hook to update your document's title.

## Installation

#### yarn

`yarn add @react-hooks-10/use-title`

#### npm

`npm i @react-hooks-10/use-title`

## Usage

```js
import React from "react";
import useTitle from "@react-hooks-10/use-title";

function App() {
  useTitle("Welcome");
  return <h1>Welcome</h1>;
}
```

### Arguments

| Argument | Type   | Description                                | Required |
| -------- | ------ | ------------------------------------------ | -------- |
| title    | string | The title you want to use on your document | yes      |