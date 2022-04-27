# DateJson

A less than 1KB library to encode and decode dates in standard JSON.

Use it to add Date support to APIs.

Send database records that contain dates without having to manually transform them.

```ts
const json = DateJson.toJSON({ createdAt: new Date() })
// --> { createdAt: { $date: 1519211811670 } }

const jsonWithDates = DateJson.fromJSON(json)
// --> { createdAt: anInstanceOfADateObject }
```

## Features

- Lightweight: Less than 1 KB
- JSON support: Transform to/from standard JSON
- string support: Transform to/from string (stringify/parse)
- End-to-end TypeScript: Keeps type integrity through transformations
- Type Safety: Ensures input values are type safe

## End-to-End TypeScript

Keeps type integrity during encode/decode enabling type safety in API calls.

```ts
const json = DateJson.toJSON({ createdAt: new Date() })
// --> { createdAt: { $date: 1519211811670 } }
type MyJson = typeof json
// --> type: { createdAt: { $date: number }}

const jsonWithDates = DateJson.fromJSON(json)
// --> { createdAt: anInstanceOfADateObject }
type MyJsonWithDates = typeof jsonWithDates
// --> type: { createdAt: Date }
```

## Inspiration

The format is inspired by EJSON from Meteor with these differences:

- laser focused on just adding dates
- preserves type integrity through transformations
- aggressively lightweight
