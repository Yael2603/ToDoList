# ToDo List – Fullstack

אפליקציית ניהול משימות: שרת ASP.NET Core Minimal API, מסד נתונים MySQL וקליינט React.

## מבנה

| תיקייה | תוכן |
|---|---|
| `TodoApi` | שרת Minimal API (.NET 9) עם Entity Framework Core ו-Pomelo (DB First) |
| `ToDoListReact` | קליינט React שפונה לשרת באמצעות Axios |

## דרישות מוקדמות

- .NET 9 SDK
- Node.js + npm
- Docker Desktop (להרצת MySQL)

## הרצה

### 1. מסד הנתונים (MySQL ב-Docker)

```
docker run --name todo-mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=yes -e MYSQL_DATABASE=ToDoDB -p 127.0.0.1:3306:3306 -v todo-mysql-data:/var/lib/mysql -d mysql:8.0
```

יצירת הטבלה:

```
docker exec todo-mysql mysql -uroot ToDoDB -e "CREATE TABLE Items (Id int NOT NULL AUTO_INCREMENT, Name varchar(100), IsComplete tinyint(1), PRIMARY KEY (Id));"
```

### 2. השרת

```
cd TodoApi
dotnet run
```

השרת מאזין ב-`http://localhost:5209`. ממשק Swagger: `http://localhost:5209/swagger`.

### 3. הקליינט

```
cd ToDoListReact
npm i
npm start
```

הקליינט נפתח ב-`http://localhost:3000`.

## API

| Method | Route | פעולה |
|---|---|---|
| GET | `/items` | שליפת כל המשימות |
| POST | `/items` | הוספת משימה |
| PUT | `/items/{id}` | עדכון משימה |
| DELETE | `/items/{id}` | מחיקת משימה |
