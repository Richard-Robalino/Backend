
# Una de tipo GET (“/”) para presentar la información del grupo de trabajo.

```javascript
const express = require("express");
const app = express();
const PORT = process.env.PORT || 3000;

// Información del grupo de trabajo
app.get('/', (req, res) => {
    res.send("Desarrollo web - Grupo 1");
});
```

# Una de tipo GET (“/integrantes”) para que presente la información de los
integrantes del grupo.

```javascript
// Información de los integrantes
app.get('/integrantes', (req, res) => {
    const integrantes = [
        { id: 1, nombre: "Richard", apellido: "Robalino", edad: 25 },
        { id: 2, nombre: "Christian", apellido: "Marquez", edad: 21 },
        { id: 3, nombre: "Angel", apellido: "Villamil", edad: 21 },
        { id: 3, nombre: "Angelp", apellido: "Loor", edad: 21 }
    ];
    res.json(integrantes);
});
```

# Una de tipo GET (“/integrantes/:id”) para que presente la información de un
integrante del grupo.

```javascript
// Información de un integrante específico por id
app.get('/integrantes/:id', (req, res) => {
    const integrantes = [
        { id: 1, nombre: "Richard", apellido: "Robalino", edad: 25 },
        { id: 2, nombre: "Christian", apellido: "Marquez", edad: 21 },
        { id: 3, nombre: "Angel", apellido: "Villamil", edad: 21 },
        { id: 3, nombre: "Angelp", apellido: "Loor", edad: 21 }
    ];
    const integrante = integrantes.find(i => i.id === parseInt(req.params.id));
    
    if (integrante) {
        res.json(integrante);
    } else {
        res.status(404).send("Integrante no encontrado");
    }
});
```
# Una de tipo GET (“/products”) para que presente un HTML con algunos
productos que sean quemados.

```javascript
// Presentación de productos quemados en un HTML
app.get('/products', (req, res) => {
    res.send(`
        <h1>Catálogo de productos</h1>
        <p>Bienvenidos a nuestra tienda</p>
        <ul>
            <li>Producto 1: Laptop - $800</li>
            <li>Producto 2: Teléfono - $500</li>
            <li>Producto 3: Tablet - $300</li>
        </ul>
    `);
});

// Inicialización del servidor
app.listen(PORT, () => {
    console.log(`Server started on port ${PORT}`);
});
```









