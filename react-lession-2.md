# 📘 บทที่ 2: JSX และ Components

## 🎯 เป้าหมายบทเรียน
- เข้าใจว่า JSX คืออะไร
- สร้าง React Components อย่างง่าย
- เข้าใจการจัดโครงสร้างหน้าด้วย Components

---

## 💡 JSX คืออะไร?
JSX (JavaScript XML) เป็นไวยากรณ์พิเศษที่ให้เราเขียน HTML-like code ภายใน JavaScript ได้ใน React

```jsx
const element = <h1>Hello JSX</h1>;
```

### ✅ ข้อควรรู้เกี่ยวกับ JSX
- JSX ต้องมี tag เดียวครอบไว้
- ใช้ `className` แทน `class`
- ใช้ `{}` แทรก JavaScript ใน JSX

```jsx
const name = "John";
return <p>สวัสดี {name}</p>;
```

---

## 🧩 การสร้าง Component แบบฟังก์ชัน

### 🔹 ตัวอย่าง Component พื้นฐาน

```jsx
function Welcome() {
  return <h1>ยินดีต้อนรับสู่ React</h1>;
}
```

### 🔹 นำ Component ไปใช้

```jsx
function App() {
  return (
    <div>
      <Welcome />
      <p>นี่คือแอปของฉัน</p>
    </div>
  );
}
```

---

## 🔀 การใช้ Fragment
ใช้ `<></>` แทน `div` ถ้าไม่ต้องการสร้าง element ใหม่

```jsx
function App() {
  return (
    <>
      <h1>หัวข้อหลัก</h1>
      <p>เนื้อหา</p>
    </>
  );
}
```

---

## 📝 แบบฝึกหัดท้ายบท

1. สร้าง Component ชื่อ `Footer` และแสดงคำว่า “© 2025 React Beginner”
2. ใช้ `<Fragment>` หรือ `<>` เพื่อแสดงหลาย tag โดยไม่ใช้ `div`
3. ลองแสดงชื่อผู้ใช้แบบ dynamic ด้วย JSX

---

## 📦 สรุปบทที่ 2

- JSX คือภาษาคล้าย HTML ที่ใช้ใน React
- Component คือฟังก์ชันที่ส่งกลับ UI
- เราสามารถแยกส่วนประกอบของหน้าให้เล็กลงเพื่อจัดการง่ายขึ้น
