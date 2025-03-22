<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo Betting Site</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <h1>Welcome to Demo Betting Website</h1>
    
    <div id="matches">
        <h2>Upcoming Matches</h2>
        <ul id="match-list"></ul>
    </div>

    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: #f4f4f4;
}
h1 {
    color: #333;
}
#matches {
    background: white;
    padding: 20px;
    margin: 20px auto;
    width: 80%;
    border-radius: 5px;
}
button {
    padding: 8px 15px;
    background: green;
    color: white;
    border: none;
    cursor: pointer;
    margin: 5px;
}
[
    { "id": 1, "team1": "India", "team2": "Australia", "odds1": 1.5, "odds2": 2.5 },
    { "id": 2, "team1": "Brazil", "team2": "Germany", "odds1": 1.8, "odds2": 2.2 }
]
document.addEventListener("DOMContentLoaded", function() {
    fetch('data.json')
    .then(response => response.json())
    .then(matches => {
        let matchList = document.getElementById("match-list");
        matches.forEach(match => {
            let li = document.createElement("li");
            li.innerHTML = `
                ${match.team1} vs ${match.team2} 
                | Odds: ${match.odds1} - ${match.odds2} 
                <button onclick="placeBet('${match.team1}')">Bet on ${match.team1}</button> 
                <button onclick="placeBet('${match.team2}')">Bet on ${match.team2}</button>
            `;
            matchList.appendChild(li);
        });
    });
});

function placeBet(team) {
    alert("Bet placed on: " + team);
}
