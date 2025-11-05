# registroasitencia_casetagam
Registro de asistencia
<title>Escaneando...</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body { font-family: Arial; text-align: center; margin-top: 50px; }
    #status { margin-top: 20px; color: green; }
  </style>
</head>
<body>
  <h1>Escaneando QR...</h1>
  <p id="status">Obteniendo ubicación...</p>

  <script>
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(success, error);
    } else {
      document.getElementById("status").innerHTML = "Tu celular no soporta ubicación";
    }

    function success(position) {
      const data = {
        lat: position.coords.latitude,
        lon: position.coords.longitude,
        time: new Date().toLocaleString('es-PE'),
        device: navigator.userAgent
      };

      ffetch('https://script.google.com/macros/s/AKfycbx.../exec', {
  method: 'POST',
  mode: 'no-cors',
  body: JSON.stringify(data)
.then(() => {
  document.getElementById("status").innerHTML = "Datos enviados: " + data.time;
.catch(() => {
  document.getElementById("status").innerHTML = "Enviado (puede tardar 5 seg en aparecer)";
    function error() {
      document.getElementById("status").innerHTML = "Necesitas permitir la ubicación";
  </script>
</body>
</html>
