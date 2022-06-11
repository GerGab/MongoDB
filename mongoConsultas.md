# Entrega desafio MongoDB

# Punto 1- Agregar 10 documentos a cada coleccion.

    db.productos.insertMany(<productos.txt>) 
.

    db.mensajes.insertMany(<mensajes.txt>)

## Punto 3- Listar todos los productos dentro de la colección productos.

    db.productos.find()
    
## Punto 3- Listar todos los productos dentro de la colección productos.

    db.mensajes.find()

## Punto 4- Mostrar la cantidad de items en cada coleccion.

    db.productos.find().count()
.

    db.mensajes.find().count()

## Punto 5- Realizar un CRUD.

### a) Agregar un producto mas a la colección productos.

    db.productos.insertOne({"id":3004,"title":"panel","precio":1830,"thumbnail":"http..."})

### b) Realizar una consulta por nombre especifica.

i) Listar productos con precio menor a 1000 pesos.

    db.productos.find({precio:{$lt:1000}})

ii) Listar productos con precio entre 1000 y 3000 pesos.

    db.productos.find({$and:[{precio:{$gt:1000}},{precio:{$lt:3000}}]})

iii) Listar productos con precio mayor a 3000 pesos.

    db.productos.find({precio:{$gt:3000}})

iV) Consultar del nombre del tercer objeto mas barato.

    db.productos.find({},{title:1,_id:0}).sort({ precio: 1 }).skip(2).limit(1)

### c) Actualizar el stock de todos los productos.

    db.productos.updateMany({},{$set:{stock:100}})

### d) Actualizar el stock a 0 de los productos con precio mayor a 4000.

    db.productos.updateMany({precio:{$gt:4000}},{$set:{stock:0}})

### e) Borrar los productos con precio menor a 1000 pesos.

    db.productos.deleteMany({precio:{$lt:1000}})

## Punto 6- Ingresar con el usuario "pepe" pwd: "asd456" y comprobar sus permisos con los siguientes comandos.

### Leer la lista de productos. (PERMITIDO)

    db.productos.find()

### Eliminar los productos de la base. (NO AUTORIZADO)

    db.productos.deleteMany({})

*Muestra la leyenda*

<span style="color:red">**MongoServerError: not authorized on ecommerce to execute command { delete: "productos", deletes: [ { q: {}, limit: 0 } ], ordered: true, lsid: { id: UUID("1c8dbe47-50a1-41b0-9a79-0e6ba4b4d7d7") }, $db: "ecommerce" }**</span>.
