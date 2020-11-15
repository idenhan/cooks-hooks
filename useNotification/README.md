# Usage

```js
import useNotification from "@react-hooks-10/use-notification"

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