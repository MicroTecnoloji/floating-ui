# Flip

The flip modifier can change the `placement` of a popper when
the `detectOverflow` modifier reported it's overflowing on the
direction of the currently given placement.

If the popper has placement set to `bottom`, but there isn't space
to position the popper in that direction, by default, it will
change the popper placement to `top`.  
As soon enough space is detected, the placement will be reverted
to the originally defined one.

You can also define a custom "flip" behavior, by providing a list
of placements to try. Doing so, when no space is available on the
defined placement, the modifier will test the ones provided in the
list, and use the first useful one.

```js
new Popper(reference, popper, {
  placement: 'left',
  modifiers: [
    {
      name: 'flip',
      options: {
        behavior: ['top', 'right'],
      },
    },
  ],
});
```

In the above example, the popper will be placed on left if there's
enough space, if not, it will try the top placement, and if even
on the top placement there's not enough space, it will try to use
the right placement.  
Note that if none of the placements is suitable, the original left
placement will be used.