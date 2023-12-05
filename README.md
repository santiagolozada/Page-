<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tienda de Productos Naturales</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f5f5f5;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #4CAF50;
            padding: 1em;
            text-align: center;
            color: white;
            font-size: 1.5em;
        }

        #productos {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
            padding: 20px;
        }

        .producto {
            border: 1px solid #ccc;
            border-radius: 5px;
            padding: 10px;
            margin: 10px;
            max-width: 200px;
            text-align: center;
            background-color: white;
        }

        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 8px 16px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 14px;
            margin: 4px 2px;
            cursor: pointer;
            border-radius: 4px;
        }

        #carrito {
            margin-top: 20px;
            padding: 20px;
            background-color: #fff;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Tienda de Productos Naturales</h1>
    </header>

    <div id="productos"></div>
    <div id="carrito"></div>

    <script>
        const productos = [
            { id: 1, nombre: 'Producto 1', precio: 10 },
            { id: 2, nombre: 'Producto 2', precio: 15 },
            { id: 3, nombre: 'Producto 3', precio: 20 }
            // Agrega más productos según sea necesario
        ];

        const carrito = [];

        function mostrarProductos() {
            const productosContainer = document.getElementById('productos');
            productosContainer.innerHTML = '';

            productos.forEach(producto => {
                const productoElement = document.createElement('div');
                productoElement.className = 'producto';
                productoElement.innerHTML = `
                    <h3>${producto.nombre}</h3>
                    <p>Precio: $${producto.precio}</p>
                    <button onclick="agregarAlCarrito(${producto.id})">Agregar al carrito</button>
                `;
                productosContainer.appendChild(productoElement);
            });
        }

        function mostrarCarrito() {
            const carritoContainer = document.getElementById('carrito');
            carritoContainer.innerHTML = '';

            carrito.forEach(item => {
                const carritoElement = document.createElement('div');
                carritoElement.innerHTML = `${item.nombre} - $${item.precio}`;
                carritoContainer.appendChild(carritoElement);
            });
        }

        function agregarAlCarrito(id) {
            const productoSeleccionado = productos.find(producto => producto.id === id);
            if (productoSeleccionado) {
                carrito.push({ id: productoSeleccionado.id, nombre: productoSeleccionado.nombre, precio: productoSeleccionado.precio });
                mostrarCarrito();
            }
        }

        // Inicializar la interfaz
        mostrarProductos();
    </script>
</body>
</html>
