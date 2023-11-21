# API-Call-using-fetch---v3
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>University Search</title>
    <style>

body {
    font-family: 'Arial', sans-serif;
    margin: 20px;
}

label {
    margin-right: 10px;
}

#country-select {
    margin-bottom: 20px;
}

.university-card {
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
    margin: 10px;
    width: 200px;
    display: inline-block;
}

ul {
    padding: 0;
    list-style: none;
}

li {
    margin-bottom: 5px;
}

    </style>
</head>
<body>

    <label for="country-select">Select a country:</label>
    <select id="country-select" onchange="getUniversities()">
        <option value="India">India</option>

    </select>

    <div id="universities-container"></div>

    <script>
        function getUniversities() {

            const selectedCountry = document.getElementById('country-select').value;

            fetch(`https://universities.hipolabs.com/search?country=${selectedCountry}`)
                .then(response => response.json())
                .then(data => {

                    displayUniversities(data);
                })
                .catch(error => {
                    console.error('Error fetching universities:', error);
                });
        }
        
        function displayUniversities(universities) {
            const universitiesContainer = document.getElementById('universities-container');
            universitiesContainer.innerHTML = ''; 
        
            universities.forEach(university => {
                const card = document.createElement('div');
                card.classList.add('university-card');
        
                const name = document.createElement('p');
                name.textContent = university.name;
                card.appendChild(name);
        
                const domains = document.createElement('ul');
                university.domains.forEach(domain => {
                    const domainItem = document.createElement('li');
                    domainItem.textContent = domain;
                    domains.appendChild(domainItem);
                });
                card.appendChild(domains);
        
                universitiesContainer.appendChild(card);
            });
        }
        
    </script>
</body>
</html>

```
# output
![Screenshot (82)](https://github.com/21002624/API-Call-using-fetch---v3/assets/113762183/2d3064b2-d25c-41f9-91c3-17a055549b37)
