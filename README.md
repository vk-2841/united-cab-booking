# united-cab-booking
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>United Cab Booking</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="booking-form">
    <h1>United Cab Ride Booking</h1>
    <form id="rideForm">
      <label for="pickup">Pickup Location:</label>
      <input type="text" id="pickup" required />

      <label for="drop">Drop Location:</label>
      <input type="text" id="drop" required />

      <label for="cabType">Cab Type:</label>
      <select id="cabType">
        <option value="standard">Standard</option>
        <option value="premium">Premium</option>
        <option value="van">Van</option>
      </select>

      <label for="time">Pickup Time:</label>
      <input type="datetime-local" id="time" required />

      <label for="contact">Contact Number:</label>
      <input type="tel" id="contact" required />

      <button type="submit">Book Ride</button>
    </form>
    <div id="confirmation" class="hidden"></div>
  </div>

  <script src="app.js"></script>
</body>
</html>
body {
  font-family: sans-serif;
  background-color: #f6c90e;
  padding: 2rem;
}

.booking-form {
  background-color: #fff;
  padding: 2rem;
  max-width: 400px;
  margin: 0 auto;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.booking-form h1 {
  text-align: center;
  margin-bottom: 1.5rem;
}

label {
  display: block;
  margin-top: 1rem;
  font-weight: bold;
}

input, select, button {
  width: 100%;
  padding: 0.5rem;
  margin-top: 0.5rem;
  border-radius: 5px;
  border: 1px solid #ccc;
}

button {
  background-color: #222;
  color: white;
  margin-top: 1.5rem;
  cursor: pointer;
}

.hidden {
  display: none;
}

#confirmation {
  margin-top: 2rem;
  padding: 1rem;
  background: #dff0d8;
  color: #3c763d;
  border: 1px solid #3c763d;
  border-radius: 5px;
}

document.getElementById('rideForm').addEventListener('submit', function(e) {
  e.preventDefault();

  const pickup = document.getElementById('pickup').value;
  const drop = document.getElementById('drop').value;
  const cabType = document.getElementById('cabType').value;
  const time = document.getElementById('time').value;
  const contact = document.getElementById('contact').value;

  const confirmation = `
    <h2>Ride Confirmed!</h2>
    <p><strong>From:</strong> ${pickup}</p>
    <p><strong>To:</strong> ${drop}</p>
    <p><strong>Cab Type:</strong> ${cabType}</p>
    <p><strong>Time:</strong> ${new Date(time).toLocaleString()}</p>
    <p><strong>Contact:</strong> ${contact}</p>
  `;

  document.getElementById('confirmation').innerHTML = confirmation;
  document.getElementById('confirmation').classList.remove('hidden');
  document.getElementById('rideForm').reset();
});
