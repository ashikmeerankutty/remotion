---
title: measureSpring()
id: measure-spring
---

_Available from v2.0.8_

Based on a [spring()](/docs/spring) configuration and the frame rate, return how long it takes for a spring animation to settle.

```tsx twoslash
import {measureSpring, SpringConfig} from 'remotion'

const config: Partial<SpringConfig> = {
  damping: 200,
}

measureSpring({
  fps: 30,
  config: {
    damping: 200,
  },
}) // => 23
```

:::info
Theoretically, a spring animation never ends. There is always a miniscule amount or energy left in the spring that causes tiny movements. Instead, we set a threshold to define when the spring animation is considered done.
:::

## Arguments

An object with these keys:

### `fps`

The frame rate on which the spring animation is based on.

### `threshold`

_optional - default: `0.005`_

Defines when the animation should be considered finished. `0.01` means that the animation is finished when it always stays within 1% of the `to` value. For example an animation that goes from 0 to 1 is considered finished when the value never leaves the range [0.99, 1.01] after the end point.

Lower values mean the spring duration is longer, higher values result in the spring duration being shorter.

### `config?`

_optional_

The spring configuration that you pass to [spring()](/docs/spring#config).

### `from?`

_optional - default: `1`_

The initial value of the animation.

### `to?`

_optional - default: `1`_

The end value of the animation. Note that depending on the parameters, spring animations may overshoot the target a bit, before they bounce back to their final target.

## See also

- [spring()](/docs/spring)
