# Differences

## React vs Angular

| React | Angular |
| :--- | :--- |
| library | framework |
| JSX | typescript |
| one direction data-flow | bi-direction data-flow |
| one way data binding | two way data binding |
| component based | MVC, component based |

## State vs Props

| State | Props |
| :--- | :--- |
| change status in component | pass data |
| setState\(\) | read-only \(setProps\(\) is deprecated\) |
| data structure that starts with a default value when a component mounts | component's configuration |
| may be mutated across time, mostly as a result of user events | don't have to be just data, can also be callback functions |

## SQL vs No-SQL

| SQL | No-SQL |
| :--- | :--- |
| table based | document based |
| predefined schema | dynamic schema |
| use sql  | use unql |
| good fit for complex query | don't have standard interfaces |

## Element vs Component

| Element | Component |
| :--- | :--- |
| the tag of an object representation of a DOM node | a function or a class which optionally accepts input and returns a React element |

## Component vs Pure Component

| Component  | Pure Component |
| :--- | :--- |
|  | implement shouldComponentUpdate\(\) with shallow props and state comparison |

## Stateless Component vs Stateful Component

| Stateless Component | Stateful Component |
| :--- | :--- |
| don't have state | have state |
| can use function expression to create | must use class expression |

## Server Side Rendering vs Client Side Rendering

| Server Side Rendering | Client Side Rendering |
| :--- | :--- |
| SEO | low SEO |
| initial loading becomes faster | initial load might require more time, faster after initial load |
| good for static sites | good for web application |

## Null vs Undefined

| Null | Undefined |
| :--- | :--- |
| an assignment value | means a variable has been declared but has not yet been assigned a value |
| an object | a type itself |

## Call vs Apply

| Call | Apply |
| :--- | :--- |
| pass a single parameter | expect the second argument to be an array that it unpacks as arguments for the called function |
| call a function with a given value and arguments provided individually | call a function with a given value, and arguments provided as an array \(or an array-like object\) |

## Redux vs Flux

| Redux | Flex |
| :--- | :--- |
| one store | multiple store |
| multiple reducers | no reducer |
| implemented dispatch function | have to implement dispatch |
| library | pattern |
| implemented based on flux |  |

## Parameter vs Argument 

| Parameter  | Argument |
| :--- | :--- |
| a variable in a method definition | the data you pass into the method's parameters when a method is called |
| variable in the declaration of function | the actual value of this variable that gets passed to function |

## Presentational Component vs Container Component

| Presentational Component | Container Component |
| :--- | :--- |
| concerned with how things look | concerned with how things work |
| receive data and callbacks via props | provide the data and behavior to presentational or other container components |
| rarely have own state and do with UI state instead of data state | call flux actions and provide these as callbacks to the presentational components, often stateful |

## Class Component vs Functional Component

| Class Component | Functional Component |
| :--- | :--- |
| allow you to use additional features like local state and lifecycle hooks | receive props and renders them to the page, can use pure function |
| to enable your component to have direct access to your store and thus holds state | also called stateless, dumb or presentational components |

## setState\(\) vs forceUpdated\(\)

| setState\(\) | forceUpdated\(\) |
| :--- | :--- |
| used to update the component state with one or more new state properties | a way to force re-render of the component and its children |
| a way of mutating the state and managing view updates | doesn't mutate the state at all |

## XML vs JSON

| XML | JSON |
| :--- | :--- |
| surrounded with HTML tags | an Object |
| slower | faster |

