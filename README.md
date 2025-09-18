# Landing Page

A web slicing project from the Foundations Course on
[The Odin Project](https://www.theodinproject.com/lessons/foundations-landing-page).

The goal of this project is to apply what I've learned so far in
the Foundations Course, especially CSS Flexbox.

Although the project assignment says *“You do **not** need to make this project responsive”*,
it’s still possible to make the site responsive using what The Odin Project has taught so far.

However, the image in the hero section is still not responsive — it would require using
`@media screen`, which hasn’t been covered yet. So I’ll stick to what TOP has taught so far,
trusting their decision since I don’t know what will be taught in later courses.

Utilizing:
- `flex-wrap`
- `flex-shrink`
- `flex-grow`
- `flex-basis`

Example from this project's CSS
<small>*(some classes are combined in this example)*</small>:

```css
.hero > .container {
  display: flex;
  justify-content: space-between;
  /* using wrap to automatically break line when not enough room */
  flex-wrap: wrap;
  gap: 2em;
  max-width: 1280px;
  margin: 0 auto;
  padding: 3em 1em;
}

.hero .left {
  flex: 1;
  max-width: 576px;
}

.hero .right {
  /* flex-grow default is 0, not able to grow */
  flex-shrink: 0;     /* not able to shrink */
  flex-basis: 576px;  /* we can say it's like width */
}
```

`.hero > .container` just normal flexbox stuff, so:

1. Let's focus on `.hero .left`

   `flex: 1;` is equal to:
   - `flex-grow: 1;`<br>
     (Able to grow)
   - `flex-shrink: 1;`<br>
     (Able to shrink)
   - `flex-basis: 0%;`<br>
     (If there is any initial width, it will be ignored. It will just grow to fill the available space)

   `max-width` is used here to limit the width when there is space to grow.

2. Then on `.hero .right`

   `flex-basis: 576px` is just like `width: 576px`. The difference is:
   - `width` is a fixed width
   - `flex-basis` can be flexible depending on the `flex-grow` and `flex-shrink`

   In this CSS selector, both `flex-grow` and `flex-shrink` are 0, so it's just like a normal `width`.
   I still use `flex-basis` just in case in the future I need to take advantage of it.

   Check the very first example from [this website](https://www.joshwcomeau.com/css/interactive-guide-to-flexbox/)
   to understand how amazing `flex-basis` is compared to a normal `width` when used in a flexbox.

---

What happens in the hero section when the screen width gets smaller is:
1. The text on the left side keeps shrinking (`flex-shrink: 1;`),
  while the image on the right side keeps its size (`flex-shrink: 0;`).

2. When the left side can no longer shrink, the right side breaks to a new line.

3. When a line break happens, the left side grows (`flex-grow: 1;`) again to its `max-width: 576px;`.

Later, when The Odin Project teaches us about `@media screen`, I will adjust the layout
so that the hero content is centered and the image resizes accordingly. The other sections are
already responsive enough even without using `@media screen`.
