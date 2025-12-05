---
{"dg-publish":true,"permalink":"/01_Reference/react notes/","title":"React key concepts","tags":["react","webdev","programming"],"created":"2025-12-05T03:27:51.077+01:00"}
---


# React key concepts

## short notes

- CSS styles for each component will apply to whole page. It is possible to style local scope of each component but by default CSS is not scoped and will apply to whole page.
- Each component will have built in `props` object. React automatically provides a special, implicit prop named "children" to any custom component. It represents whatever is rendered between opening and closing tags of each component. If there is a single child `props.children` will be that child (a string, element, component... etc). If there are multiple children, it will represent an array of those children. It will not render `innerHTML` elements, instead it will render plain text. React has a special prop called `dangerouslySetInnerHTML` for when you absolutely need to inject raw HTML into component.
- When writing React code, remember! Vanilla javascript is **imperative** but when working with React you should let React do the work and write in **declarative** style.

```javascript
// imperative javascript
document.querySelector("button").addEventListener("click", eventHandlerFunction );
```

```jsx
// declarative jsx
<button onClick={ eventHandlerFunction }> { props.children } </button>
```

- Event handler functions can be defined inside component function. The advantage of doing so is having access to the component's props and state.

```jsx
export default function TabButton({ children }) {
    function handleClick() {
        console.log("Hello World!");
    }

    return (
        <li>
            <button onClick={handleClick}>{children}</button>
        </li>
    );
}
```

## read more

- [react.dev](https://react.dev/learn) - official documentation
- [[01_Reference/javascript notes\|javascript notes]] - personal note
- [[03_Literature_notes/react key concepts - an in-depth guide\|react key concepts - an in-depth guide]] - personal note
- [[03_Literature_notes/learning react - modern patterns 2nd edition\|learning react - modern patterns 2nd edition]] - personal note
- [[03_Literature_notes/modern fullstack react projects\|modern fullstack react projects]] - personal note
- [youtube.com/video](https://www.youtube.com/watch?v=-XKvVyC6si0) - "Understanding React: The first 6 hours" by Tony Alicea
- "React key concepts - An in-depth guide to React's core features" - book by Maximillian Schwarzmuller
