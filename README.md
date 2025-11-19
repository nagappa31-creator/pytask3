Here is a clean and clear README.md you can use for your project:


---

📚 Book Management REST API + Frontend UI

This project is a simple Node.js + Express REST API for managing books (in-memory storage) along with a HTML frontend that interacts with the API using Fetch API.


---

⭐ Features

✔ GET all books

✔ POST add a new book

✔ PUT update a book

✔ DELETE remove a book

✔ Simple HTML UI to test all endpoints

✔ No database required (books stored in memory)



---

📁 Project Structure

project/
│── server.js        # Express API
│── index.html       # Frontend UI
│── README.md


---

🚀 How to Run the Project

1️⃣ Install Dependencies

Make sure you have Node.js installed.

npm init -y
npm install express cors


---

2️⃣ Create server.js

Below is the API code (make sure this file exists):

const express = require("express");
const cors = require("cors");
const app = express();

app.use(cors());
app.use(express.json());

// In-memory data
let books = [
    { id: 1, title: "Book One", author: "Author A" },
    { id: 2, title: "Book Two", author: "Author B" }
];

// GET all books
app.get("/books", (req, res) => {
    res.json(books);
});

// POST add book
app.post("/books", (req, res) => {
    const { title, author } = req.body;
    const newBook = { id: books.length + 1, title, author };
    books.push(newBook);
    res.json(newBook);
});

// PUT update book
app.put("/books/:id", (req, res) => {
    const id = parseInt(req.params.id);
    const { title, author } = req.body;

    const book = books.find(b => b.id === id);
    if (!book) return res.status(404).json({ message: "Book not found" });

    book.title = title;
    book.author = author;

    res.json(book);
});

// DELETE book
app.delete("/books/:id", (req, res) => {
    const id = parseInt(req.params.id);
    books = books.filter(book => book.id !== id);
    res.json({ message: "Book deleted" });
});

app.listen(3000, () => {
    console.log("Server running on http://localhost:3000");
});


---

3️⃣ Run the Server

node server.js

You should see:

Server running on http://localhost:3000


---

🌐 4️⃣ Open the Frontend (index.html)

Simply open index.html in your browser.

All buttons will call:

GET    http://localhost:3000/books
POST   http://localhost:3000/books
PUT    http://localhost:3000/books/:id
DELETE http://localhost:3000/books/:id


---

🧪 Testing the API

You can test using:

Browser (UI provided)

Postman

curl


Example GET:

GET http://localhost:3000/books


---

🎯 Notes

Since books are stored in memory, data resets whenever server restarts.

Enable CORS to allow index.html to call API.



---

📌 Author

Made for learning REST APIs using Node.js + Express.
---
