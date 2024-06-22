---
category: Sensors
---

# useKeyModifier

Reactive [Modifier State](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/getModifierState). Tracks state of any of the [supported modifiers](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/getModifierState#browser_compatibility) - see Browser Compatibility notes.

## Usage

```ts
import { useKeyModifier } from "solidjs-use"

const capsLockState = useKeyModifier("CapsLock")

console.log(capsLockState())
```

## Events

You can customize which events will prompt the state to update. By default, these are `mouseup`, `mousedown`, `keyup`, `keydown`. To customize these events:

```ts
import { useKeyModifier } from "solidjs-use"

const capsLockState = useKeyModifier("CapsLock", { events: ["mouseup", "mousedown"] })

console.log(capsLockState()) // null

// Caps Lock turned on with key press
console.log(capsLockState()) // null

// Mouse button clicked
console.log(capsLockState()) // true
```

## Initial State

By default, the returned ref will be `Accessor<null>` until the first event is received. You can explicitly pass the initial state to it via:

```ts
const capsLockState1 = useKeyModifier("CapsLock") // Accessor<boolean | null>
const capsLockState2 = useKeyModifier("CapsLock", { initial: false }) // Accessor<boolean>
```

## Prevent Default

You can prevent default by `preventDefault` option. It will only prevent the modifier you specify.

```ts
const capsLockState2 = useKeyModifier("CapsLock", { preventDefault: false })
```
