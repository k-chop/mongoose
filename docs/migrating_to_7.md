## Migrating from 6.x to 7.x

<style>
  ul > li {
    padding: 4px 0px;
  }
</style>

There are several backwards-breaking changes
you should be aware of when migrating from Mongoose 6.x to Mongoose 7.x.

If you're still on Mongoose 5.x, please read the [Mongoose 5.x to 6.x migration guide](migrating_to_6.html) and upgrade to Mongoose 6.x first.

* [`strictQuery`](#strictquery)

<h3 id="strictquery"><a href="#strictquery">`strictQuery`</a></h3>

`strictQuery` is now false by default.

```javascript
const mySchema = new Schema({ field: Number });
const MyModel = mongoose.model('Test', mySchema);

// Mongoose will not strip out `notInSchema: 1` because `strictQuery` is false by default
const docs = await MyModel.find({ notInSchema: 1 });
// Empty array in Mongoose 7. In Mongoose 6, this would contain all documents in MyModel
docs;
```