# DateJson

The purpose of the DateJson code is to allow us to transport Date data from the server to the Client. This is important because database models often include date data like `createdAt` and `updatedAt` fields.

DateJson allows adds `Date` support to JSON by encoding it as `${ $date: number }`.

The library is inspired by EJSON from Meteor, but with two differences:

1. It is lightweight and supports only the Date format

2. It preserves types during conversion giving us type safety which is valuable for API calls.

The purpose of the library is to allow us to more easily work with database records which often contain `Date` types in them. This library allows dates to be sent to the client without manually finding and transforming them from/to date formats.

It works by converting any dates to `{ $date: number }` where `number` is the number of ms since epoch as retrieved by `date.getTime()`.

It does this in the method `DateJson.toJsonValue`. It reverse this in `DateJson.fromJsonValue`
