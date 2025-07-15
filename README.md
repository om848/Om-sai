<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Bus Operator App</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      margin: 20px;
      background-color: #f2f2f2;
    }
    input, select, button, textarea {
      display: block;
      margin: 10px 0;
      padding: 10px;
      width: 100%;
      max-width: 500px;
      border-radius: 6px;
      border: 1px solid #ccc;
    }
    .section {
      border: 1px solid #ccc;
      border-radius: 10px;
      padding: 20px;
      background: white;
      margin-bottom: 30px;
    }
    button {
      background-color: #007bff;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
    nav {
      display: flex;
      justify-content: space-around;
      margin-bottom: 30px;
    }
    nav button {
      width: 30%;
    }
    .invoice-box {
      background: white;
      max-width: 800px;
      margin: auto;
      padding: 30px;
      border: 1px solid #eee;
      box-shadow: 0 0 10px rgba(0,0,0,.15);
    }
    .invoice-box table {
      width: 100%;
      border-collapse: collapse;
    }
    .invoice-box th, .invoice-box td {
      padding: 10px;
      border: 1px solid #ddd;
      text-align: left;
      font-size: 14px;
    }
    .invoice-box th {
      background-color: #eee;
    }
    .btn-print {
      background: #007bff;
      color: white;
      padding: 10px 20px;
      border: none;
      cursor: pointer;
      border-radius: 5px;
    }
  </style>
</head>
<body>  <nav>
    <button onclick="showSection('booking')">Booking</button>
    <button onclick="showSection('expense')">Expenses</button>
    <button onclick="showSection('bill')">Bill</button>
  </nav>  <div id="booking" class="section">
    <h2>🚌 Passenger Booking</h2>
    <label>Passenger Name</label>
    <input type="text" id="passenger">
    <label>From</label>
    <input type="text" id="from">
    <label>To</label>
    <input type="text" id="to">
    <label>Fare</label>
    <input type="number" id="fare">
    <label>Passenger Photo</label>
    <input type="file" id="photo" accept="image/*" capture="environment">
    <label>Location</label>
    <input type="text" id="location" readonly>
    <label>Date & Time</label>
    <input type="text" id="datetime" readonly>
    <button onclick="submitBooking()">Submit Booking</button>
  </div>  <div id="expense" class="section" style="display:none">
    <h2>💸 Trip Expense Entry</h2>
    <label>Expense Type</label>
    <select id="type">
      <option value="Diesel">Diesel</option>
      <option value="Toll">Toll</option>
      <option value="Police">Police</option>
      <option value="Other">Other</option>
    </select>
    <label>Amount</label>
    <input type="number" id="amount">
    <label>Description</label>
    <textarea id="desc"></textarea>
    <label>Proof Photo</label>
    <input type="file" id="expensePhoto" accept="image/*" capture="environment">
    <label>Location</label>
    <input type="text" id="expenseLocation" readonly>
    <label>Date & Time</label>
    <input type="text" id="expenseTime" readonly>
    <button onclick="submitExpense()">Submit Expense</button>
  </div>  <div id="bill" class="invoice-box" style="display:none">
    <h1>Bus Agency Invoice</h1>
    <table>
      <tr><th>Passenger</th><th>From</th><th>To</th><th>Fare</th></tr>
      <tr><td>Rahul</td><td>Mumbai</td><td>Pune</td><td>500</td></tr>
      <tr><td>Anjali</td><td>Mumbai</td><td>Pune</td><td>500</td></tr>
    </table>
    <table>
      <tr><th>Expense</th><th>Description</th><th>Amount</th></tr>
      <tr><td>Diesel</td><td>Fuel</td><td>2000</td></tr>
      <tr><td>Toll</td><td>Express Toll</td><td>300</td></tr>
    </table>
    <p style="text-align:right"><strong>Total Fare:</strong> ₹1000</p>
    <p style="text-align:right"><strong>Total Expenses:</strong> ₹2300</p>
    <p style="text-align:right; font-size: 18px;"><strong>Net Profit:</strong> ₹-1300</p>
    <button class="btn-print" onclick="window.print()">🖨️ Print / Download</button>
  </div>  <script>
    function updateDateTime() {
      const now = new Date();
      document.getElementById('datetime').value = now.toLocaleString();
      document.getElementById('expenseTime').value = now.toLocaleString();
    }

    function updateLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(pos => {
          const loc = `${pos.coords.latitude}, ${pos.coords.longitude}`;
          document.getElementById('location').value = loc;
          document.getElementById('expenseLocation').value = loc;
        });
      }
    }

    window.onload = () => {
      updateDateTime();
      updateLocation();
    };

    function showSection(id) {
      document.getElementById('booking').style.display = 'none';
      document.getElementById('expense').style.display = 'none';
      document.getElementById('bill').style.display = 'none';
      document.getElementById(id).style.display = 'block';
    }

    function submitBooking() {
      alert('Booking submitted. Link to database logic here.');
    }

    function submitExpense() {
      alert('Expense submitted. Link to database logic here.');
    }
  </script></body>
</html>
