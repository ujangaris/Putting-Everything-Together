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

## 345. Deleting Items to our Todolist Database

    restart server nodemon app.js
    buka browser : http://localhost:3000/
    kemudian cobal cheklist checkbox pada list yang tersedia, dan lihat apa yang terjadi
    response juga dapat dilihat pada terminal.

## 346. Creating Custom Lists using Express Route Parameters

    pengujian pada browser : http://localhost:3000/<masukan nama parameter>
        note: nama parameter : bisa home, work, school
        contoh http://localhost:3000/School

    pengujian pada database:
    mongo
    show dbs
    use todolistDB
    show collections
    masuk kedalam lists : db.lists.find()
    dan coba liat isi lists

## 347. Adding New Items to the Custom ToDo Lists

    pengujian pada browser : http://localhost:3000/<masukan nama parameter>
        note: nama parameter : bisa home, work, school
        contoh http://localhost:3000/School
        kemudian coba input data .
        dikatan berhasil jika pada parameter inputan berhasil menampikan data yang di input pada todolist.

## 348. Revisiting Loadash and Deleting Items from Custom ToDo Lists

    Documentation: https://docs.mongodb.com/manual/reference/operator/update/pull/

    install lodash : npm i lodash
    Documentation: https://lodash.com/docs/4.17.15#capitalize

        ┌──────────────────────────────────────────────────────────────────────────────┐
        │  note:   loadash capitalize digunakan pada bagian parameter web setelah      │
        │           http://localhost:3000,                                             │
        │          jika /work atau /Work akan dibaca sama dan menuju halaman yang      │
        │           sama.                                                              │
        │             contoh : http://localhost:3000/work dan                          │
        │                       http://localhost:3000/Work dibaca oleh browser         │
        │                       sama                                                   │
        └──────────────────────────────────────────────────────────────────────────────┘

    pertama hapus data lists:
    masuk ke mongo:
    mongo
    show dbs
    use todolistDB
    show collections
    db.lists.drop()


    pengujian pada browser : http://localhost:3000/<masukan nama parameter>
        note: nama parameter : bisa home, work, school
        contoh http://localhost:3000/School
        kemudian coba cheklist data(disini cheklis menandakan hapus) .
        dikatan berhasil jika pada halaman brwoser yang sesuai parameter berhasil menghapus data pada todolist.

## Section 29: Deploying Your Web Application

### 351. How to Setup MongoDB Atlas

    ┌──────────────────────────────────────────────────────────────────────────────┐
    │ pada halaman mongodb klik connect :                                          │
    │     =>  connect your aplication                                              │
    │     =>  copy string :                                                        │
    │         mongodb+srv://ujang123:<password>@ujangarisandi.poe2b.mongodb.net/   │
    │         myFirstDatabase?retryWrites=true&w=majority                          │
    │                                                                              │
    │         ganti <password> dengan password yang sesuai , jika lupa liat pada   │
    │         database access                                                      │
    │         kemudian pilih password dan show password.                           │
    │     =>  dan pastekan pada app.js                                             │
    │     =>  restart kembali server, kemudian coba input todoList pada browser    │
    │         dan lihat pada mongodb altas,                                        │
    │         jika data berhasil ter integrasi maka langkah yang kita lakukan      │
    │         berhasil                                                             │
    └──────────────────────────────────────────────────────────────────────────────┘

### 352. Deploying an App with a Database to Heroku

        ┌──────────────────────────────────────────────────────────────────────────────┐
        │ note: deploying ini tidak menggunakan file .env                              │
        │       jadi tidak perlu pengaturan tambahan                                   │
        └──────────────────────────────────────────────────────────────────────────────┘
    Documentation:
            https://devcenter.heroku.com/articles/deploying-nodejs
            https://devcenter.heroku.com/search?utf8=%E2%9C%93&q=articles+deploying+nodejs&commit=Submit+search
            https://devcenter.heroku.com/articles/git
            https://devcenter.heroku.com/articles/preparing-a-codebase-for-heroku-deployment

    untuk lebih aman lakukan langkah berikut:
    copy folder directory todolist,
    kemudian namakan sesuai yang kita inginkan,
    lalu hapus file .git dengan cara rm -rf .git

    git init
    git add .
    git commit-"Initial commit"

    login to heroku:
    heroku login
    kemuan kelik tombol apa saja pada keybord,
    tunggu beberapa saat akan terbuka halaman login heroku
    jika succes akan seperti ini:
        Logging in... done
        Logged in as ujangaja@gmail.com

    heroku create
    touch Procfile

    pada file Procfile isi seperti berikut:
        web: node app.js

    pada app.js  update port:

    ┌──────────────────────────────────────────────────────────────────────────────┐
    │         let port = process.env.PORT                                          │
    │         if(port == null || port == ""){                                      │
    │             port = 3000                                                      │
    │         }                                                                    │
    │                                                                              │
    │         app.listen(port, function(){                                         │
    │             console.log("Server has started success")                        │
    │         })                                                                   │
    └──────────────────────────────────────────────────────────────────────────────┘

    pada package.json tambahkan
        "engines": {
        "node": "14.x"
    },

    seperti berikut :
    ┌──────────────────────────────────────────────────────────────────────────────┐
    │       "license": "ISC",                                                      │
    │       "engines": {                                                           │
    │         "node": "14.x"                                                       │
    │       },                                                                     │
    └──────────────────────────────────────────────────────────────────────────────┘

    buat file .gitignore
    touch .gitignore
    pastekan pada file .gitignore
    ┌──────────────────────────────────────────────────────────────────────────────┐
    │       /node_modules                                                          │
    │       npm-debug.log                                                          │
    │       .DS_Store                                                              │
    │       /*.env                                                                 │
    └──────────────────────────────────────────────────────────────────────────────┘

    git add .
    git commit -m"Add gitignore, procfile and update ports"
    git push heroku master
    tunggu beberapa saat...
    pada terminal akan tampil halaman dari application yang kita deploy, contoh:
    ┌──────────────────────────────────────────────────────────────────────────────┐
    │     remote: ---> Launching...                                                │
    │     remote:      Released v3                                                 │
    │     remote:      https://limitless-sands-25469.herokuapp.com/ deployed to-   │
    │                  Heroku                                                      │
    │     remote:                                                                  │
    │     remote: Verifying deploy... done.                                        │
    │                                                                              │
    │     klik ctr + klik pada https://limitless-sands-25469.herokuapp.com/        │
    └──────────────────────────────────────────────────────────────────────────────┘
