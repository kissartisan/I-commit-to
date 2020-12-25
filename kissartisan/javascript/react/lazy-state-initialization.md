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
