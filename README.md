# ideal-cafe
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ideal Café - Mangalore</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <header>
    <h1>Ideal Café</h1>
    <nav>
      <a href="#home">Home</a>
      <a href="#icecreams">Ice Cream Menu</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>  <section id="home" class="hero">
    <h2>Welcome to Ideal Café</h2>
    <p>Serving delicious treats and iconic ice creams in Mangalore!</p>
  </section>  <section id="icecreams">
    <h2 style="text-align:center">Ice Cream Menu</h2>
    <div class="grid" id="icecream-list"></div>
  </section>  <section id="contact" class="hero">
    <h2>Contact Us</h2>
    <p>Phone: <a href="tel:+918242447896">0824 244 7896</a></p>
    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3929.342688161639!2d74.83821047481455!3d12.869935287445795!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3ba35a4ddcad1e4d%3A0x76fe9b9339a3b1d6!2sIdeal%20Cafe!5e0!3m2!1sen!2sin!4v1713086412630!5m2!1sen!2sin" width="100%" height="300" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
  </section>  <div class="modal hidden" id="popup">
    <div class="modal-content">
      <span id="close-popup">×</span>
      <img id="popup-image" src="" alt="" />
      <h3 id="popup-title"></h3>
      <p><strong>Price:</strong> ₹<span id="popup-price"></span></p>
      <p><strong>Ingredients:</strong> <span id="popup-ingredients"></span></p>
    </div>
  </div>  <script>
    const iceCreams = [
      {
        name: "Choco Chip",
        price: 85,
        image: "https://source.unsplash.com/400x300/?chocolate,icecream",
        ingredients: "Chocolate chips, vanilla ice cream"
      },
      {
        name: "Kesar Falooda",
        price: 95,
        image: "https://source.unsplash.com/400x300/?falooda,icecream",
        ingredients: "Kesar syrup, falooda sev, basil seeds"
      },
      {
        name: "Swiss Chocolate",
        price: 60,
        image: "https://source.unsplash.com/400x300/?swisschocolate",
        ingredients: "Swiss chocolate, cocoa cream"
      },
      {
        name: "Fruit Salad",
        price: 95,
        image: "https://source.unsplash.com/400x300/?fruit,salad",
        ingredients: "Vanilla Ice Cream with Fresh Fruits"
      },
      {
        name: "Jack Fruit Payasam",
        price: 70,
        image: "https://source.unsplash.com/400x300/?jackfruit,dessert",
        ingredients: "Jackfruit, coconut milk, jaggery"
      },
      {
        name: "Hot Carrot Halwa with Vanilla",
        price: 100,
        image: "https://source.unsplash.com/400x300/?carrot,halwa",
        ingredients: "Carrot halwa, vanilla ice cream"
      },
      {
        name: "Dilkush",
        price: 150,
        image: "https://source.unsplash.com/400x300/?icecream,special",
        ingredients: "Fruit and nut mix with flavored ice cream"
      },
      {
        name: "Low n Lite",
        price: 60,
        image: "https://source.unsplash.com/400x300/?healthy,icecream",
        ingredients: "Low calorie, no added sugar"
      },
      {
        name: "Chocolate Fantasy",
        price: 170,
        image: "https://source.unsplash.com/400x300/?chocolate,fantasy",
        ingredients: "Rich chocolate, fudge, brownie"
      }
    ];

    const list = document.getElementById("icecream-list");
    const popup = document.getElementById("popup");
    const popupImage = document.getElementById("popup-image");
    const popupTitle = document.getElementById("popup-title");
    const popupPrice = document.getElementById("popup-price");
    const popupIngredients = document.getElementById("popup-ingredients");
    const closePopup = document.getElementById("close-popup");

    iceCreams.forEach((item) => {
      const card = document.createElement("div");
      card.className = "card";
      card.innerHTML = `
        <img src="${item.image}" alt="${item.name}" />
        <h3>${item.name}</h3>
        <p>₹${item.price}</p>
      `;
      card.addEventListener("click", () => {
        popupImage.src = item.image;
        popupTitle.textContent = item.name;
        popupPrice.textContent = item.price;
        popupIngredients.textContent = item.ingredients;
        popup.classList.remove("hidden");
      });
      list.appendChild(card);
    });

    closePopup.addEventListener("click", () => {
      popup.classList.add("hidden");
    });
  </script>  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #fff9f0;
    }
    header {
      background: #ff6f61;
      color: #fff;
      padding: 20px;
      text-align: center;
    }
    nav a {
      color: #fff;
      margin: 0 10px;
      text-decoration: none;
      font-weight: bold;
    }
    .hero {
      padding: 40px;
      text-align: center;
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
      padding: 20px;
    }
    .card {
      background: white;
      padding: 10px;
      border-radius: 10px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      text-align: center;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .card:hover {
      transform: scale(1.05);
    }
    .card img {
      width: 100%;
      height: 150px;
      object-fit: cover;
      border-radius: 10px;
    }
    .modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: rgba(0,0,0,0.7);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 999;
    }
    .modal-content {
      background: white;
      padding: 20px;
      border-radius: 10px;
      width: 90%;
      max-width: 400px;
      text-align: center;
      position: relative;
    }
    .modal-content img {
      width: 100%;
      height: auto;
      border-radius: 10px;
    }
    #close-popup {
      position: absolute;
      top: 10px;
      right: 15px;
      font-size: 24px;
      cursor: pointer;
      background: black;
      color: white;
      padding: 2px 10px;
      border-radius: 5px;
    }
    .hidden {
      display: none;
    }
  </style></body>
</html>
