# Fetch Pokemon Data - README

## Description
This JavaScript code defines an asynchronous function `fetchData` that fetches data about a Pokémon from the PokeAPI based on user input and displays the Pokémon's sprite on a webpage.

## Functionality
- **Input Handling**: The function retrieves the Pokémon name entered by the user in an input field.
- **API Call**: It makes an asynchronous request to the PokeAPI to fetch data for the specified Pokémon.
- **Error Handling**: If the API request fails, an error is caught and logged to the console.
- **Display**: On a successful fetch, the Pokémon's sprite is displayed on the webpage.

---

## Requirements
- A modern web browser that supports JavaScript and ES6 features (such as `async/await`).
- Internet connection to access the PokeAPI.

---

## Installation and Setup

### 1. HTML Structure
Ensure your HTML file contains the necessary elements:

```html
<input type="text" id="pokemonNames" placeholder="Enter Pokémon name">
<button onclick="fetchData()">Fetch Pokémon</button>
<img id="pokemonSprite" style="display:none;" alt="Pokémon Sprite">
2. JavaScript
Include the fetchData function in a script tag or a separate JavaScript file:

html
Copy code
<script>
    async function fetchData() {
        try {
            const pokemonName = document.getElementById("pokemonNames").value.toLowerCase();
            const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonName}`);
            if (!response.ok) {
                throw new Error("Failed to fetch data from PokeAPI");
            }
            const data = await response.json();
            const pokemonSprite = data.sprites.front_default;
            const imgElement = document.getElementById('pokemonSprite');
            imgElement.src = pokemonSprite;
            imgElement.style.display = "block";
        } catch (error) {
            console.error(error);
        }
    }
</script>
3. Styling
Optionally, add CSS to style the input, button, and image elements as desired.

Usage
Open the HTML file in a web browser.
Enter the name of a Pokémon in the input field.
Click the "Fetch Pokémon" button.
The sprite of the specified Pokémon will be displayed below the input field.
Error Handling
If the entered Pokémon name does not exist or there is a network issue, an error message will be logged to the console.
The image element will remain hidden if an error occurs.
Additional Notes
Ensure that the PokeAPI endpoint (https://pokeapi.co/api/v2/pokemon/) is accessible from your network.
The Pokémon name input is case-insensitive; it will be converted to lowercase before making the API call.
This example displays only the front default sprite of the Pokémon.
Example
html
Copy code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fetch Pokémon Data</title>
</head>
<body>
    <input type="text" id="pokemonNames" placeholder="Enter Pokémon name">
    <button onclick="fetchData()">Fetch Pokémon</button>
    <img id="pokemonSprite" style="display:none;" alt="Pokémon Sprite">
    <script>
        async function fetchData() {
            try {
                const pokemonName = document.getElementById("pokemonNames").value.toLowerCase();
                const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonName}`);
                if (!response.ok) {
                    throw new Error("Failed to fetch data from PokeAPI");
                }
                const data = await response.json();
                const pokemonSprite = data.sprites.front_default;
                const imgElement = document.getElementById('pokemonSprite');
                imgElement.src = pokemonSprite;
                imgElement.style.display = "block";
            } catch (error) {
                console.error(error);
            }
        }
    </script>
</body>
</html>
This example demonstrates how to set up and use the fetchData function within an HTML document. Simply copy and paste the provided HTML and JavaScript code into your project to get started.

