# nodejs api ด้วย expressjs

## ติดตั้ง dependencies

```
npm init -y
npm install express mysql2
```

## db.js (ไฟล์เชื่อมต่อ MySQL)

```js
// db.js
const mysql = require("mysql2/promise");

const pool = mysql.createPool({
  host: "localhost",
  user: "root",
  password: "",
  database: "cscku2025",
  waitForConnections: true,
  connectionLimit: 10,
  queueLimit: 0,
});

module.exports = pool;
```

## routes/users.js (ไฟล์ routes สำหรับจัดการ user)

```js
// routes/users.js
const express = require("express");
const router = express.Router();
const pool = require("../db");

// CREATE - เพิ่มผู้ใช้
router.post("/", async (req, res) => {
  const {name, email} = req.body;
  try {
    const [result] = await pool.query(
      "INSERT INTO users (name, email) VALUES (?, ?)",
      [name, email]
    );
    res.status(201).json({id: result.insertId, name, email});
  } catch (err) {
    res.status(500).json({error: err.message});
  }
});

// READ - ดึงผู้ใช้ทั้งหมด
router.get("/", async (req, res) => {
  try {
    const [rows] = await pool.query("SELECT * FROM users");
    res.json(rows);
  } catch (err) {
    res.status(500).json({error: err.message});
  }
});

// READ - ดึงผู้ใช้ตาม id
router.get("/:id", async (req, res) => {
  try {
    const [rows] = await pool.query("SELECT * FROM users WHERE id = ?", [
      req.params.id,
    ]);
    if (rows.length === 0)
      return res.status(404).json({error: "User not found"});
    res.json(rows[0]);
  } catch (err) {
    res.status(500).json({error: err.message});
  }
});

// UPDATE - แก้ไขผู้ใช้
router.put("/:id", async (req, res) => {
  const {name, email} = req.body;
  try {
    const [result] = await pool.query(
      "UPDATE users SET name = ?, email = ? WHERE id = ?",
      [name, email, req.params.id]
    );
    if (result.affectedRows === 0)
      return res.status(404).json({error: "User not found"});
    res.json({id: req.params.id, name, email});
  } catch (err) {
    res.status(500).json({error: err.message});
  }
});

// DELETE - ลบผู้ใช้
router.delete("/:id", async (req, res) => {
  try {
    const [result] = await pool.query("DELETE FROM users WHERE id = ?", [
      req.params.id,
    ]);
    if (result.affectedRows === 0)
      return res.status(404).json({error: "User not found"});
    res.json({message: "User deleted"});
  } catch (err) {
    res.status(500).json({error: err.message});
  }
});

module.exports = router;
```

## index.js (รันเซิร์ฟเวอร์)

```js
// index.js
const express = require("express");
const app = express();
const userRoutes = require("./routes/users");

app.use(express.json()); // เพื่ออ่าน JSON จาก req.body
app.use("/users", userRoutes); // กำหนด route

app.listen(3000, () => {
  console.log("Server is running at http://localhost:3000");
});
```

## run node ตรง ๆ

```js
node index.js
```

## ใช้ nodemon (รันอัตโนมัติเมื่อมีการแก้ไขไฟล์)

```js
npm install --save-dev nodemon

# package.json
"scripts": {
  "start": "node index.js",
  "dev": "nodemon index.js"
}

npm run dev
```
