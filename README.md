<p align="center" width="100%">
  <img width="25%" src="https://layerzs.tixte.co/r/layerzs.jpeg" alt="Layerzs">
</p>

<h1 align="center">Layerzs</h1>
<p align="center">
User-friendly API that makes web design and development simpler. <br />
It's available as either <strong>Tailwind</strong> classes or
<strong>React</strong> components.
</p>


<p align="center">
    <img src="https://img.shields.io/badge/work_is_still_in_progress-WIP-green?style=flat" alt="WIP">
    <img src="https://img.shields.io/github/license/cipherlogs/layerzs" alt="License">
</p>

------

<br />

## How does it work?
Layerzs provides advanced layers for layout, sizing, alignment, typography,
tables, effects, and more. Each category consists of at least two layers. This
guide starts with the foundational layers and moves upward.

**Note:** Please read the [discussion](https://github.com/cipherlogs/layerzs/discussions/1) and vote for what you believe is best.


<br />

## The Base Layer
Take flexbox as an example. The base layer is what you're already using,
whether you write vanilla CSS, CSS in JS, or use tailwind classes. The same
rules still apply.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/figg1-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/figg1-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/figg1-light.png" style="max-width: 100%;">
    </picture>
</p>

<br />

Before using it, you need to understand the main axis, the cross axis, and how
they change. This is great for beginners, but for advanced users it is
inefficient and a waste of time.

**Does Layerzs offer a better solution?**

<br />
<br />

## The First Layer

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/figs2-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/figs2-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/figs2-light.png" style="max-width: 100%;">
    </picture>
</p>

In the first layer, we use *flexes*. This simplifies things by removing
unnecessary details and extra work from the base layer.


<br />
<br />

### Alignments
Flexes is straightforward. It operates with only two fixed axes. These axes don't change, which makes understanding things very simple.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig3-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig3-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig3-light.png" style="max-width: 100%;">
    </picture>
</p>


For example, if you want to center an item along the X-axis, it will be
centered along the X-axis regardless of the flex direction or other factors.
It will always be centered along the X-axis.

Unlike flexbox, where many behaviors depend on various factors that you always
have to remember, flexes is different. Its API is like a strict rule that
never changes, making it really easy to understand and figure out. Let's try
using the *center* utility and see how it works in two different situations.
<br />

<ins>Note:</ins> When you use center, it's like using both centerX and centerY
at once. This means it will center along both the X-axis and the Y-axis.

<br />

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig4-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig4-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig4-light.png" style="max-width: 100%;">
    </picture>
</p>

<br />

By default, the API targets the **container**. To target an **item**, we add
'i' to any method we want. So instead of using 'center', we'll use item center
'iCenter'.


<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig5-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig5-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig5-light.png" style="max-width: 100%;">
    </picture>
</p>

That's interesting, **how's *flexes* capable of centering an item along
the X-axis when direction is row?**

Behind the scenes, flexes uses the item count inside the container to decide
if it can center them.


<br />
<br />

### Order
Flexes automatically manages the arrangement of items. If you need to change
the order of a specific item, you can use 'iShift'.


<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig6-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig6-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig6-light.png" style="max-width: 100%;">
    </picture>
</p>

<br />
<br />


Sometimes, you might want to set a custom order. Here's an example:

```css
.item:nth-child(3n+1) { order: 1; }
.item:nth-child(3n+2) { order: 2; }
.item:nth-child(3n)   { order: 3; }
```

You can create a custom order and use it with flex.

```js
const orders = {
  // "start, step": order
  "1, 3": 1,
  "2, 3": 2,
  "3, 3": 3,
};
```
In the second layer, you can't set a custom order. Instead, you get access to
a higher level API that lets you do more without worrying about low-level
details.


To learn more, check out the [API](./flexesAPI.md)


<br />
<br />

### Orientation

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig7-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig7-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig7-light.png" style="max-width: 100%;">
    </picture>
</p>


The reverse function changes the direction but keeps the layout the same. It
looks like the item orders are reversed. To only reverse the direction, use
*flip ("dir")*, or just *flip* if wrap is on.

**Note:** Please take a moment to [vote &uarr;](https://github.com/cipherlogs/layerzs/discussions/1) on upcoming API changes.

<br />
<br />

### Spacing
You can manage spacing from the **container** globally using autoGap. There
are 4 modes: none, around, between, even, and a fallback value if the mode
can't be used.

Example:
+ *autoGap ("around")*
+ *autoGap ("even", "gap-2")*
+ *autoGap ("none", "gap-x-2 gap-y-2")*


If you don't provide a fallback, a gap of `gap-2` will be used.


<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig8-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig8-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig8-light.png" style="max-width: 100%;">
    </picture>
</p>



To control the spacing of each item, use *iSpace*. It can do two things:

In order to control the spacing of each **item**, you can use *iSpace*. to
instruct it to do two things

+ Decide what to do when there's extra space:
    + Either add that space inside the item. **Inject**
    + Or put that space after, before or around the item. **Put**

+ Decide what to do when there's no space left (by default items will shrink). You can stop this or control how fast each item shrinks compared to others.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig9-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig9-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig9-light.png" style="max-width: 100%;">
    </picture>
</p>

That's it! Check out the docs and give it a try. With this small API, you can
do everything you need with flexbox and more.

**You might be wondering why there's another level on top of this?**

<br />
<br />

## The second layer
WIP
