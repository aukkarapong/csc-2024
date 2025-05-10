# 📘 บทที่ 1: รู้จักกับ React

## 🎯 เป้าหมายบทเรียน
- เข้าใจว่า React คืออะไร และมีข้อดีอย่างไร
- เตรียมเครื่องมือสำหรับพัฒนาเว็บด้วย React
- สร้างโปรเจกต์แรก และแสดงข้อความ “Hello React!”

---

## 🧠 React คืออะไร?
React เป็น JavaScript library (ไม่ใช่ framework) สำหรับสร้าง **User Interface (UI)** ที่ถูกพัฒนาโดย Facebook

### 🔑 จุดเด่นของ React
- สร้าง UI แบบ **Component-Based**
- ใช้ **Virtual DOM** ช่วยให้การเรนเดอร์เร็วขึ้น
- มีชุมชนใหญ่มาก และใช้ร่วมกับ framework อื่น ๆ ได้

---

## 🛠 เตรียมเครื่องมือ

### 1. ติดตั้ง Node.js
ดาวน์โหลดที่ [https://nodejs.org/](https://nodejs.org/)  
ตรวจสอบว่า `node` และ `npm` ติดตั้งแล้ว:
```bash
node -v
npm -v
```

### 2. ติดตั้ง Visual Studio Code
ดาวน์โหลดที่ [https://code.visualstudio.com/](https://code.visualstudio.com/)

### 3. ติดตั้ง Extension ที่แนะนำ:
- ESLint
- Prettier
- ES7+ React/Redux/React-Native snippets
- React Developer Tools
- Tailwind CSS IntelliSense (ถ้าใช้ Tailwind)

---

## 🚀 สร้างโปรเจกต์ React แรก

### ✅ ใช้ Vite (แนะนำ)
```bash
npm create vite@latest my-react-app -- --template react
cd my-react-app
npm install
npm run dev
```

---

## 🧩 แก้ไฟล์ `App.jsx`
```jsx
function App() {
  return (
    <div>
      <h1>Hello React!</h1>
      <p>ยินดีต้อนรับสู่โลกของ React.js</p>
    </div>
  );
}

export default App;
```

---

## 📝 แบบฝึกหัดท้ายบท

1. เปลี่ยนข้อความใน `<h1>` และ `<p>` เป็นของคุณเอง
2. สร้าง `Header.jsx` แล้วใส่ข้อความ “นี่คือ Header” จากนั้นแสดงใน `App.jsx`
3. เปลี่ยนสีพื้นหลังโดยใช้ CSS

---

## 📦 สรุปบทที่ 1

- รู้จักกับ React และความสามารถหลัก
- เตรียมเครื่องมือสำหรับการพัฒนา
- สร้างโปรเจกต์แรก และเขียน Component เบื้องต้น
