# CCSS

A minimal set of conventions for CSS class naming in a modern apps.

CCSS a hybrid methodology, designed and tailored for SPA apps or any framework where componentization is heavily used. It's the result of experimenting on different ideas and reaching a minimal system that proves most maintainable when building huge apps.

It prefers keeping things simple and to the point, and only covers the most fundamental naming rules within a component, leaving the rest for the consumer. The ultimate focus is on maintainability and ease of visual debugging (i.e telling where each class comes from and what it's doing from its name).

## Conventions

Conventions are tied directly to the component. We have only two types of classes: elements and modifiers.

### Elements

Elements are actual html elements. This can be the component itself (or its root html element as in React), or a component child (i.e any html element in the component's template).

#### Component

Use "component-name" for the main component class.

**Examples:**
- "my-component" for a `MyComponent` component

#### Component child

A component child is an html element in its own template. This means that elements deeper inside other components aren't considered, as they belong to their own component.

Use an underscore after the base to mark a child element: "component-name_element".

Underscore is only allowed once in a class name, and it always follows the component's class name.

**Examples:**
- "my-component_content"
- "my-component_content-text"

_Why?_ This makes it clear at a glance that this class lives in "some-component", and that it's on an element inside this component's template called "container-text".

### Modifiers

Modifiers are the equivalent of a boolean flag on elements. It's either on (class is added) or off (class is removed).

For the class naming, use a double dash after the base to mark a modifier class: "[element-class]--[modifier]". A modifier always modifies an element, which can be a component or an element in its template.

**Examples:**
- "my-component--disabled": Target this class when you want to modify the "my-component" element for disabled styles.
- "some-component_text--disabled": Target this class when you want to modify

If you're using SCSS or similar, it's recommended to use the `&--[state]` syntax to target this in CSS.

### Prefixing

Optional: Add a constant prefix (such as "app-*") to all component class names in all of the application. This will act as namespacing.

_Why?_ Avoids potential naming clashes between your own component and other 3rd party CSS your app uses. Do this especially if your components have generic/common names.

In case of shared components, consider using a prefix such as "s-*" to make it easier to tell if the component is shared or specific in usage.
