<!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Añadir y eliminar actividades</title>
    <link rel="stylesheet" type="text/css" href="./style.css">
  </head>
  <body>
    <h1>INTRODUZCA_LA_ACTIVIDAD</h1>
    
    <form onsubmit="return false;">
    <label><span class="text-black">Actividad</span></label>
    <input type="text" id="actividad"><br><br>
     </form>
    
    <button class="btnI">Enviar</button>
    
    <ul id="lista-actividades"></ul>
    <script src="./script.js"></script>
</body>
</html>
                                           #CSS

body {
  background-color: #000000;
  text-align: center;
  margin: 10px;
}

h1 {
  color: #0ef3a3;
}

.text-black {
  color: #fdfefe; 
}

input {
  padding: 8px;
  width: 250px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.btnI {  
  color: #000000;
  background-color: #0ef3a3;
  padding: 15px 35px;
  cursor: pointer;
  border-radius: 5px;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

li {
  background: #f8f9fa;
  padding: 10px;
  margin: 5px;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

button.eliminar {
  background-color: #0cc68a;
  color: white;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 5px;
}

                                           #JS

let inputActividad = document.querySelector("#actividad");
let btnAgregar = document.querySelector(".btnI");
let listaActividades = document.querySelector("#lista-actividades");

btnAgregar.addEventListener("click", function() {
    let texto = inputActividad.value.trim(); 

    if (texto === "") {
        alert("Escribe una actividad antes de agregarla :)");
        return;
    }

    let li = document.createElement("li");
    li.textContent = texto;

    let btnEliminar = document.createElement("button");
    btnEliminar.textContent = "X";
    btnEliminar.classList.add("eliminar");

    btnEliminar.addEventListener("click", function() {
        listaActividades.removeChild(li);
    });

    li.appendChild(btnEliminar);

    listaActividades.appendChild(li);

    inputActividad.value = "";
});

inputActividad.addEventListener("keypress", function(event) {
    if (event.key === "Enter") {
        btnAgregar.click();
    }
});
                                           
