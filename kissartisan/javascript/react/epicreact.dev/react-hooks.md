## Lazy State Initialization
- Every time our component runs, the useState call is going to run.
- So if we have an expensive call on the useState like using localStorage or so, we need to lazily read into localStorage using a function call

Instead of this:

    const [name, setName] = React.useState(
      window.localStorage.getItem('name') || initialName
    )

We will do an inline function to call it only once when the component is rendered:

    const [name, setName] = React.useState(
      () => window.localStorage.getItem('name') || initialName
    )

Take note of the () => since that is the inline function.

Relevant URL: https://epicreact.dev/modules/react-hooks/useeffect-persistent-state-extra-credit-solution-1

## Difference of Managed State vs Derived State
- Managed State: State that you need to explicitly manage
- Derived State: State that you can calculate based on other state

That's really the definition for it, but it's hard to determine the use case.
It doesn't makes sense to me until I read this article: https://kentcdodds.com/blog/dont-sync-state-derive-it
