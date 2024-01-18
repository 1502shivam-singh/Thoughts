# Overriding third party styles, global styles and CSS modules  
 
In the context of CSS Modules, the :global selector is a special syntax used to define global styles, as opposed to locally scoped styles which are the default behavior in CSS Modules.

When you use CSS Modules, class names defined in your stylesheet are automatically scoped locally to the component. This means they won't affect other elements outside of the component, preventing style conflicts across your application. However, there are situations where you might want to intentionally define global styles or override styles from a global library (like Ant Design).

Here's how you use :global:

## Defining Global Styles
If you want some styles in your CSS Module to be global (i.e., not locally scoped), you wrap them in :global.


    /* styles.module.css */


    :global {
      .global-class {
        color: red;
      }
    }

      
***
In this example, .global-class will be a global style, despite being defined in a CSS Module.

Overriding Global Styles from a Module
If you want to override styles of a global library (like Ant Design) within a CSS Module, you also use :global.

    /* styles.module.css */


    :global(.ant-btn) {
      background-color: blue;
    }


Here, you're overriding the styles of Ant Design's Button component globally, but you're doing it from within a CSS Module.

Using Global Styles in JSX
When you use global styles in your JSX, you don't reference them through the imported classNames object because they aren't transformed into unique identifiers.


    import React from 'react';
    import './styles.module.css';

    const MyComponent = () => {
      return <div className="global-class">This is a globally styled element</div>;
    };

In this example, global-class is used directly as a string, not through the classNames object, because it's a global class.

## Conclusion
The :global selector in CSS Modules is a powerful tool to control the scope of your styles, allowing you to mix local and global styling approaches in a modular and maintainable way. It's particularly useful when working with UI libraries like Ant Design, where you might need to override or extend global styles within your locally scoped modules.
