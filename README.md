# DateJson

A lightweight (794 bytes) library to add Date support to JSON APIs.

Enables APIs to send database records that contain dates without having to manually transform them.

```ts
import { DateJson } from "@portive/date-json"

const json = DateJson.toJSON({ createdAt: new Date() })
// --> { createdAt: { $date: 1519211811670 } }

const jsonWithDates = DateJson.fromJSON(json)
// --> { createdAt: anInstanceOfADateObject }
```

## Features

- Lightweight: 795 bytes
- JSON: Transform to/from JSON
- String: Transform to/from string (stringify/parse)
- TypeScript: Keeps type integrity through transformations

## TypeScript

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

## No `$date` Key Allowed

The key `$date` is prohibited in `toJSON` like in `DateJson.toJSON({ $date: 'today' })`. This will throw the error `Object with key $date is invalid`.

This is intentional and is there to prevent confusion. Am I looking at a DateJson object or a plain JSON object with `$date` in it?
