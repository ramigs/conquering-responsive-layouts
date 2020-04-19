# conquering-responsive-layouts

> Notes and challenge solutions for [Kevin
> Powell's](https://www.kevinpowell.co/) course [Conquering Responsive
> Layouts](https://courses.kevinpowell.co/courses/conquering-responsive-layouts)

## Using percentages & avoiding heights

- Layouts are responsive by default. A website without CSS is responsive. It's us who ruin the responsiveness of the web.
- Work in percentages for widths.
- Percentage width of an element is always relative to its parent.
- Avoid setting heights.
- If you need more background use `padding`.

## em vs rem

https://codepen.io/kevinpowell/pen/RKdjXe
https://www.youtube.com/watch?v=_-aDOAMmDHI

- Pixels are solid units, they never change.
- `em` and `rem` make our lives much easier when it comes to responsive.
- The whole em unit has its background in the print world, but it the world of web it relates just to font sizes
- `em` looks at its parent's `font-size`. If `font-size` is not defined, it keeps looking up for it until its found.
- Generally, if `font-size` is not changed, `1em` equals to `16px`.
- With `em` the font sizes compound, they build on each other, so things can get out of control.
- `rem` (root em) was invented to fix the compounding problem. Relates to `html`'s `font-size`.
- `rem` units are more consistent.
- These units can be also used in other properties, such as margins and paddings.
- When `em` is used in properties other than `font-size`, it will look at its own `font-size`.

```css
.col--em h1 {
  font-size: 2.5em;
  margin-bottom: 1em;
}
```

- In the example above, `margin-bottom` will be `2.5em`.
- This does not apply to `rem`. `rem` will **always** look to the root.

```css
.col--em h1 {
  font-size: 2.5em;
  margin-bottom: 1rem;
}
```

- In this case, `margin-bottom` will be `16px` (the font size of the `html` element).

How is this useful? (See video at 8:10s)

- For example, setting `padding` in a `button`.

```css
.btn {
  padding: 1em 3em;
}
```

- Now, imagine we want a small button:

```css
.btn-small {
  font-size: 0.5em;
}
```

```html
<a href="#" class="btn btn-small"></a>
```

- Because we are using `em` the `padding` is automatically adjusting to the `font-size`, keeping everything in the same proportion.
- If it was in `rem`, the `padding` would have not changed, only the `font-size`.
- Its useful to use `em` for this kind of situations, where we want something to be _adaptable_ and _scalable_.
- It's a great way of having consistent elements. Just by creating a new class and setting its `font-size`.
- Now, imagine you'd want consistent spacing (`margin`) between the buttons. In that case it would be more appropriate to use `rem`. It's not going to be relative to the button's `font-size`, so it will always be the same.

- Mind-blowing trick with media queries @ 15:08:

```css
html {
  font-size: 16px;
}
@media (min-width: 700px) {
  html {
    font-size: 25px;
  }
}
```

- Everything gets bigger because at one point both `em`s and `rem`s will reach `html` (careful with the compounding effect). With one media query only, all the `font-size`s can be changed. If `px` was being used, it would not be possible to do this.
