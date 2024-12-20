CoinTrack Project Documentation

1. Project Overview
CoinTrack is a real-time cryptocurrency tracking web application that displays the latest prices of popular cryptocurrencies. Powered by the CoinGecko API, it provides a user-friendly interface with essential information like the coin’s name, symbol, and current price. The app aims to offer real-time updates on multiple cryptocurrencies in an organized and visually appealing grid format.

2. Key Features
Displays real-time cryptocurrency prices for multiple coins.
Fetches data from CoinGecko API. With a refresh time of 30seconds
Dynamic grid layout that adapts to different screen sizes (responsive design).
Error handling to ensure smooth user experience in case of failed data fetch.


3. Technologies Used
Frontend: HTML, CSS, JavaScript
API: CoinGecko API for fetching cryptocurrency data.
Hosting: Firebase Hosting
Version Control: Git, GitHub for source code management


4. Setup Instructions
To set up the CoinTrack project locally, follow the steps below:

Clone the repository:

bash
Copy code
git clone https://github.com/Izudavo/CoinTrackSetup
Navigate to the project directory:

bash
Copy code
cd cointrack
Open the project in your preferred code editor: You can use Visual Studio Code (VSCode) or any other editor of your choice:

bash
Copy code
code .
Run the project locally: Simply open the index.html file in a web browser to view the application. There’s no need for a backend server, as all data is fetched directly from the API.


5. File Structure
Here’s an overview of the file structure:

bash
Copy code
/cointrack
├── index.html        # Main HTML file with content, inline css and JavaScript
└── README.md         # This documentation file


6. API Integration
The app fetches data from the CoinGecko API using the following URL:

javascript
Copy code
const apiUrl = 'https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&ids=bitcoin,ethereum,cardano,binancecoin,xrp,solana,polkadot,litecoin,uniswap,dogecoin,shiba-inu,terraluna,chainlink,quidax&order=market_cap_desc&per_page=30&page=1&sparkline=false';


API URL Parameters:
vs_currency=usd: The currency in which the prices are displayed.
ids=bitcoin,ethereum,...: List of cryptocurrencies to track.
order=market_cap_desc: Sorts the coins based on market cap.
per_page=30: Limits the number of results per page.
The data returned by the API includes the following properties for each coin:

name: The name of the cryptocurrency (e.g., Bitcoin, Ethereum).
symbol: The cryptocurrency’s symbol (e.g., BTC, ETH).
current_price: The current price in USD.
image: The URL of the coin’s logo.

7. Error Handling
In case the API request fails or there’s an issue fetching the data, the app will display a friendly error message instead of leaving the page blank:

javascript
Copy code
try {
  const response = await fetch(apiUrl);
  const coins = await response.json();
  if (!response.ok) throw new Error('Failed to fetch data from CoinGecko API');
} catch (error) {
  console.error('Error fetching coins:', error);
  document.getElementById('coin-list').innerHTML = '<p>Sorry, there was an error loading the data.</p>';
}


8. Future Improvements
Real-time Updates: Implement WebSockets or periodic refreshes to get live updates without reloading the page.
User Authentication: Allow users to create an account and save their favorite coins.
Additional Data: Include other coin metrics, such as 24-hour price change, volume, etc.
Design Enhancements: Improve the user interface with animations and a more modern design.


9. License
Deployed on Firebase
