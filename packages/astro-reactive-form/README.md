![package-form-cover](https://user-images.githubusercontent.com/4262489/193812095-1cffa287-e2ac-4671-b604-1e2ff2e6f19e.png)

[![version](https://img.shields.io/npm/v/astro-reactive-form)](https://www.npmjs.com/package/astro-reactive-form)
[![license](https://img.shields.io/npm/l/astro-reactive-form)](https://www.npmjs.com/package/astro-reactive-form)
[![downloads](https://img.shields.io/npm/dt/astro-reactive-form)](https://www.npmjs.com/package/astro-reactive-form)
[![dependencies](https://img.shields.io/librariesio/release/npm/astro-reactive-form)](https://www.npmjs.com/package/astro-reactive-form)

# Astro Reactive Form 🔥

Generate a dynamic form based on your data, and modify programatically.

The Reactive Form component for [Astro](https://astro.build) 🔥

_[All contributions are welcome.](https://github.com/ayoayco/astro-reactive-library/issues)_

## Installation
In your Astro project:

```
npm i astro-reactive-form
```

## Usage
Use in an Astro page:

```astro
---
import { FormControl, FormGroup } from "astro-reactive-form/core";
import Form from "astro-reactive-form";

// create a form group
const form = new FormGroup([
  {
    name: "username",
    label: "Username",
  },
  {
    name: "password",
    label: "Password",
    type: "password",
  },
]);

// set the name optionally
form.name = "Simple Form";

// you can insert a control at any point
form.controls.push(
  new FormControl({
    type: "checkbox",
    name: "is-awesome",
    label: "is Awesome?",
    labelPosition: "right",
  })
);

// you can get a FormControl object
const userNameControl = form.get("username");

// you can set values dynamically
userNameControl?.setValue("RAMOOOON");
form.get('is-awesome')?.setValue("checked");
---

<!-- 
  the `formGroups` attribute can take a single FormGroup
  or an array of FormGroup for multiple fieldsets;
  we do a single for now in this example
-->
<Form
  formGroups={form}
  submitControl={{
    type: "submit",
    name: "submit",
  }}
/>
```

# Screenshots
Result of example above:

![Screen Shot 2022-10-08 at 10 38 04 PM](https://user-images.githubusercontent.com/4262489/194726969-bdddefdf-d582-4201-a40e-3798383f03a0.png)

Example of multiple form groups:

![Screen Shot 2022-09-27 at 10 44 03 PM](https://user-images.githubusercontent.com/4262489/192631524-3139ac60-8d84-4c12-9231-fe2d49962756.png)

# Future Plans

Currently this only supports very basic form creation, but the goal of the project is ambitious:

1. Validator library for common validation scenarios
   1. Client-side validation
   1. Server-side validation
   1. validation hooks - onFocus, onBlur, onSubmit
1. Themes - unstyled, light mode, dark mode, compact, large
1. FormGroup class
   1. `statusChanges` - observable that emits the form status when it changes
   1. `valueChanges` - observable that emits the values of all controls when they change
1. FormControl class
   1. `statusChanges` - observable that emits the control status when it changes
   1. `valueChanges` - observable that emits the control value when it changes
1. Documentation website

... and so much more

_All contributions are welcome. Let's make the fastest web form component powered by Astro_
