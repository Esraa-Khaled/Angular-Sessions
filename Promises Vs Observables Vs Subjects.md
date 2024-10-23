# Promises

### What are Promises?
Promises represent a single asynchronous operation that may or may not be completed in the future. They provide a cleaner alternative to callbacks, allowing developers to write more readable and maintainable asynchronous code.

### How do Promises work?
When a promise is created, it is in one of three states: pending, fulfilled, or rejected. Once a promise is resolved (either fulfilled or rejected), it transitions to a final state and stays there. Promises can be chained using .then() and .catch() methods to handle successful resolution or errors, respectively.

### **$\color{Aquamarine}{Pros:}$**
- __Simplicity:__ Easy to understand and use for handling single asynchronous operations.
- __Chaining:__ Supports chaining with .then() and .catch() for sequential asynchronous operations.
- __Error Handling:__ Provides straightforward error handling with .catch().

### **$\color{Bittersweet}{Cons:}$**
- __Single Value:__ Can only handle a single value or error.
- __Non-cancelable:__ Once started, a promise cannot be canceled.
- __Eager Execution:__ Executes immediately upon creation, which can lead to unnecessary operations if not needed.

> [!TIP]
> __Single Value:__ Promises handle a single asynchronous event at a time. \
> __Eager:__ They start executing immediately upon creation. \
> __Non-cancelable:__ Once a promise is initiated, it cannot be canceled. \
> __Syntax:__ Uses .then() for success and .catch() for errors.


___

# Observables

### What are Observables?
Observables are a powerful way to handle asynchronous data streams in Angular applications. They enable developers to work with multiple values over time, offering features like cancellation, composition, and transformation.

### How do Observables work?
An observable represents a stream of data that can emit multiple values asynchronously. Observables can be created from various sources such as events, timers, promises, or even other observables. Subscribers can then listen to these streams and react accordingly to emitted values.

### **$\color{Aquamarine}{Pros:}$**
- __Multiple Values:__ Can emit multiple values over time.
- __Lazy Execution:__ Only starts emitting values when subscribed to.
- __Cancelable:__ Subscriptions can be canceled to stop receiving values.
- __Operators:__ Rich set of operators for transforming, filtering, and combining streams of data.

### **$\color{Bittersweet}{Cons:}$**
- __Complexity:__ Can be more complex to understand and use compared to promises.
- __Memory Leaks:__ Improperly managed subscriptions can lead to memory leaks

> [!TIP]
> __Multiple Values:__ Observables can emit multiple values over time. \
> __Lazy:__ They do not start emitting values until they are subscribed to. \
> __Cancelable:__ Subscriptions to observables can be canceled. \
> __Syntax:__ Uses .subscribe() to handle emitted values and errors. 
___

# Subjects

### What are Subjects?
Subjects in Angular are a special type of observable that allows both subscribing to and emitting values. They act as both an observer and an observable, making them particularly useful for multicasting values to multiple subscribers.

### How do Subjects work?
Subjects have the ability to maintain a list of observers and emit values to all subscribers. They come in different flavors such as ```Subject```, ```BehaviorSubject```, ```ReplaySubject```, and ```AsyncSubject```, each catering to specific use cases. Subjects provide a way to broadcast values to multiple parts of an application, facilitating better communication between components and services.

### **$\color{Aquamarine}{Pros:}$**
- __Multicasting:__ Allows multiple subscribers to share the same observable execution.
- __Emit Values:__ Can emit new values to subscribers using .next().
- __Versatile:__ Acts as both an observer and an observable.
  
### **$\color{Bittersweet}{Cons:}$**
- __State Management:__ Requires careful management to avoid issues with state consistency.
- __Hot Observable:__ Starts emitting values immediately, which might not always be desirable

>[!Tip]
> __Multicasting:__ Subjects allow multiple subscribers to share the same observable execution. \
> __Emit Values:__ They can emit new values to their subscribers using .next(). \
> __Types:__ There are different types of subjects, including ```BehaviorSubject```, ```ReplaySubject```, and ```AsyncSubject```.

## BehaviorSubjects

### **$\color{Aquamarine}{Pros:}$**
- __Initial Value:__ Requires an initial value and always emits the current value to new subscribers.
- __State Management:__ Useful for maintaining and sharing state across components.

### **$\color{Bittersweet}{Cons:}$**
- __Memory Usage:__ Can consume more memory as it stores the latest value.
- __Initial Value Requirement:__ Always needs an initial value, which might not be suitable for all use cases

>[!Tip]
> __Initial Value:__ Requires an initial value and emits the current value to new subscribers.
> __Latest Value:__ Always holds the latest value emitted and provides it to new subscribers immediately.

## ReplaySubjects

### **$\color{Aquamarine}{Pros:}$**
- __Buffer:__ Stores a specified number of past values and replays them to new subscribers.
- __State Replay:__ Ensures new subscribers receive past values, useful for late subscribers.

### **$\color{Bittersweet}{Cons:}$**
- __Memory Usage:__ Can consume significant memory if the buffer size is large.
- __Complexity:__ Managing buffer size and window time can add complexity. \


> [!Tip]
> __Buffer:__ Can store a specified number of past values and replay them to new subscribers.
> __Replay:__ New subscribers receive the specified number of past values immediately upon subscription.

## AsyncSubject
### **$\color{Aquamarine}{Pros:}$**
- __Final Value:__ Only emits the last value to subscribers when the observable completes.
- __Completion Handling:__ Useful for scenarios where only the final result is needed.
 
### **$\color{Bittersweet}{Cons:}$**
- __Single Emission:__ Only emits one value upon completion, not suitable for continuous data streams.

>[!Tip]
> __Final Value:__ Only emits the last value to subscribers when the observable completes.
> __Completion:__ Subscribers only receive the final emitted value after the observable completes.
____

## When should I use Promises?
Promises are ideal for handling asynchronous operations that produce a single value. They are well-suited for scenarios where you only need to fetch data once and do not expect multiple emissions over time.

## When should I use Observables?
Observables shine when dealing with streams of data that can emit multiple values asynchronously. They are perfect for scenarios like event handling, HTTP requests, and real-time data updates where continuous updates are expected.

## When should I use Subjects?
Subjects are a great choice when you need to multicast values to multiple subscribers. They are particularly useful for implementing pub/sub patterns, event buses, and communication between different parts of an application.

- [Subject vs ReplaySubject vs BehaviorSubject](/https://upmostly.com/angular/subject-vs-replaysubject-vs-behaviorsubject) 
- [ReplaySubject, BehaviorSubject & AsyncSubject in Angular](https://www.tektutorialshub.com/angular/replaysubject-behaviorsubject-asyncsubject-in-angular)
