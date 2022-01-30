## Section 28: Putting Everything Together

    Todolist-v2-starting-files

    npm i

## 342. Lest take the TodoList project to the Next Level and Connect it with Mongoose

    npm i mongoose

    restart sever nodemon app.js

    pada terminal baru , masuk kedalam mongodb:
    mongo
    show dbs
    masuk kedalam todolistDB: use todolistDB
    > show collections
    items
    > db.items.find()
    { "_id" : ObjectId("61f667ac1667d9ff268f493b"), "name" : "welcome to your todolist!", "__v" : 0 }
    { "_id" : ObjectId("61f667ac1667d9ff268f493c"), "name" : "Hit the + buttom to aff a new item.", "__v" : 0 }
    { "_id" : ObjectId("61f667ac1667d9ff268f493d"), "name" : "<-- Hit this to delete an item.", "__v" : 0 }

## 343. Rendering Database items in the ToDoList App part 1

    menampilkan data : http://localhost:3000/

## 343. Rendering Database items in the ToDoList App part 2

    (kondisi jika data belum tersedia dan juga jika data tersedia)
    pertma delete database :
    mongo
    > use todolistDB
    switched to db todolistDB
    > show collections
    items
    > db.dropDatabase()
    { "dropped" : "todolistDB", "ok" : 1 }
    > show dbs

    maka database todolistDB akan terhapus.

    selanjutnya restart server nodemon app.js
    dan tampilkan data pada browser : http://localhost:3000/

## 344. Adding new Items to our Todolist Database

    restart server nodemon app.js
    buka browser : http://localhost:3000/
    lakukan input todolist dan data akan bertambah
