# StyleGuide for mmart_SG
 
This repository was created by the command `npx styleguidist build`, which generated this folder that contains
html materials that documents and presents selective components of the application `mmart`.

The processing of applying StyleGuidist to the app:

1. You have to install StyleGuidist: `npm install react-styleguidist`.

2. Add the file `styleguide.config.js`. This file has a filter that tells StyleGuidist where to find the components to document.
In this rendition, only `.jsx` in `src/components` are included.

3. For each `.jsx` to be documented, do the following (using `src/components/coll-item.jsx` as example:

3.1 First refer to this line `export const CollItem = ({objId, goDele, goPick}) => {`.  This line tells there are three props.

3.2 Add this line to the top `import PropTypes from "prop-types";`, this is needed to define the props passed to the component.

3.3 Add these lines to the bottom to define the type of each prop.
```jsx
CollItem.propTypes = {
  objId: PropTypes.string,
  goDele: PropTypes.func,
  goPick: PropTypes.func
};
```
The other variations are:
```jsx
variant: PropTypes.oneOf(["primary", "outline"]),
value: PropTypes.number,
```
for strings that have a set of valid values, and for numeric props.

3.4 Optionally add comments just before the `export` statement:
```jsx
import { ButtonAdd } from "./button-add";

/**
 * This component represents an item on a page of items.
 * - objId is a string that is the access key to the object.  This is key 
 *   is appended to a URL to fetch further details.
 * - goDele is a function that when present, will cause a bin icon to be displayed, which 
 *   when clicked should remove the item from the user's collection.
 * - goPick is a function that when present, will cause a download icon to be displayed, which 
 *   when clicked should included the item into the user's collection.
 * Usually, only one of goDele or goPick is present.
 */

export const CollItem = ({objId, goDele, goPick}) => {
```

4. Other files that may be related.

4.1 `tailwind.config.js`

4.2 `craco.config.js`

5. While making the above changes, it is necessary to necessary to bring up StyleGuidist using `npx styleguidist server` 
which will constantly refresh the StyleGuidst display base on changes to the app.  Only when all changes are finalised, 
the command `npx styleguidist build` can then be used to create this `styleguide/` folder.
