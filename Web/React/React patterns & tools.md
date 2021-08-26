# React patterns & tools

## State management

When using `useReducer()`, use [Immer](https://hswolff.com/blog/level-up-usereducer-with-immer/) to make it much more succinct and readable.

This is a great guide, advocating for using context only when prop drilling becomes unsustainable: [Application State Management with React](https://kentcdodds.com/blog/application-state-management-with-react)

Other research on context + reducers:

- https://medium.com/suyeonme/using-usecontext-and-usereducer-together-lets-create-redux-like-global-state-in-react-87470e3ce7fa
- https://stackoverflow.com/questions/64938820/usereducer-and-usecontext-dispatch-doesnt-work-in-onclick-function
- https://hswolff.com/blog/how-to-usecontext-with-usereducer/
- https://twitter.com/dan_abramov/status/1102008543014735873

## Connecting with APIs

See [Building Your Own Hooks](https://reactjs.org/docs/hooks-custom.html).