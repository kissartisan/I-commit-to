## When to use Ref vs State
It's way better to use **React.useRef** and this special ref prop to get access to the DOM node that React creates for this element.
Keep in mind that React.useRef gives you an object that has a current property on it, and that current property is mutable.

*Anytime you want to maintain a reference to something and you want to be able to make changes to that thing without triggering a rerender.*

If you want to trigger a rerender then you should probably just use **state** instead.

But in some case, we just want to have an object where its current value will be mutated to the div that React creates the particular element. And that's when the **ref** comes into play.
