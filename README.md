![checkboxNav]
(http://demo.sklein-medien.de/fileadmin/Demo/Images/checkboxNav-logo-pos.svg =250x70)

# checkboxNav

## A CSS-only, Sass-built responsive multi-level navigation

This menu uses the **Checkbox Hack** and is based on [this tutorial by W3Bits](http://w3bits.com/css-responsive-nav-menu/), but completely rebuilt with Sass. Also, unlike the W3Bits version, checkboxNav does not rely on two html elements for the drop icon, but only needs the label.

## Features
- multi-level navigation
- no JavaScript necessary
- responsive
- easy customization through Sass variables
- BEM-like naming convention with unique names - no hassle with classes like _'nav'_ or _'menu'_ when using your favourite CSS framework
- choose between hamburger icon or toggle-bar
- 2 example themes

## FAQ
### How does it work?

We hide the actual checkboxes, but show labels that activate or deactivate them. When a checkbox is checked by the assigned label, we use the [sibling selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Adjacent_sibling_selectors) `+` to style the element that is immediately following the checkbox. This way, we can open or close the navigation in mobile view. 

**CSS:**

```
.cbnav input[type="checkbox"]:checked + .cbnav__lvl--sub {
    display: block;
}
```

**HTML:**

```
<a class="cbnav__link--first" href="#">A link
    <label class="cbnav__label" for="id1"><span class="cbnav__arrow"></span></label>
</a>
<input type="checkbox" id="id1">
<ul class="cbnav__lvl--sub">
    <li class="cbnav__item"><a class="cbnav__link--sub" href="#">A link</a></li>
    <li class="cbnav__item"><a class="cbnav__link--sub" href="#">A link</a></li>
</ul>
```

On desktop we use the common hover effect to show the navigation. Although the same label with drop icon is shown, it has no effect when you click on it to activate/deactivate the checkboxes.

### How do I use it?

- `_checkboxNav.vars.scss` contains all variables that can be customized
- `_checkboxNav.menu.scss` includes the navigation's functionality

To adapt checkboxNav to your needs you can create a new Sass file, load the variables, then alter some of them and finally import `checkboxNav.menu`.

If you want to make further changes like adding borders, import another file which contains the modifications. See `demo.bar.scss` as an example:

```
@import "_checkboxNav.vars";


// override default values:
$cbn-color-link-first: #424254;
$cbn-color-text-first: #fff;
$cbn-color-link-first-hover: #64908A;
$cbn-color-text-first-hover: #fff;

$cbn-color-link-sub: $cbn-color-link-first;
$cbn-color-text-sub: $cbn-color-text-first;
$cbn-color-link-sub-hover: $cbn-color-link-first-hover;
$cbn-color-text-sub-hover: $cbn-color-text-first-hover;

$cbn-color-link-active: #64908A;
$cbn-color-text-active: #fff;

$cbn-color-label: #a02a3c;
$cbn-color-toggle: $cbn-color-link-first;


@import "checkboxNav.menu";
@import "themes/theme.bar";
```