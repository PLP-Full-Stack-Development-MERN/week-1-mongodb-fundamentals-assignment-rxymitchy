library> db.books.insertMany([ {_id: 1,title: "Harry Potter",author: "JK Rowling",publishedYear: 2012,genre: "fiction",ISBN:"9780743273565"}, {_id: 2,title: "A thousand Splendind Suns",author: "Khaled Hosseini",publishedYear: 2015,genre: "fiction",ISBN:"9780061120084" }])
{ acknowledged: true, insertedIds: { '0': 1, '1': 2 } }

library> db.books.insertMany([
...   { _id: 3, title: "1984", author: "George Orwell", publishedYear: 1949, genre: "Dystopian", ISBN: "1234567890" },
...   { _id: 4, title: "To Kill a Mockingbird", author: "Harper Lee", publishedYear: 1960, genre: "Fiction", ISBN: "1234
567891" },
...   { _id: 5, title: "The Great Gatsby", author: "F. Scott Fitzgerald", publishedYear: 1925, genre: "Fiction", ISBN: "1234567892" },
...   { _id: 6, title: "Harry Potter and the Philosopher's Stone", author: "J.K. Rowling", publishedYear: 1997, genre: "Fantasy", ISBN: "1234567893" },
...   { _id: 7, title: "The Road", author: "Cormac McCarthy", publishedYear: 2006, genre: "Post-apocalyptic", ISBN: "1234567894" }
... ]);
{
  acknowledged: true,
  insertedIds: { '0': 3, '1': 4, '2': 5, '3': 6, '4': 7 }
}
library> db.books.find();
[
  {
    _id: 1,
    title: 'Harry Potter',
    author: 'JK Rowling',
    publishedYear: 2012,
    genre: 'fiction',
    ISBN: '9780743273565'
  },
  {
    _id: 2,
    title: 'A thousand Splendind Suns',
    author: 'Khaled Hosseini',
    publishedYear: 2015,
    genre: 'fiction',
    ISBN: '9780061120084'
  },
  {
    _id: 3,
    title: '1984',
    author: 'George Orwell',
    publishedYear: 1949,
    genre: 'Dystopian',
    ISBN: '1234567890'
  },
  {
    _id: 4,
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee',
    publishedYear: 1960,
    genre: 'Fiction',
    ISBN: '1234567891'
  },
  {
    _id: 5,
    title: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    publishedYear: 1925,
    genre: 'Fiction',
    ISBN: '1234567892'
  },
  {
    _id: 6,
    title: "Harry Potter and the Philosopher's Stone",
    author: 'J.K. Rowling',
    publishedYear: 1997,
    genre: 'Fantasy',
    ISBN: '1234567893'
  },
  {
    _id: 7,
    title: 'The Road',
    author: 'Cormac McCarthy',
    publishedYear: 2006,
    genre: 'Post-apocalyptic',
    ISBN: '1234567894'
  }
]
library> db.books.find({publishedYear: {$gt:2000}});
[
  {
    _id: 1,
    title: 'Harry Potter',
    author: 'JK Rowling',
    publishedYear: 2012,
    genre: 'fiction',
    ISBN: '9780743273565'
  },
  {
    _id: 2,
    title: 'A thousand Splendind Suns',
    author: 'Khaled Hosseini',
    publishedYear: 2015,
    genre: 'fiction',
    ISBN: '9780061120084'
  },
  {
    _id: 7,
    title: 'The Road',
    author: 'Cormac McCarthy',
    publishedYear: 2006,
    genre: 'Post-apocalyptic',
    ISBN: '1234567894'
  }
]

library> db.books.deleteOne({ ISBN: "9780743273565" });
{ acknowledged: true, deletedCount: 1 }
library> db.books.find();
[
  {
    _id: 2,
    title: 'A thousand Splendind Suns',
    author: 'Khaled Hosseini',
    publishedYear: 2015,
    genre: 'fiction',
    ISBN: '9780061120084'
  },
  {
    _id: 3,
    title: '1984',
    author: 'George Orwell',
    publishedYear: 1949,
    genre: 'Dystopian',
    ISBN: '1234567890'
  },
  {
    _id: 4,
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee',
    publishedYear: 1960,
    genre: 'Fiction',
    ISBN: '1234567891'
  },
  {
    _id: 5,
    title: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    publishedYear: 1925,
    genre: 'Fiction',
    ISBN: '1234567892'
  },
  {
    _id: 6,
    title: "Harry Potter and the Philosopher's Stone",
    author: 'J.K. Rowling',
    publishedYear: 1997,
    genre: 'Fantasy',
    ISBN: '1234567893'
  },
  {
    _id: 7,
    title: 'The Road',
    author: 'Cormac McCarthy',
    publishedYear: 2006,
    genre: 'Post-apocalyptic',
    ISBN: '1234567894'
  }
]
library> db.books.updateOne({author: "J.K. Rowling"}, {$set: {publishedYear: 2005}});
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
library> db.books.find();
[
  {
    _id: 2,
    title: 'A thousand Splendind Suns',
    author: 'Khaled Hosseini',
    publishedYear: 2015,
    genre: 'fiction',
    ISBN: '9780061120084'
  },
  {
    _id: 3,
    title: '1984',
    author: 'George Orwell',
    publishedYear: 1949,
    genre: 'Dystopian',
    ISBN: '1234567890'
  },
  {
    _id: 4,
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee',
    publishedYear: 1960,
    genre: 'Fiction',
    ISBN: '1234567891'
  },
  {
    _id: 5,
    title: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    publishedYear: 1925,
    genre: 'Fiction',
    ISBN: '1234567892'
  },
  {
    _id: 6,
    title: "Harry Potter and the Philosopher's Stone",
    author: 'J.K. Rowling',
    publishedYear: 2005,
    genre: 'Fantasy',
    ISBN: '1234567893'
  },
  {
    _id: 7,
    title: 'The Road',
    author: 'Cormac McCarthy',
    publishedYear: 2006,
    genre: 'Post-apocalyptic',
    ISBN: '1234567894'
  }
]
library> db.books.update({}, {rating: 8});
DeprecationWarning: Collection.update() is deprecated. Use updateOne, updateMany, or bulkWrite.
MongoInvalidArgumentError: Update document requires atomic operators
library> db.books.updateMany({}, {rating: 8});
MongoInvalidArgumentError: Update document requires atomic operators
library> db.books.updateMany({}, {$set: {rating: 8}});
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 6,
  modifiedCount: 6,
  upsertedCount: 0
}
library> db.books.find();
[
  {
    _id: 2,
    title: 'A thousand Splendind Suns',
    author: 'Khaled Hosseini',
    publishedYear: 2015,
    genre: 'fiction',
    ISBN: '9780061120084',
    rating: 8
  },
  {
    _id: 3,
    title: '1984',
    author: 'George Orwell',
    publishedYear: 1949,
    genre: 'Dystopian',
    ISBN: '1234567890',
    rating: 8
  },
  {
    _id: 4,
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee',
    publishedYear: 1960,
    genre: 'Fiction',
    ISBN: '1234567891',
    rating: 8
  },
  {
    _id: 5,
    title: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    publishedYear: 1925,
    genre: 'Fiction',
    ISBN: '1234567892',
    rating: 8
  },
  {
    _id: 6,
    title: "Harry Potter and the Philosopher's Stone",
    author: 'J.K. Rowling',
    publishedYear: 2005,
    genre: 'Fantasy',
    ISBN: '1234567893',
    rating: 8
  },
  {
    _id: 7,
    title: 'The Road',
    author: 'Cormac McCarthy',
    publishedYear: 2006,
    genre: 'Post-apocalyptic',
    ISBN: '1234567894',
    rating: 8
  }
]
library> db.books.deleteMany({ genre: "Post-apocalyptic"});
{ acknowledged: true, deletedCount: 1 }
library> db.books.find();
[
  {
    _id: 2,
    title: 'A thousand Splendind Suns',
    author: 'Khaled Hosseini',
    publishedYear: 2015,
    genre: 'fiction',
    ISBN: '9780061120084',
    rating: 8
  },
  {
    _id: 3,
    title: '1984',
    author: 'George Orwell',
    publishedYear: 1949,
    genre: 'Dystopian',
    ISBN: '1234567890',
    rating: 8
  },
  {
    _id: 4,
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee',
    publishedYear: 1960,
    genre: 'Fiction',
    ISBN: '1234567891',
    rating: 8
  },
  {
    _id: 5,
    title: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    publishedYear: 1925,
    genre: 'Fiction',
    ISBN: '1234567892',
    rating: 8
  },
  {
    _id: 6,
    title: "Harry Potter and the Philosopher's Stone",
    author: 'J.K. Rowling',
    publishedYear: 2005,
    genre: 'Fantasy',
    ISBN: '1234567893',
    rating: 8
  }
]
library> db.books.aggregate([
... {$group : {_id: "$genre" , count: {$sum: 1}}}
... ]);
[
  { _id: 'Fantasy', count: 1 },
  { _id: 'Dystopian', count: 1 },
  { _id: 'Fiction', count: 2 },
  { _id: 'fiction', count: 1 }
]
library> db.books.updateOne({publishedYear:2015}, {$set:{genre:"Fiction"}});
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
library> db.books.aggregate([ { $group: { _id: "$genre", count: { $sum: 1 } } }] );
[
  { _id: 'Dystopian', count: 1 },
  { _id: 'Fantasy', count: 1 },
  { _id: 'Fiction', count: 3 }
]

library> db.books.aggregate([
...   { $group: { _id: null, avgPublishedYear: { $avg: "$publishedYear" } } }
... ]);
[ { _id: null, avgPublishedYear: 1970.8 } ]
library> db.books.aggregate([
...   { $sort: { rating: -1 } },
...   { $limit: 1 }
... ]);
[
  {
    _id: 2,
    title: 'A thousand Splendind Suns',
    author: 'Khaled Hosseini',
    publishedYear: 2015,
    genre: 'Fiction',
    ISBN: '9780061120084',
    rating: 8
  }
]
library> db.books.createIndex({ author: 1 });
author_1