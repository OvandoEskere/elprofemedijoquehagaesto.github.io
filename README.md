<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Presupuesto de Productos</title>
    <style>
        body { font-family: Arial, sans-serif; }
        input, select { margin-bottom: 10px; width: 100px; }
        table { width: 100%; margin-bottom: 20px; }
        th, td { padding: 10px; text-align: center; border: 1px solid #ddd; }
        button { margin-top: 20px; }
    </style>
</head>
<body>
    <h1>Generador de Presupuestos</h1>
    <form id="presupuestoForm">
        <label for="cliente">Cliente:</label>
        <input type="text" id="cliente" name="cliente" required><br>

        <table>
            <thead>
                <tr>
                    <th>Producto</th>
                    <th>Cantidad</th>
                    <th>Precio Unitario</th>
                </tr>
            </thead>
            <tbody id="productos">
                <tr>
                    <td>Producto 1</td>
                    <td><input type="number" name="cantidad" placeholder="Cantidad" required></td>
                    <td><input type="number" name="precioUnitario" placeholder="Precio Unitario" required></td>
                </tr>
                <tr>
                    <td>Producto 2</td>
                    <td><input type="number" name="cantidad" placeholder="Cantidad" required></td>
                    <td><input type="number" name="precioUnitario" placeholder="Precio Unitario" required></td>
                </tr>
                <tr>
                    <td>Producto 3</td>
                    <td><input type="number" name="cantidad" placeholder="Cantidad" required></td>
                    <td><input type="number" name="precioUnitario" placeholder="Precio Unitario" required></td>
                </tr>
                <tr>
                    <td>Producto 4</td>
                    <td><input type="number" name="cantidad" placeholder="Cantidad" required></td>
                    <td><input type="number" name="precioUnitario" placeholder="Precio Unitario" required></td>
                </tr>
                <tr>
                    <td>Producto 5</td>
                    <td><input type="number" name="cantidad" placeholder="Cantidad" required></td>
                    <td><input type="number" name="precioUnitario" placeholder="Precio Unitario" required></td>
                </tr>
            </tbody>
        </table>

        <label>Subtotal: $</label><span id="subtotal">0.00</span><br>
        <label>IVA (21%): $</label><span id="iva">0.00</span><br>
        <label>Total: $</label><span id="total">0.00</span><br>
        <label>Cuota 12 meses: $</label><span id="cuota12">0.00</span><br>
        <label>Cuota 18 meses: $</label><span id="cuota18">0.00</span><br>

        <button type="button" onclick="calcularTotales()">Calcular Total</button>
        <button type="button" onclick="imprimirPresupuesto()">Imprimir Presupuesto</button>
    </form>

    <script>
        function calcularTotales() {
            let subtotal = 0;
            const productos = document.querySelectorAll('#productos tr');

            productos.forEach(tr => {
                const cantidad = tr.querySelector('input[name="cantidad"]').value || 0;
                const precioUnitario = tr.querySelector('input[name="precioUnitario"]').value || 0;
                subtotal += cantidad * precioUnitario;
            });

            const iva = subtotal * 0.21;
            const total = subtotal + iva;
            const cuota12 = total / 12;
            const cuota18 = total * 1.75 / 18; // 75% de interés

            document.getElementById('subtotal').textContent = subtotal.toFixed(2);
            document.getElementById('iva').textContent = iva.toFixed(2);
            document.getElementById('total').textContent = total.toFixed(2);
            document.getElementById('cuota12').textContent = cuota12.toFixed(2);
            document.getElementById('cuota18').textContent = cuota18.toFixed(2);
        }

        function imprimirPresupuesto() {
            window.print();
        }
    </script>
</body>
</html>
