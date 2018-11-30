
# Project Reactor

## Documentation

I always find the javadocs difficult to find by searching (because 'Mono' is a common term)

https://projectreactor.io/docs

## Exception handling

When wanting to use the Flux/Mono reactive coding mechanisms, but having a method that throws exceptions:

```java
return Mono.fromCallable(() -> methodThatThrowsException(params));
```

This creates a Mono from the method that is a Mono.error if an exception is thrown

## Dealing with Mono.empty

If a default value is required when processing an empty response, the following code will result in the "someOtherMethod" call every time, because
it is being evaluated when the Mono is created, not when it resolves.

```java
return someMono
    .defaultIfEmpty(someOtherMethod());
```

If someOtherMethod is non-trivial, then this alternative should be used, which only calls "someOtherMethod" when the mono is actually empty.
This is somewhat ugly syntax, could possibly be improved in the future.

```java
return someMono
    .switchIfEmpty(Mono.defer(()->Mono.just(someOtherMethod())));
```

