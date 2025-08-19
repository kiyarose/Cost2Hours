<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Work Hours Calculator</title>
  
  <!-- Google Fonts + Material Icons -->
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap" rel="stylesheet">
  <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">

  <style>
    body {
      font-family: 'Roboto', sans-serif;
      background: #f5f5f5;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }

    .card {
      background: #fff;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.15);
      padding: 30px;
      width: 350px;
      max-width: 90%;
    }

    h2 {
      margin-top: 0;
      color: #333;
      text-align: center;
    }

    .input-group {
      display: flex;
      align-items: center;
      margin: 15px 0;
    }

    .input-group .material-icons {
      margin-right: 10px;
      color: #666;
    }

    .input-group input {
      flex: 1;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 14px;
    }

    button {
      background: #6200ea;
      color: #fff;
      border: none;
      padding: 12px;
      width: 100%;
      border-radius: 6px;
      font-size: 16px;
      cursor: pointer;
      margin-top: 15px;
      transition: background 0.2s;
    }

    button:hover {
      background: #4500b5;
    }

    .results {
      margin-top: 20px;
      padding: 15px;
      background: #f1f1f1;
      border-radius: 6px;
      text-align: center;
    }

    .results p {
      margin: 8px 0;
      font-size: 15px;
    }
  </style>
</head>
<body>
  <div class="card">
    <h2><span class="material-icons">calculate</span> Work Hours Calculator</h2>

    <div class="input-group">
      <span class="material-icons">attach_money</span>
      <input type="number" id="wage" placeholder="Hourly Wage ($)">
    </div>

    <div class="input-group">
      <span class="material-icons">shopping_cart</span>
      <input type="number" id="price" placeholder="Item Price ($)">
    </div>

    <div class="input-group">
      <span class="material-icons">schedule</span>
      <input type="number" id="hoursPerDay" placeholder="Hours per Day (optional)">
    </div>

    <button onclick="calculate()">Calculate</button>

    <div class="results" id="results"></div>
  </div>

  <script>
    function calculate() {
      const wage = parseFloat(document.getElementById('wage').value);
      const price = parseFloat(document.getElementById('price').value);
      const hoursPerDay = parseFloat(document.getElementById('hoursPerDay').value);

      if (!wage || !price || wage <= 0 || price <= 0) {
        document.getElementById('results').innerHTML = "<p style='color:red;'>Please enter valid numbers for wage and price.</p>";
        return;
      }

      const totalHours = (price / wage).toFixed(2);
      let resultHTML = `<p><b>${totalHours}</b> hours needed to afford this item.</p>`;

      if (hoursPerDay && hoursPerDay > 0) {
        const totalDays = (totalHours / hoursPerDay).toFixed(2);
        resultHTML += `<p>That’s about <b>${totalDays}</b> work days (${hoursPerDay} hrs/day).</p>`;
      }

      document.getElementById('results').innerHTML = resultHTML;
    }
  </script>
</body>
</html>
