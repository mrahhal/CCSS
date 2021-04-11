# CCSS

A minimal set of conventions for CSS class naming in modern apps.

CCSS is designed and tailored for SPA apps or any framework where componentization is heavily used. It's the result of experimenting on different ideas and reaching a minimal system that proves most maintainable when building huge apps.

It prefers keeping things simple and to the point, and only covers the most fundamental naming rules within a component - the skeleton of the application, leaving the rest of the details for the consumer.

The ultimate focus is on maintainability and ease of visual debugging, i.e telling where each class comes from and what it's doing from its name, while avoiding clashes with other parts of the app.

## Conventions

Conventions are tied directly to the component. We have only two types of classes: elements and modifiers.

### Elements

Elements are actual html elements. This can be the component itself (or its root html element as in React), or a component child (i.e any html element in the component's template).

#### Component

Use "component-name" for the main component class.

**Examples:**
- "my-component" for a `MyComponent` component

#### Component child

A component child is an html element in its wrapping component's template. This means that elements deeper inside other components aren't considered, as these belong to their own component.

Use an underscore after the base class to mark a child element: "component-name_element".

Underscore is only allowed once in a class name, and it always follows the component's class name.

**Examples:**
- "my-component_content"
- "my-component_content-text"

_Why?_ This makes it clear at a glance that this class lives in "my-component", and that it's on an element inside this component's template called "container-text".

### Modifiers

Modifiers are the equivalent of a boolean flag on elements. It's either on (class is added) or off (class is removed). It's great for classes that change things depending on the state of the component. We use modifiers to modify elements (the other kind of classes we have).

Use a double dash after the base class to mark a modifier class: "element-class--modifier".

**Examples:**
- "my-component--disabled"
- "my-component_text--larger"

If you're using SCSS or similar, it's recommended to use the `&--modifier` syntax to target modifier classes.

### Prefixing

Optional: Add a constant prefix (such as "app-*") to all component class names. This will act as namespacing.

_Why?_ Avoids potential naming clashes between your own component and other 3rd party CSS your app uses. Do this especially if your components have generic/common naming sense.

In case of shared components, components that are generic in nature, consider using a prefix such as "s-*" to make it easier to tell that this component is shared and not a specific component that belongs to some page.
