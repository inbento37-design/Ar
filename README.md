<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Generador de Configuración para Free Fire</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 300px;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        p {
            text-align: center;
            color: #666;
        }
        form {
            display: flex;
            flex-direction: column;
        }
        label {
            margin-top: 10px;
            color: #333;
        }
        input, select {
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        input[type="submit"] {
            background-color: #007BFF;
            color: white;
            border: none;
            cursor: pointer;
            margin-top: 20px;
        }
        input[type="submit"]:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Generador de Configuración para Free Fire</h1>
        <p>Descarga el archivo de configuración personalizado para Free Fire.</p>
        <form action="/generate_config" method="post">
            <label for="username">Nombre de Usuario:</label>
            <input type="text" id="username" name="username" required>
            <label for="aimbot">Aimbot:</label>
            <select id="aimbot" name="aimbot">
                <option value="true">Activado</option>
                <option value="false">Desactivado</option>
            </select>
            <label for="wallhack">Wallhack:</label>
            <select id="wallhack" name="wallhack">
                <option value="true">Activado</option>
                <option value="false">Desactivado</option>
            </select>
            <label for="auto_headshot">Auto Headshot:</label>
            <select id="auto_headshot" name="auto_headshot">
                <option value="true">Activado</option>
                <option value="false">Desactivado</option>
            </select>
            <input type="submit" value="Generar Configuración">
        </form>
    </div>
</body>
</html>
