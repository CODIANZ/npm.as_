# as_

## description

Initialize the object type-safely in the right section.

You can easily and safely initialize the object as a return value.

## usage

Suppose there is such a type.

```ts
/** sample type */
type Result = {
  status: "ok" | "ng",
  code: number;
};
```

```ts
/** explicit */
function foo() : Result {
  return {
    status: "ok",
    code: 100
  };
}

/** inference */
function bar() {
  const p: Result = {
    status: "ok",
    code: 100
  };
  return p;
}

/** damm code... */
function baz() {
  return {
    status: "cancel", /* <- no error!! */
    code: "what?",    /* <- no error!! */
    bad: true         /* <- no error!! */
  } as Result;
}

/** inference with as_ */
function hoge() {
  return as_<Result>({
    status: "ok",
    code: 100
  });
}
```


