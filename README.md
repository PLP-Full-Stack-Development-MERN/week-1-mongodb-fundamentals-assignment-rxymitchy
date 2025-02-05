MongoDB Week 1 Assignment
Objective

The goal of this assignment is to learn and apply MongoDB fundamentals by performing various CRUD operations, data modeling, and aggregation on a library database.
Prerequisites

    MongoDB installed locally or a free cluster on MongoDB Atlas.
    MongoDB Shell (mongosh) installed.
    Basic knowledge of MongoDB commands.

Step 1: Setup MongoDB
Option 1: Install MongoDB Locally

    Download MongoDB from https://www.mongodb.com/try/download/community.
    Follow the installation guide for your operating system.
    Start the MongoDB server using the command:

    mongod

Verify the installation by running:

    mongo --version

Option 2: Use MongoDB Atlas

    Go to https://www.mongodb.com/cloud/atlas and create an account.
    Create a new cluster.
    Connect to your cluster using the connection string provided by MongoDB Atlas.

Step 2: Create Database and Collection
Create a library Database and books Collection

    Open the MongoDB Shell (mongosh).
    Create the library database and switch to it:

use library

Create the books collection and insert sample data with custom _id fields:

    db.books.insertMany([
      {_id: 1,title: "Harry Potter",author: "JK Rowling",publishedYear: 2012,genre: "fiction",ISBN:"9780743273565"},
      {_id: 2,title: "A thousand Splendind Suns",author: "Khaled Hosseini",publishedYear: 2015,genre: "fiction",ISBN:"9780061120084" },
      { _id: 3, title: "1984", author: "George Orwell", publishedYear: 1949, genre: "Dystopian", ISBN: "1234567890" },
      { _id: 4, title: "To Kill a Mockingbird", author: "Harper Lee", publishedYear: 1960, genre: "Fiction", ISBN: "1234567891" },
      { _id: 5, title: "The Great Gatsby", author: "F. Scott Fitzgerald", publishedYear: 1925, genre: "Fiction", ISBN: "1234567892" },
      { _id: 6, title: "Harry Potter and the Philosopher's Stone", author: "J.K. Rowling", publishedYear: 1997, genre: "Fantasy", ISBN: "1234567893" },
      { _id: 7, title: "The Road", author: "Cormac McCarthy", publishedYear: 2006, genre: "Post-apocalyptic", ISBN: "1234567894" }
    ]);

Step 3: CRUD Operations
Retrieve All Books

db.books.find();

Query Books by Author

db.books.find({ author: "George Orwell" });

Find Books Published After 2000

db.books.find({ publishedYear: { $gt: 2000 } });

Update Published Year of a Book

db.books.updateOne({author: "J.K. Rowling"}, {$set: {publishedYear: 2005}});

Add a New Field (rating) to All Books

db.books.updateMany({}, { $set: { rating: 8 } });

Step 4: Delete Data
Delete a Book by ISBN

db.books.deleteOne({ ISBN: "9780743273565" });

Remove All Books of a Specific Genre

db.books.deleteMany({ genre: "Post-apocalyptic" });

Step 5: Data Modeling for an E-Commerce Platform
Collections:

    Users
        Fields: userId, name, email, address, createdAt

    Products
        Fields: productId, name, description, price, category, stock

    Orders
        Fields: orderId, userId (reference to Users), products (array of product references), totalAmount, orderDate

Step 6: Aggregation Examples
Total Number of Books per Genre

db.books.aggregate([
  { $group: { _id: "$genre", totalBooks: { $sum: 1 } } }
]);

Calculate Average Published Year

db.books.aggregate([
  { $group: { _id: null, avgPublishedYear: { $avg: "$publishedYear" } } }
]);

Identify the Top-Rated Book

db.books.find().sort({ rating: -1 }).limit(1);

Step 7: Indexing
Create an Index on the author Field

db.books.createIndex({ author: 1 });

Benefits of Indexing

    Improves Query Performance: Speeds up search operations.
    Reduces Scan Time: Prevents MongoDB from scanning all documents.
    Efficient Sorting: Helps with sorting large collections quickly.

Step 8: Testing and Verification

    Use the MongoDB shell or Compass to test all operations.
    Verify that your queries return the expected results.
    Ensure that updates and deletions are correctly applied.

