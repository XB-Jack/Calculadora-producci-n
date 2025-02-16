</head>
<body>
    <div class="container">
        <h2>Calculadora de Producción</h2>
        <label for="piezas">Número de piezas:</label>
        <input type="number" id="piezas" placeholder="Ingrese la cantidad de piezas">
        
        <label for="tiempoPorPieza">Tiempo por pieza (min):</label>
        <input type="number" id="tiempoPorPieza" value="3.5">
        
        <label for="eficiencia">Eficiencia de la máquina (%):</label>
        <input type="number" id="eficiencia" value="90">
        
        <label for="ajustesCada">Ajustes cada (piezas):</label>
        <input type="number" id="ajustesCada" value="25">
        
        <label for="tiempoAjuste">Tiempo por ajuste (min):</label>
        <input type="number" id="tiempoAjuste" value="5">
        
        <label for="tiempoInspeccion">Tiempo de inspección (min):</label>
        <input type="number" id="tiempoInspeccion" value="10">
        
        <button onclick="calcularTiempo()">Calcular</button>
        <h3>Resultados:</h3>
        <p id="resultado"></p>
    </div>

    <script>
        function calcularTiempo() {
            let piezas = parseInt(document.getElementById("piezas").value);
            let tiempoPorPieza = parseFloat(document.getElementById("tiempoPorPieza").value);
            let eficiencia = parseFloat(document.getElementById("eficiencia").value) / 100;
            let ajustesCada = parseInt(document.getElementById("ajustesCada").value);
            let tiempoAjuste = parseFloat(document.getElementById("tiempoAjuste").value);
            let tiempoInspeccion = parseFloat(document.getElementById("tiempoInspeccion").value);
            
            if (isNaN(piezas) || piezas <= 0 || isNaN(tiempoPorPieza) || isNaN(eficiencia) || isNaN(ajustesCada) || isNaN(tiempoAjuste) || isNaN(tiempoInspeccion)) {
                document.getElementById("resultado").innerText = "Ingrese valores válidos en todos los campos.";
                return;
            }
            
            let tiempoNeto = piezas * tiempoPorPieza;
            let tiempoReal = tiempoNeto / eficiencia;
            let numAjustes = Math.floor(piezas / ajustesCada);
            let tiempoTotal = tiempoReal + (numAjustes * tiempoAjuste) + tiempoInspeccion;
            let horas = Math.floor(tiempoTotal / 60);
            let minutos = Math.round(tiempoTotal % 60);

            document.getElementById("resultado").innerText = `Tiempo total: ${horas} horas y ${minutos} minutos.`;
        }
    </script>
</body>
</html>
