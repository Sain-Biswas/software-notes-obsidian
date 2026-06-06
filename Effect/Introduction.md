## What is an `Effect`?

- Something brought about by a cause or agent
- Side effects?
- The `Effect` type

> An Effect is a description of a program that is lazy and immutable

### Functions

In general a `function` is represented as:

```typescript
type Function<Args, T> = ( ...args: Args ) => T;
```

We can create `safer function` represented as:

```typescript
type SaferFunction<Args, T, E> = ( ...args: Args ) => T | E;
```

But here it can be discriminate between errors and values. And we need to manually check for error and values.

### Effects

```typescript
type Effect<Value, Error = never, Requirement = never> = /* unimportant */;

declare const foo: Effect<number, never>;
// also the same as Effect<number>

declare const bar: Effect<number, Error>;
```

`Error` and `Requirement` are by default never.

Samples:
```typescript
declare const getUser: Effect<User, NotFoundError, DataBase>;

declare const updateEmail: Effect<
	User,
	NotFoundError,
	DataBase | Logger | Telemetry
>;
```
