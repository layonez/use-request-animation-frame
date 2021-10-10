# use-request-animation-frame

React hook for easy access requestAnimationFrame browser API.
Written with Typescript and provides you with handy animation duration control.

## Usage

- Basic usage requres only one handler:

  ```typescript
  const nextAnimationFrameHandler = (progress: number) => {...};
  useRequestAnimationFrame(nextAnimationFrameHandler);
  ```

  With this `nextAnimationFrameHandler` will be called every frame and `progress` variable will always have value _1_, so you wont need it in your `nextAnimationFrameHandler`

- Usage with `duration`:

  ```typescript
  const myAnimatedDiv = React.useRef();
  const nextAnimationFrameHandler = (progress: number) => {
    if(myAnimatedDiv.current)
        myAnimatedDiv.current.style.left = progress * 100 + 'px'
    //...
  }
  useRequestAnimationFrame(nextAnimationFrameHandler, { duration: 2000 })
  ```

  In this case`nextAnimationFrameHandler` will be called every frame with `progress` calculated based on time when first animation frame was shown

- Usage with `shouldAnimate`:

  ```typescript
  const [shouldAnimate, setShouldAnimate] = React.useState(false);

  const nextAnimationFrameHandler = (progress: number) => {...};
  useRequestAnimationFrame(nextAnimationFrameHandler, { duration: 2000, shouldAnimate });
  ```

  In this case`nextAnimationFrameHandler` will not be called initially and animation will start only after `setShouldAnimate(true)` call


### ⭐ Happy Hacking ⭐

You can find more implementation details in my [article](https://layonez.medium.com/performant-animations-with-requestanimationframe-and-react-hooks-99a32c5c9fbf)
