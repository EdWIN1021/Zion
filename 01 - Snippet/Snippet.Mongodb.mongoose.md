# mongoose

Owner: Edwin

```jsx
const mongoose = require('mongoose');
```

## Schema

```jsx
const userSchema = new mongoose.Schema({
  name: {
    type: String,
    require: [true, 'error message'],
    unique: true,
    trim: true,
  },
  age: {
    type: Number,
    require: [true, 'error message'],
    default: 0,
  },
  skills: [String],
  createdAt: {
    type: Date,
    default: Date.now(),
  },
});
```

## Model

```jsx
const User = mongoose.model('User', userSchema);
module.exports = Tour;
```

## Get all data

```jsx
User.find();
```

## Get single data

```jsx
User.findById(req.params.id)
```

## Create data

```jsx
User.create(req.body)
```

## Update data

```jsx
User.findByIdAndUpdate(req.params.id, req.body, {
      new: true, //return latest doc
      runValidators: true,
});
```

## Delete data

```jsx
User.findByIdAndDelete(req.params.id)
```

## Sort

```jsx
await query.sort([field_name])
```

## Fields

```jsx
await query.select({ field1 field2 })
```

## Pagenation

```jsx
const page = req.query.page * 1 || 1;
const limit = req.query.limit * 1 || 100;
const skip = (page - 1) * limit;

query = query.skip(skip).limit(limit);
```

## countDocuments

```jsx
const total = await User.countDocuments()
```