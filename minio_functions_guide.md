# מדריך פונקציות MinIO

MinIO היא ספריית JavaScript/Node.js ללקוח של Amazon S3 עבור אחסון אובייקטים. הנה הפונקציות העיקריות:

## חיבור והגדרה

**new Client(options)**
יוצר חיבור חדש ללקוח MinIO.
```javascript
const MinIO = require('minio');
const client = new MinIO.Client({
  endPoint: 'localhost',
  port: 9000,
  accessKey: 'minioadmin',
  secretKey: 'minioadmin'
});
```

## פעולות Bucket (תיקיות)

**makeBucket(bucketName, region, callback)**
יוצר bucket חדש.
```javascript
client.makeBucket('myBucket', 'us-east-1', (err) => {
  if (err) console.log(err);
});
```

**listBuckets(callback)**
מחזיר רשימת כל ה-buckets.
```javascript
client.listBuckets((err, buckets) => {
  console.log(buckets);
});
```

**bucketExists(bucketName, callback)**
בודק אם bucket קיים.
```javascript
client.bucketExists('myBucket', (err, exists) => {
  console.log(exists); // true או false
});
```

**removeBucket(bucketName, callback)**
מוחק bucket ריק.
```javascript
client.removeBucket('myBucket', (err) => {
  if (!err) console.log('מחוק בהצלחה');
});
```

## העלאת קבצים

**putObject(bucketName, objectName, stream, size, metadata, callback)**
מעלה קובץ לבucket.
```javascript
const fs = require('fs');
const stream = fs.createReadStream('file.txt');
client.putObject('myBucket', 'myFile.txt', stream, 1024, (err) => {
  if (!err) console.log('הועלה בהצלחה');
});
```

**fPutObject(bucketName, objectName, filePath, metadata, callback)**
מעלה קובץ מהדיסק.
```javascript
client.fPutObject('myBucket', 'myFile.txt', '/path/file.txt', (err) => {
  if (!err) console.log('הועלה');
});
```

## הורדת קבצים

**getObject(bucketName, objectName, callback)**
מוריד קובץ כ-stream.
```javascript
client.getObject('myBucket', 'myFile.txt', (err, stream) => {
  if (!err) stream.pipe(fs.createWriteStream('downloaded.txt'));
});
```

**fGetObject(bucketName, objectName, filePath, callback)**
מוריד קובץ וחוסך אותו בדיסק.
```javascript
client.fGetObject('myBucket', 'myFile.txt', './local-file.txt', (err) => {
  if (!err) console.log('הורד');
});
```

## רשימה ומידע על קבצים

**listObjects(bucketName, prefix, recursive, callback)**
רושם כל הקבצים בbucket.
```javascript
const stream = client.listObjects('myBucket', '', true);
stream.on('data', (obj) => {
  console.log(obj.name);
});
```

**listObjectsV2(bucketName, prefix, recursive, callback)**
גרסה חדשה יותר של listObjects.
```javascript
const stream = client.listObjectsV2('myBucket', 'documents/', true);
stream.on('data', (obj) => console.log(obj.name));
```

**statObject(bucketName, objectName, callback)**
מקבל מידע על קובץ (גודל, תאריך, וכו').
```javascript
client.statObject('myBucket', 'myFile.txt', (err, stat) => {
  console.log(stat.size); // גודל הקובץ
  console.log(stat.etag); // זיהוי ייחודי
});
```

## מחיקת קבצים

**removeObject(bucketName, objectName, callback)**
מוחק קובץ יחיד.
```javascript
client.removeObject('myBucket', 'myFile.txt', (err) => {
  if (!err) console.log('מחוק');
});
```

**removeObjects(bucketName, objectsList, callback)**
מוחק מספר קבצים בבת אחת.
```javascript
const objList = ['file1.txt', 'file2.txt', 'file3.txt'];
client.removeObjects('myBucket', objList, (err) => {
  if (!err) console.log('כל הקבצים מחוקים');
});
```

## שיתוף וגישה

**presignedGetObject(bucketName, objectName, expirySeconds, callback)**
יוצר URL זמנית להורדת קובץ (עם תוקף).
```javascript
client.presignedGetObject('myBucket', 'myFile.txt', 24*60*60, (err, url) => {
  console.log(url); // ניתן לשתף את הURL הזו
});
```

**presignedPutObject(bucketName, objectName, expirySeconds, callback)**
יוצר URL זמנית להעלאת קובץ.
```javascript
client.presignedPutObject('myBucket', 'newFile.txt', 60*60, (err, url) => {
  console.log(url); // ניתן לעלות לקובץ דרך URL זו
});
```

## תגיות ומטא-דטה

**setObjectTagging(bucketName, objectName, tags, callback)**
מוסיף תגיות לקובץ.
```javascript
const tags = { category: 'documents', year: '2024' };
client.setObjectTagging('myBucket', 'myFile.txt', tags, (err) => {
  if (!err) console.log('תגיות הוספו');
});
```

**getObjectTagging(bucketName, objectName, callback)**
מקבל את התגיות של קובץ.
```javascript
client.getObjectTagging('myBucket', 'myFile.txt', (err, tags) => {
  console.log(tags);
});
```

## העתקת קבצים

**copyObject(bucketName, objectName, sourceObject, conditions, callback)**
מעתיק קובץ ממקום למקום.
```javascript
const source = '/source-bucket/source-file.txt';
client.copyObject('dest-bucket', 'dest-file.txt', source, (err) => {
  if (!err) console.log('הועתק');
});
```

## גרסאות ודלקות חיים

**setBucketVersioning(bucketName, versioningConfig, callback)**
מפעיל שמירת גרסאות קודמות של קבצים.
```javascript
client.setBucketVersioning('myBucket', { Status: 'Enabled' }, (err) => {
  console.log('גרסאות מופעלות');
});
```

**setBucketLifecycle(bucketName, lifecycleConfig, callback)**
קבע כללים למחיקה או הסתרה אוטומטית של קבצים ישנים.

## התראות

**setBucketNotification(bucketName, notificationConfig, callback)**
הגדרת התראות כשקבצים מועלים או נמחקים.

**listenBucketNotification(bucketName, prefix, suffix, events, callback)**
האזנה לאירועים בזמן אמת בbucket.

## טיפול בשגיאות

הרוב של פונקציות MinIO משתמשות בcallback עם (error, result).
```javascript
client.getObject('myBucket', 'myFile.txt', (err, data) => 