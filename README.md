# News App

A simple and interactive **News App** built using HTML, CSS, and JavaScript. This app fetches and displays news articles dynamically from the [News API](https://newsapi.org/) based on user input or navigation clicks.

## Features

- **Dynamic News Fetching**: Fetch news articles for any topic using the [News API](https://newsapi.org/).
- **Category Navigation**: Quickly navigate through predefined categories such as IPL, Finance, and Politics.
- **Search Functionality**: Search for specific topics by entering keywords.
- **Responsive Design**: A clean and responsive UI for a better user experience.
- **Open News Links**: Click on any news card to open the full article in a new tab.

## Technologies Used

- **HTML**: For structuring the application.
- **CSS**: For styling and making the app visually appealing.
- **JavaScript**: For handling API requests and dynamic DOM updates.

## File Structure

```
.
├── index.html        # Main HTML file for the app structure
├── style.css         # Stylesheet for the app design
├── script.js         # JavaScript file for app functionality
├── assets/           # Contains app assets like the logo image
└── README.md         # Documentation file
```

## Getting Started

1. Clone the repository or download the project files.
2. Open the `index.html` file in your browser to view the app.
3. Replace the `API_KEY` in the `script.js` file with your own API key from [News API](https://newsapi.org/).

## Code Snippets

### Example of HTML Structure:
```html
<nav>
    <div class="main-nav container flex">
        <a href="#" onclick="reload()" class="company-logo">
            <img src="./assets/logo.png" alt="company logo">
        </a>
        <div class="nav-links">
            <ul class="flex">
                <li class="hover-link nav-item" id="ipl" onclick="onNavItemClick('ipl')">IPL</li>
                <li class="hover-link nav-item" id="finance" onclick="onNavItemClick('finance')">Finance</li>
                <li class="hover-link nav-item" id="politics" onclick="onNavItemClick('politics')">Politics</li>
            </ul>
        </div>
        <div class="search-bar flex">
            <input id="search-text" type="text" class="news-input" placeholder="e.g. Science">
            <button id="search-button" class="search-button">Search</button>
        </div>
    </div>
</nav>
```

### Example of JavaScript Functionality:
```javascript
async function fetchNews(query) {
    const res = await fetch(`${url}${query}&apiKey=${API_KEY}`);
    const data = await res.json();
    bindData(data.articles);
}

function bindData(articles) {
    const cardsContainer = document.getElementById("cards-container");
    const newsCardTemplate = document.getElementById("template-news-card");

    cardsContainer.innerHTML = "";

    articles.forEach((article) => {
        if (!article.urlToImage) return;
        const cardClone = newsCardTemplate.content.cloneNode(true);
        fillDataInCard(cardClone, article);
        cardsContainer.appendChild(cardClone);
    });
}
```

## How to Use

1. **Navigation**: Click on a category like IPL, Finance, or Politics to view related news.
2. **Search**: Enter a keyword in the search bar and click the search button to fetch news for that topic.
3. **Reload**: Click on the company logo to reload the app.
4. **Read Articles**: Click on a news card to open the full article in a new tab.

## Screenshot

![{7127E325-5238-4F70-9DF1-6535D79A4F31}](https://github.com/user-attachments/assets/6dee34b0-bfa3-4a3b-aafe-1eba6dae6e18)
![{EAFE01C5-516B-4DE4-9652-C99018BA54A4}](https://github.com/user-attachments/assets/60015059-dbb3-49ac-ba89-0c04f524be3e)


## API Key

To fetch news, the app uses the [News API](https://newsapi.org/). Obtain your API key by signing up on their website and replace the placeholder in the `script.js` file:

```javascript
const API_KEY = "YOUR_API_KEY_HERE";
```

## Example Output

- **Category**: IPL
- **Search Query**: Science
- **News Card Example**:

  - **Title**: Latest Discoveries in Science
  - **Source**: Science Daily · 06/01/2025
  - **Description**: Discover groundbreaking scientific research and updates in this article.

