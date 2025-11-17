# 📚 מדריך Promises ו-Async/Await ב-JavaScript

## 1️⃣ מה זה Promise?
- Promise הוא **אובייקט** שמייצג פעולה אסינכרונית שתסתיים בעתיד.
- Promise יכול להיות במצב אחד מתוך שלושה:
  1. `pending` - ממתין להשלמת הפעולה
  2. `fulfilled` - הסתיים בהצלחה
  3. `rejected` - הסתיים בכישלון

### דוגמה בסיסית:
```js
const p = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Done"), 1000);
});
p.then(console.log); // ידפיס "Done" אחרי שנייה
```

---

## 2️⃣ Async / Await
- `async` - פונקציה שמוגדרת כסינכרונית ומחזירה **Promise** תמיד.
- `await` - מחכה ל-Promise להסתיים לפני שממשיך את הקוד.

### דוגמה בסיסית:
```js
async function fetchData() {
  const data = await Promise.resolve("Hello");
  console.log(data);
}
fetchData(); // ידפיס "Hello"
```

### כללים חשובים:
- `await` רק בתוך `async` function.
- `async/await` הוא תחביר נוח על בסיס Promises.
- שגיאות בתוך async תופסות עם `try/catch`.

---

## 3️⃣ דוגמאות קצרות עם פלט

### דוגמה 1 - setTimeout + Promise
```js
console.log("A");
setTimeout(() => console.log("B"), 0);
console.log("C");
```
**פלט:**
```
A
C
B
```

### דוגמה 2 - Promise.then
```js
Promise.resolve().then(() => console.log("1"));
console.log("2");
```
**פלט:**
```
2
1
```

### דוגמה 3 - Async / Await
```js
async function test() {
  console.log("start");
  await Promise.resolve();
  console.log("end");
}
test();
console.log("outside");
```
**פלט:**
```
start
outside
end
```

### דוגמה 4 - Catch ב-Promise
```js
Promise.reject("Error")
  .catch(() => console.log("catch 1"))
  .then(() => console.log("then 2"));
```
**פלט:**
```
catch 1
then 2
```

---

## 4️⃣ מתי להשתמש באסינכרוניות
- פעולה שדורשת **המתנה למשהו חיצוני**: קריאת קובץ, בקשה לשרת, DB.
- פעולה שדורשת **זמן ממושך**: עיבוד כבד, טיימרים.
- סדר פעולות תלויות: פעולה אחת צריכה להסתיים לפני השנייה.
- **לא צריך** עבור חישובים פשוטים ומהירים.

---

## 5️⃣ שאלות תאורטיות עם תשובות

1. **מהו Promise?**  
   ✅ אובייקט שמייצג פעולה שתסתיים בעתיד.

2. **מהם המצבים של Promise?**  
   ✅ pending, fulfilled, rejected

3. **מה ההבדל בין Promise ל-async/await?**  
   ✅ async/await הוא תחביר נוח לקריאה על בסיס Promises.

4. **מה עושה מילת המפתח `await`?**  
   ✅ מחכה ל-Promise להסתיים בתוך פונקציה async.

5. **מה קורה אם נשתמש ב-await מחוץ ל-async?**  
   ✅ SyntaxError.

6. **איך מטפלים בשגיאות ב-async function?**  
   ✅ עם try { ... } catch(e) { ... }

7. **מה מחזירה פונקציה async?**  
   ✅ תמיד Promise.

8. **מה קורה ב-Promise.all אם אחד נכשל?**  
   ✅ כולן נכשלות ומוחזר reject.

9. **מה יודפס?**  
```js
async function foo() { return 42; }
foo().then(x => console.log(x));
console.log("Done");
```  
✅ Done  
✅ 42

10. **יתרון השימוש ב-async/await על פני then/catch?**  
✅ קוד קריא יותר, נוח לתחזוקה.

---

