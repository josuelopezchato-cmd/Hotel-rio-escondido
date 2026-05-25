# Hotel-rio-escondido
Registro para huéspedes 

<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Hotel Río Escondido - Reservación</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>

*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

body{
  font-family:'Poppins',sans-serif;
  background:#f3f6f9;
  color:#333;
}

/* HEADER */

header{
  background:linear-gradient(135deg,#1f4d2e,#2c5f2d);
  color:white;
  padding:35px 20px;
  text-align:center;
  box-shadow:0 4px 12px rgba(0,0,0,0.15);
}

header h1{
  font-size:32px;
  margin-bottom:8px;
}

header p{
  opacity:0.9;
  font-size:15px;
}

/* CONTAINER */

.container{
  max-width:1000px;
  margin:30px auto;
  padding:0 20px;
}

.section{
  background:white;
  border-radius:18px;
  padding:30px;
  margin-bottom:25px;
  box-shadow:0 5px 18px rgba(0,0,0,0.08);
}

.section h2{
  color:#2c5f2d;
  margin-bottom:15px;
  border-bottom:3px solid #2c5f2d;
  padding-bottom:10px;
}

/* HABITACIONES */

.rooms-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(120px,1fr));
  gap:15px;
  margin-top:20px;
}

.room{
  padding:18px 10px;
  border-radius:12px;
  text-align:center;
  font-weight:600;
  transition:0.25s;
  cursor:pointer;
  border:2px solid transparent;
}

.room:hover{
  transform:translateY(-4px);
}

.DIS{
  background:#4CAF50;
  color:white;
}

.HOS{
  background:#2196F3;
  color:white;
  cursor:not-allowed;
}

.selected{
  border:3px solid #ff9800;
  transform:scale(1.05);
}

/* FORMULARIO */

form{
  display:grid;
  gap:18px;
}

.form-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
  gap:18px;
}

label{
  display:block;
  margin-bottom:6px;
  font-weight:600;
  font-size:14px;
}

input, select{
  width:100%;
  padding:12px;
  border-radius:10px;
  border:1px solid #ccc;
  font-size:14px;
  transition:0.2s;
}

input:focus,
select:focus{
  border-color:#2c5f2d;
  outline:none;
  box-shadow:0 0 0 3px rgba(44,95,45,0.15);
}

/* TARJETAS */

.payment-box{
  background:#f8fafb;
  border:1px solid #ddd;
  padding:20px;
  border-radius:15px;
}

.cards{
  display:flex;
  gap:10px;
  margin-bottom:15px;
}

.card-logo{
  background:white;
  border:1px solid #ddd;
  padding:8px 14px;
  border-radius:8px;
  font-weight:600;
  font-size:14px;
}

/* BOTON */

button{
  background:linear-gradient(135deg,#2c5f2d,#1f4d2e);
  color:white;
  border:none;
  padding:15px;
  border-radius:12px;
  font-size:16px;
  font-weight:600;
  cursor:pointer;
  transition:0.25s;
}

button:hover{
  transform:translateY(-2px);
  opacity:0.95;
}

button:disabled{
  background:#999;
  cursor:not-allowed;
}

/* ALERTAS */

.alert{
  display:none;
  padding:14px;
  border-radius:10px;
  margin-top:15px;
  font-weight:500;
}

.success{
  background:#d4edda;
  color:#155724;
}

.error{
  background:#f8d7da;
  color:#721c24;
}

/* RESUMEN */

.summary{
  background:#eef5ef;
  border-left:5px solid #2c5f2d;
  padding:15px;
  border-radius:10px;
  margin-top:20px;
}

.summary p{
  margin:6px 0;
}

/* RESPONSIVE */

@media(max-width:600px){

  header h1{
    font-size:25px;
  }

  .section{
    padding:22px;
  }

}

</style>
</head>

<body>

<header>
  <h1>HOTEL RÍO ESCONDIDO</h1>
  <p>Reservación en línea rápida y segura</p>
</header>

<div class="container">

  <!-- HABITACIONES -->

  <div class="section">

    <h2>1. Selecciona tu habitación</h2>

    <p>
      Habitaciones disponibles en verde.
      Habitaciones ocupadas en azul.
    </p>

    <div class="rooms-grid" id="roomsGrid"></div>

  </div>

  <!-- FORMULARIO -->

  <div class="section">

    <h2>2. Completa tu reservación</h2>

    <form id="bookingForm">

      <input type="hidden" id="selectedRoom">

      <div class="form-grid">

        <div>
          <label>Nombre completo</label>
          <input type="text" id="nombre" required>
        </div>

        <div>
          <label>Correo electrónico</label>
          <input type="email" id="email" required>
        </div>

        <div>
          <label>Teléfono</label>
          <input type="tel" id="telefono" required>
        </div>

        <div>
          <label>Fecha de entrada</label>
          <input type="date" id="checkin" required>
        </div>

        <div>
          <label>Fecha de salida</label>
          <input type="date" id="checkout" required>
        </div>

      </div>

      <!-- METODO DE PAGO -->

      <div class="payment-box">

        <h3 style="margin-bottom:15px;">Método de Pago</h3>

        <div class="cards">
          <div class="card-logo">💳 VISA</div>
          <div class="card-logo">💳 MasterCard</div>
        </div>

        <div class="form-grid">

          <div>
            <label>Nombre del titular</label>
            <input type="text" id="titular" required>
          </div>

          <div>
            <label>Número de tarjeta</label>
            <input 
              type="text"
              id="tarjeta"
              maxlength="19"
              placeholder="1234 5678 9012 3456"
              required
            >
          </div>

          <div>
            <label>Fecha de expiración</label>
            <input type="month" id="expiracion" required>
          </div>

          <div>
            <label>CVV</label>
            <input 
              type="password"
              id="cvv"
              maxlength="4"
              placeholder="123"
              required
            >
          </div>

        </div>

      </div>

      <!-- RESUMEN -->

      <div class="summary" id="summary">
        <p><strong>Habitación:</strong> No seleccionada</p>
        <p><strong>Total:</strong> $0 MXN</p>
      </div>

      <button type="submit" id="btnReservar" disabled>
        Confirmar Reservación
      </button>

    </form>

    <div class="alert success" id="alertSuccess">
      ✅ Reservación confirmada correctamente.
    </div>

    <div class="alert error" id="alertError">
      ⚠️ Completa todos los campos correctamente.
    </div>

  </div>

</div>

<script>

const TOTAL_ROOMS = 15;
const ROOM_PREFIX = "10";
const ROOM_PRICE = 850;

let selectedRoom = null;

/* RENDER HABITACIONES */

function renderRooms(){

  const grid = document.getElementById('roomsGrid');
  grid.innerHTML = '';

  const bookings = JSON.parse(
    localStorage.getItem('rioBookings') || '[]'
  );

  for(let i=1; i<=TOTAL_ROOMS; i++){

    const roomNum = ROOM_PREFIX + String(i).padStart(2,'0');

    const isBooked = bookings.some(
      b => b.room === roomNum
    );

    const status = isBooked ? 'HOS' : 'DIS';

    const room = document.createElement('div');

    room.className = `room ${status}`;
    room.textContent = roomNum;

    if(status === 'DIS'){

      room.onclick = () => selectRoom(roomNum, room);

    }

    grid.appendChild(room);

  }

}

/* SELECCIONAR */

function selectRoom(roomNum, element){

  document.querySelectorAll('.room')
    .forEach(r => r.classList.remove('selected'));

  element.classList.add('selected');

  selectedRoom = roomNum;

  document.getElementById('selectedRoom').value = roomNum;

  document.getElementById('btnReservar').disabled = false;

  updateSummary();

}

/* RESUMEN */

function updateSummary(){

  const summary = document.getElementById('summary');

  summary.innerHTML = `
    <p><strong>Habitación:</strong> ${selectedRoom}</p>
    <p><strong>Total:</strong> $${ROOM_PRICE} MXN</p>
  `;

}

/* FORMATEAR TARJETA */

document.getElementById('tarjeta')
.addEventListener('input', function(e){

  let value = e.target.value
    .replace(/\D/g,'')
    .substring(0,16);

  value = value.replace(/(.{4})/g,'$1 ').trim();

  e.target.value = value;

});

/* VALIDAR FECHAS */

document.getElementById('checkin').min =
  new Date().toISOString().split('T')[0];

document.getElementById('checkout').min =
  new Date().toISOString().split('T')[0];

/* RESERVAR */

document.getElementById('bookingForm')
.addEventListener('submit', function(e){

  e.preventDefault();

  const booking = {

    room: document.getElementById('selectedRoom').value,
    nombre: document.getElementById('nombre').value,
    email: document.getElementById('email').value,
    telefono: document.getElementById('telefono').value,
    checkin: document.getElementById('checkin').value,
    checkout: document.getElementById('checkout').value,

    pago: {
      titular: document.getElementById('titular').value,
      tarjeta: document.getElementById('tarjeta').value
    },

    fechaRegistro: new Date().toLocaleString('es-MX')

  };

  if(!booking.room){

    document.getElementById('alertError')
      .style.display = 'block';

    return;

  }

  const bookings = JSON.parse(
    localStorage.getItem('rioBookings') || '[]'
  );

  bookings.push(booking);

  localStorage.setItem(
    'rioBookings',
    JSON.stringify(bookings)
  );

  document.getElementById('alertSuccess')
    .style.display = 'block';

  document.getElementById('alertError')
    .style.display = 'none';

  this.reset();

  selectedRoom = null;

  document.getElementById('summary').innerHTML = `
    <p><strong>Habitación:</strong> No seleccionada</p>
    <p><strong>Total:</strong> $0 MXN</p>
  `;

  document.getElementById('btnReservar')
    .disabled = true;

  document.querySelectorAll('.room')
    .forEach(r => r.classList.remove('selected'));

  setTimeout(() => {

    document.getElementById('alertSuccess')
      .style.display = 'none';

    renderRooms();

  },2000);

});

/* INICIAR */

renderRooms();

</script>

</body>
</html>
