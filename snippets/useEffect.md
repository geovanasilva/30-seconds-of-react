---
title: useEffect
tags: hooks,effect,state,intermediate
---

A hook that implements `useEffect` with a window width size example.

- Use `React.useEffect()` to recover de width size of a window.

```jsx
function useWndowWidthSize() {
  const [windowWidthSize, setWindowWidthSize] = React.useState(0);

  React.useEffect(() => {
    handleResize = (e) => {
      const { width } = document.body.getBoundingClientRect();

      setWindowWidthSize(Math.ceil(width));
    }

    window.addEventListener('resize', handleResize);

    return () => window.removeEventListener('resize', handleResize);
  }, []);
  
  return windowWidthSize;
};

const WindowWidthSize = () => {
  const windowWidthSize = useWndowWidthSize();
  return (
    <h1>
      Window width size is now: {windowWidthSize} pixels
    </h1>
  )
};

```

```jsx
ReactDOM.render(<WindowWidthSize />, document.getElementById('root'));
```
