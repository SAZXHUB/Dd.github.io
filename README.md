<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Attack Console</title>
</head>
<body>

<h1>Attack Console</h1>

<div id="stats">
  <h2>Attack Stats</h2>
  <p>Total TCP Attacks: <span id="totalTcpAttacks">0</span></p>
  <p>Total UDP Attacks: <span id="totalUdpAttacks">0</span></p>
  <p>Total ICMP Attacks: <span id="totalIcmpAttacks">0</span></p>
</div>

<h2>Start Attack</h2>
<form id="attackForm">
  <label for="password">Enter Password:</label><br>
  <input type="password" id="password" name="password" required><br><br>
  
  <label for="website">Enter Website URL:</label><br>
  <input type="text" id="website" name="website" required><br><br>
  
  <label for="threads">Enter Number of Threads:</label><br>
  <input type="number" id="threads" name="threads" required><br><br>
  
  <label for="use_tcp">Use TCP Attack:</label>
  <input type="checkbox" id="use_tcp" name="use_tcp" value="true"><br>
  
  <label for="use_tcp2">Use TCPv2 Attack:</label>
  <input type="checkbox" id="use_tcp2" name="use_tcp2" value="true"><br>
  
  <label for="use_tcp3">Use TCPv3 Attack:</label>
  <input type="checkbox" id="use_tcp3" name="use_tcp3" value="true"><br>
  
  <label for="use_udp">Use UDP Attack:</label>
  <input type="checkbox" id="use_udp" name="use_udp" value="true"><br>
  
  <label for="use_udp2">Use UDPv2 Attack:</label>
  <input type="checkbox" id="use_udp2" name="use_udp2" value="true"><br>
  
  <label for="use_udp3">Use UDPv3 Attack:</label>
  <input type="checkbox" id="use_udp3" name="use_udp3" value="true"><br>
  
  <label for="use_icmp">Use ICMP Attack:</label>
  <input type="checkbox" id="use_icmp" name="use_icmp" value="true"><br><br>
  
  <input type="submit" value="Start Attack">
</form>

<div id="responseMessage"></div>

<script>
// Function to send attack request
function sendAttackRequest(formData) {
  fetch('/start_attack', {
    method: 'POST',
    body: formData
  })
  .then(response => response.json())
  .then(data => {
    document.getElementById('responseMessage').innerText = data.message;
  })
  .catch(error => {
    console.error('Error:', error);
    document.getElementById('responseMessage').innerText = 'Error occurred';
  });
}

// Handle attack form submission
document.getElementById('attackForm').addEventListener('submit', function(event) {
  event.preventDefault();
  var formData = new FormData(this);
  sendAttackRequest(formData);
});
</script>

</body>
</html>
