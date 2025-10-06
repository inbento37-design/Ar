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
        <p>Personaliza tu configuración y descarga el archivo.</p>
        <form id="configForm">
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
        <a id="downloadLink" style="display:none;">Descargar Configuración</a>
    </div>

    <script>
        document.getElementById('configForm').addEventListener('submit', function(event) {
            event.preventDefault();

            const username = document.getElementById('username').value;
            const aimbot = document.getElementById('aimbot').value === 'true';
            const wallhack = document.getElementById('wallhack').value === 'true';
            const auto_headshot = document.getElementById('auto_headshot').value === 'true';

            const configContent = `[GameSettings]
username=${username}
aimbot_enabled=${aimbot}
wallhack_enabled=${wallhack}
auto_headshot_enabled=${auto_headshot}
aimbot_sensitivity=0.8
aimbot_smoothness=0.3
aimbot_fov=80
aimbot_recoil_control=0.7
aimbot_aim_key=mouse1
aimbot_predictive_aim=true
aimbot_predictive_factor=0.5

[AdvancedSettings]
enemy_color_detection=true
enemy_colors=255,0,0,0,255,0
enemy_detection_threshold=127
enemy_tracking=true
enemy_tracking_speed=0.7

[PerformanceSettings]
performance_mode=true
update_interval=50
max_enemies_to_track=5

[DebugSettings]
debug_mode=false
log_level=1
log_file=aimbot_debug.log

[Hotkeys]
toggle_aimbot_key=F1
reload_config_key=F3
exit_key=Esc`;

            const blob = new Blob([configContent], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const downloadLink = document.getElementById('downloadLink');
            downloadLink.href = url;
            downloadLink.download = `freefire_config_${username}.txt`;
            downloadLink.style.display = 'block';
            downloadLink.click();
        });
    </script>
</body>
</html>
