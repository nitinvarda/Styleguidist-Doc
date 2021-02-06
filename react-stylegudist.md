<h2>React-Styleguidist Documentation</h2>

<h3>Introduction :</h3>

`react-styleguidist` generates documentation for your components based on the comments in your source code, propTypes declarations, and Readme files.

<h3>Installation :</h3>

To install we need to run the following command
```
npm install react-styleguidist

```


<h3>Configuration :</h3>
After installing we need to do some configuration to tell stylguidist where to search files for documenting.


we need to make a new file with name `styleguide.config.json`
```
module.exports = {
    components: 'src/components/**/*.js',
};
```

The above code is showing stylguidist to look into src/components/ and parse any file with the 
`/** */` syntax and it will parse .md files with either `component.md` or `readme.md`

Next we need to add two commands to `package.json` 
```
...
"scripts":{
    "styleguide": "styleguidist server",
    "styleguide:build": "styleguidist build"
}
...
```

<h3>Usage :</h3>

After the configuration we  need to need to comment the components we need to document with 
`/** */` and `readme.md` .

Later we need to run the following command
```
npm run styleguide

```

It will run the styleguide server on localhost  and checks for any errors during parsing files.

If there are no errors  we can proceed to next step 

Now we need to run build command 
```
npm run styleguide:build

```
With this command `react-stylguidist` will generate docummentation folder in your `src/` directory in the name of `styleguide` which contains `html` file.

<h3>Example :</h3>

example is taken from the official website of `react-styleguidist`


```
import React from 'react'
import PropTypes from 'prop-types'
/**
 * General component description in JSDoc format. Markdown is *supported*.
 */
export default class Button extends React.Component {
  static propTypes = {
    /** Description of prop "foo". */
    foo: PropTypes.number,
    /** Description of prop "baz". */
    baz: PropTypes.oneOfType([PropTypes.number, PropTypes.string])
  }
  static defaultProps = {
    foo: 42
  }

  render() {
    /* ... */
  }
}

```

and readme.md 

```
React component example:

```js
<Button size="large">Push Me</Button>
``

You can add a custom props to an example wrapper:

```js { "props": { "className": "checks" } }
<Button>I’m transparent!</Button>
``

Or add padding between examples in a block by passing the `padded` modifier:

```jsx padded
<Button>Push Me</Button>
<Button>Click Me</Button>
<Button>Tap Me</Button>
``

Or disable an editor by passing a `noeditor` modifier:

```jsx noeditor
<Button>Push Me</Button>
``

To render an example as highlighted source code add a `static` modifier:

```jsx static
import React from 'react';
``

Examples with all other languages are rendered only as highlighted source code, not an actual component:

```html
<Button size="large">Push Me</Button>
``

Any [Markdown](http://daringfireball.net/projects/markdown/) is **allowed** _here_.

```

<h3>Output :</h3>

![Image](https://raw.githubusercontent.com/nitinvarda/Styleguidist-Doc/master/ButtonComponent.png)







