<p align="center" width="100%">
  <img width="25%" src="https://layerzs.tixte.co/r/layerzs.jpeg" alt="Layerzs">
</p>

<h1 align="center">Layerzs</h1>
<p align="center">
    A delightful and easy-to-use API that simplifies web design and development.<br />
  Available as either <strong>Tailwind</strong> classes or <strong>React</strong> components.</strong>
</p>


<p align="center">
    <img src="https://img.shields.io/badge/work_is_still_in_progress-WIP-green?style=flat" alt="WIP">
    <img src="https://img.shields.io/github/license/cipherlogs/layerzs" alt="License">
</p>

------

<br />

## How does it work?
You have access to advanced layers for layout, sizing, alignment, typography,
tables, effects, and beyond...

Each category comprises a minimum of two layers. While the topmost layer is
typically utilized, this guide will begin with the foundational layers and
progress upward.

<br />

## The Base Layer
Let’s take *flexbox* as an example, the <ins>base layer</ins> is what you are
already using, whether you write vanilla CSS, CSS in JS, or use tailwind
classes. The same rules still apply.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/figg1-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/figg1-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/figg1-light.png" style="max-width: 100%;">
    </picture>
</p>

<br />

You have to learn it before you use it, and every time you use it, you have to
constantly think about the *main axis*, the *cross axis*, and how they change.
How do they affect *cross start*, *cross end*, *cross size*, and other
properties. This may be great for beginners, but when you are more advanced,
it becomes inefficient and a waste of time.

Does **Layerzs** offer something better?

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

In the first layer, we can use *flexes*, it simplifies things by removing
unnecessary details and extra work from the base layer.

believe or not, that tiny API is capable of doing more than what *flexbox*
is able to but most importantly is that it is predictable and easier to reason
about. and that's what we are going to see next.

<br />

### Alignments
*flexes* is straightforward. It operates with only two fixed axes: These axes
don't change, which makes understanding things very simple.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig3-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig3-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig3-light.png" style="max-width: 100%;">
    </picture>
</p>

For example, if you want to center an item along the X-axis, it will be
centered along the X-axis regardless of whether the *flex direction* is set to
row or column, regardless of whether the direction is reversed or flipped or
wherever. **it will always be centered along the X-axis**.

Unlike *flexbox* where many behaviours depend on other factors, and you have
to always keep that in mind, *flexes* is the opposite the API is like
hard set rule, which makes thinking and reasoning about things super easy.
Let's use the *center* API and see how it behaves when used in two different
scenarios.

<br />

<ins>Note:</ins> *center* is the same as applying *centerX* and *centerY* at
the same time, meaning that it will center along the X-axis and the Y-axis.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig4-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig4-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig4-light.png" style="max-width: 100%;">
    </picture>
</p>

By default the API will target the **container**, in order to target an
**item**, we add *i* to any method we want so instead of using *center*
we'll use item center *iCenter*.

Let's see how alignment works when applied to an item instead.


<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig5-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig5-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig5-light.png" style="max-width: 100%;">
    </picture>
</p>

That's interesting, **how's *flexes* capable of centering an item along
the X-axis when direction is row?**

Under the hood, *flexes* uses the number of items within the container to
determine if the centering can happen.


<br />

### Order
By default *flexes* manages the ordering of the items and it allows you
to shift the order of a specific item if you need to by using *iShift*.


<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig6-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig6-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig6-light.png" style="max-width: 100%;">
    </picture>
</p>

<br />
<br />

However sometimes, you might need to set a custom ordering, imagine
we want to achieve something like the following:

```css
.item:nth-child(3n+1) { order: 1; }
.item:nth-child(3n+2) { order: 2; }
.item:nth-child(3n)   { order: 3; }
```

We can easily create a custom order and pass it to *flex*.

```js
const orders = {
  // "start, step": order
  "1, 3": 1,
  "2, 3": 2,
  "3, 3": 3,
};
```

That's great, however in the second layer there's no way to set a custom
ordering or even think about ordering because you get access to even a higher
level API that helps you achieve bigger things and not waste time with low
level things.

To learn more, please take a look at the [API](./flexesAPI.md)


<br />

### Orientation


<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig7-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig7-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig7-light.png" style="max-width: 100%;">
    </picture>
</p>

The current version of *reverse* reverses the direction however it keeps the
layout the same way it was before so it looks like we just reversed the item
orders. in order to only reverse the direction, you can use *flip ("dir")*, or
just *flip* if wrap is on.

**Note:** Take 5 seconds, and [vote &uarr;](https://github.com/cipherlogs/layerzs/discussions/1) for the upcoming API changes.

<br />

### Spacing
To globally manage spacing from the **container**, you can use *autoGap*.
You have 4 modes to choose from *none*, *around*, *between*, *even*, and a
fallback value to apply if the mode can't be used.

+ *autoGap ("around")*
+ *autoGap ("even", "gap-2")*
+ *autoGap ("none", "gap-x-2 gap-y-2")*

If the fallback is ommitted a gap of `gap-2` will be applied.



<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig8-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig8-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig8-light.png" style="max-width: 100%;">
    </picture>
</p>


In order to control the spacing of each **item**, you can use *iSpace*. to
instruct it to do two things

+ what to do when there's available space left
    + Inject that space inside the item.
    + Put that space after, before or around the item.

+ what to do when there's no space left





<br />
<br />

## The second layer
WIP

