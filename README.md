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
    <a href="https://twitter.com/cipherlogs"><img alt="X (formerly Twitter) Follow" src="https://img.shields.io/twitter/follow/cipherlogs?style=flat"></a>
    <img src="https://img.shields.io/badge/work_is_still_in_progress-WIP-green?style=flat" alt="WIP">
    <img src="https://img.shields.io/github/license/cipherlogs/layerzs" alt="License">
</p>

------

<br />

## How does it work?
Layerzs offers sophisticated layers for various tasks such as layout design,
sizing, alignment, typography, table creation, effects, and more. To get a
better understanding of how Layerzs is constructed, let's use flexbox as an
example:

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://layerzs.tixte.co/r/fig0-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://layerzs.tixte.co/r/fig0-light.png">
     <img alt="Tailwind CSS" src="https://layerzs.tixte.co/r/fig0-light.png" style="max-width: 100%;">
    </picture>
</p>


+ **API Layers:**
    + **Layer1:** This is a basic layer that supports the next layer. You usually won't use it directly, but it's necessary for Layer2 to function.

    + **Layer2:** This is a more advanced layer built on Layer1. It lets you create layouts quickly and easily. It can switch between CSS grid and CSS flexbox automatically, so you don't need to worry about the details. This combination creates a powerful and universal API.

    + **Niche Layers:** These are built on Layer2. They're used to build components and more complex user interfaces.


> [!CAUTION]
>
> Each new layer in the API is designed to replace the previous one. This
> means if you're using Layer2, you won't need to use Layer1 or the base
> layer. This is a key principle of our design. If a new layer doesn't make
> the previous one obsolete, it's not a good abstraction. That's why our
> top-level components are built with Layer2. They're not bloated like
> other UI libraries, and they're easy to read, edit, and modify.


**Note:** Please read the [discussion](https://github.com/cipherlogs/layerzs/discussions/1) and vote for what you believe is best.

<br />

**Next, we'll compare using flexes to using flexbox. Keep in mind that flexes is just Layer1. In practice, you'll be using Layer2 and above.**

<br />
<br />

## The Base Layer
The base layer is what you're already using, whether you write vanilla CSS,
CSS in JS, or use tailwind classes. The same rules still apply.

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

### Getting Started
In the first layer, we'll be using *flexes*. This simplifies things by
removing unnecessary details and extra work from the base layer.

Start by installing *flexes*:

```bash
$ npm -i flexes
```

This version of flexes uses tailwind as the **base layer**, so ensure tailwind
is installed. Then, import and initialize flexes:

```js
import flex from "flexes";

function App() {
  const {cls, f} = flex ();

  return (<></>);
}
```

Here, `f` contains the entire flexes API, and `cls` is a utility that helps us
manage and run all tailwind classes and layerzs utils.


#### cls

`cls` removes tailwind duplicates and conflicts, and helps organize long
tailwind class sets. It can also include variables and functions.

```js
className={cls("hover:p-2 hover:p-4")} // → 'hover:p-4'
```

It also assists in organizing lengthy sets of Tailwind classes.

Instead of this:

```js
className="relative inline-flex items-center justify-center rounded-md p-2 text-gray-400 hover:bg-gray-700 hover:text-white focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
```

You could break it down to small sets that makes sense to you

```jsx
className={cls(
  "relative inline-flex items-center justify-center",
  "rounded-md p-2 text-gray-400",
  "hover:bg-gray-700 hover:text-white",
  "focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white",
)}
```

You can also include variables and functions,

```jsx
const display = "flex";
const background = (color = "black") =>
    color === "black"
    ? "bg-black"
    : "bg-white";

...

<div className={cls(display, background,)}></div>
<div className={cls(display, background("white"),)}></div>
<div className={cls(display, "border border-dashed")}></div>
```

### Creating a container
To create a flex box container using flexes, label the parent as a box and its
children as items.

```jsx
<>
  <div className={cls(f.box)}>
    <div className={cls(f.item)}>Child 1</div>
    <div className={cls(f.item)}>Child 2</div>
  </div>
</>
```

#### Box API
> **box(direction, wrap, orders)**
>
> + direction (*optional*): "row", "col" (*default* = "row")
>
> + wrap (*optional*): enable wrap (*default* = false)
>
> + orders (*optional*): (*default* = items are ordered automatically)

### Dealing with nested containers
Often, you'll need to create a container that's also an item. In this case,
you need to help flexes understand the nesting level you're at. Simply use
`f.lastItem`.

```jsx
<>
  <div className={cls(f.box)}>
    <div className={cls(f.item, f.box)}>
      <p>Child 1</p>
      <div className={cls(f.item)}>Sub child 1</div>
      <div className={cls(f.lastItem)}>Sub child 2</div>
    </div>

    <div className={cls(f.lastItem)}>
      <p>Child 2</p>
    </div>
  </div>
</>
```

**Note:** to use this featuer, switch to the *dev* branch.

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

```jsx
<>
  <div className={cls(f.box, center)}>
    <div className={cls(f.item)}>Child 1</div>
    <div className={cls(f.item)}>Child 2</div>
    <div className={cls(f.item)}>Child 2</div>
  </div>
</>
```

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


```jsx
<>
  <div className={cls(f.box)}>
    <div className={cls(f.item, f.iCenter(3))}>Child 1</div>
    <div className={cls(f.item)}>Child 2</div>
    <div className={cls(f.item)}>Child 2</div>
  </div>
</>
```

That's interesting, flexbox doesn't have `justify-self` **how's *flexes*
capable of centering an item along the X-axis when direction is row?**


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


```jsx
<>
  <div className={cls(f.box)}>
    <div className={cls(f.item, f.iShift(2))}>Child 1</div>
    <div className={cls(f.item)}>Child 2</div>
    <div className={cls(f.item)}>Child 2</div>
  </div>
</>
```

#### iShift API
> **iShift(n)**
>
> + n: (*default* = 0)
>
>   + if n > 0 -> shift to the right by n (if direction is col, it will shift
>       to the bottom)
>
>   + if n < 0 -> shift to the left by n (if direction is col, it will shift
>       to the top)
>
>   + if n == 0 -> no mouvement


Sometimes, you might want to set a custom order. Here's an example:

```css
.item:nth-child(3n+1) { order: 1; }
.item:nth-child(3n+2) { order: 2; }
.item:nth-child(3n)   { order: 3; }
```

You can create a custom order and use it with flex.

```jsx
const orders = {
  // "start, step": order
  "1, 3": 1,
  "2, 3": 2,
  "3, 3": 3,
};

<div className={cls(f.box("col", true, orders))}>...</div>
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

```jsx
<>
  <div className={cls(f.box, flip)}>
    <div className={cls(f.item)}>Child 1</div>
    <div className={cls(f.item)}>Child 2</div>
    <div className={cls(f.item)}>Child 2</div>
  </div>
</>
```


#### flip API
> **flip(mode)**
>
>  it will flip the direction, but only if wrap in on, if wrap is off and you
>  want to flip the direction, use `flip("dir")`
>

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


```jsx
<>
  <div className={cls(f.box, f.autoGap)}>
    <div className={cls(f.item)}>Child 1</div>
    <div className={cls(f.item)}>Child 2</div>
    <div className={cls(f.item)}>Child 2</div>
  </div>
</>
```

#### autoGap API
> **autoGap(mode, fallback)**
>  + mode:
>    + "none"
>    + "around"
>    + "even"
>    + "between"
>
>  + fallback: any value you want using tailwind classes (*default* gap-1)


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


```jsx
<>
  <div className={cls(f.box)}>
    <div className={cls(f.item)}>Child 1</div>
    <div className={cls(f.item, f.iSpace("inject"))}>Child 2</div>
    <div className={cls(f.item)}>Child 2</div>
  </div>
</>
```

#### iSpace API
> **iSpace(arg1, arg2)**
>  + arg1: what to do when there's available free space
>    + "inject"
>      + iSpace("inject"), or explicitly add the amount iSpace("inject", 4)
>
>    + "put"
>      + "putBefore"
>      + "putAfter"
>      + "putAround"
>
>  + arg2: what to do when there's no avilable free space (*default* shrink)
>    + control the amount of shrinking
>      + `iSpace("inject", 1, 2)`
>      + `iSpace("putAround", 2)`
>
>    + stop shrinking
>      + `iSpace("inject", 1, 0)`
>      + `iSpace("putAround", 0)`
>

<br />

This compact API lets you do everything you could with flexbox, and more.

Keep in mind, the next layer built on top of this should only use Layer1 and
should render this layer obsolete. You've seen how simple and seamless it is
to work with flexbox using Layer1. **But what about Layer2, which is the layer
you'll actually be using?**

<br />
<br />

## What's coming next?
Star this repository to receive updates on upcoming changes and join the discussion! [discussion](https://github.com/cipherlogs/layerzs/discussions/1)

Please vote for what you believe is best.

