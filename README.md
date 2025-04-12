# Enhanced Chat Interface 💬✨

This project is a front-end web chat interface featuring a stylish design with a gradient background, custom fonts, and smooth animations. It connects to the OpenRouter AI API to provide responses from AI models (specifically configured for `mistralai/mistral-nemo:free` in this example).

## Features 🎨

* **Stylish UI:** Modern chat interface with a blue gradient background, rounded corners, and custom font ("Anotica").
* **AI Integration:** Connects to the OpenRouter API to fetch responses from AI models.
* **Real-time Interaction:** Displays user messages and AI responses dynamically.
* **Loading Indicator:** Shows a bouncing dots animation while waiting for the AI response.
* **Distinct Message Styling:** Different background colors and alignment for user messages and AI messages.
* **Smooth Animations:** Subtle fade-in animation for new messages.
* **External Links:** Includes fixed links/logos for LinkedIn and GitHub profiles.
* **Custom Scrollbar:** Styled scrollbar for a consistent look (WebKit browsers).
* **Enter Key Submission:** Allows sending messages by pressing Enter.
* **Basic Error Handling:** Displays an error message if the API call fails.
* **Disclaimer:** Includes a small note that "AI can make mistakes."

## Technologies Used 💻

* **HTML5:** Semantic structure for the chat interface.
* **CSS3:** Styling, layout (Flexbox), custom fonts (`@font-face`), gradients, animations (`@keyframes`), custom scrollbars.
* **JavaScript (Vanilla):**
    * DOM Manipulation (displaying messages, handling input).
    * `Workspace` API for asynchronous communication with the OpenRouter API.
    * Event Listeners (button click, keypress).

## Setup & Installation 🚀

1.  **Clone or Download:** Get the project files (HTML, font files).
2.  **Font Files:**
    * Make sure you have the `Anotica-Regular.woff` and `Anotica-Regular.woff2` font files.
    * Update the `src` paths in the `@font-face` rule within the `<style>` tags to point to the correct location of your font files (e.g., replace `'path/to/Anotica-Regular.woff2'` ).
    * *Note: Ensure you have the necessary license to use the "Anotica" font if it's not free/open-source.*
3.  **(Optional) Local Logos:** The LinkedIn and GitHub logos are currently hotlinked from Wikimedia. For better reliability, download them and update the `<img>` `src` attributes to use local paths.
4.  **Web Server:** You need to serve this `index.html` file using a local web server (like Python's `http.server`, Node.js `live-server`, or VS Code Live Server extension). Opening the file directly via `file://` protocol might cause issues with the `Workspace` API request due to browser security policies (CORS).

## Configuration ⚙️

**CRITICAL:** You need to configure the JavaScript code to correctly use the OpenRouter API.

1.  **OpenRouter API Key:**
    * Sign up at [OpenRouter.ai](https://openrouter.ai/) to get your API key.
    * **🚨 SECURITY WARNING 🚨:** The current code has a placeholder API key directly in the JavaScript (`Authorization: "Bearer sk-or-v1-..."`). **NEVER commit your real API key directly into client-side code or public repositories.** Anyone can steal it!
    * **For Testing Only:** Replace the placeholder key with your actual key for local testing.
    * **For Production/Public Use:** Implement a backend proxy or serverless function to handle the API call. Your front-end would call your backend, which would then securely add the API key and forward the request to OpenRouter.
2.  **API Headers:**
    * In the `WorkspaceChatResponse` function, find the `headers` section.
    * Replace `<YOUR_SITE_URL>` in the `HTTP-Referer` header with the actual URL where you will host this chat (required by OpenRouter).
    * Replace `<YOUR_SITE_NAME>` in the `X-Title` header with the name of your application/site (optional but recommended by OpenRouter).
    * `"Content-Type": "application/json"` should remain as is.
3.  **(Optional) AI Model:**
    * The code is set to use `"model": "mistralai/mistral-nemo:free"`. You can change this string to any other model available on OpenRouter that you have access to. Check the OpenRouter documentation for available models. Note that non-free models will incur costs.

## Usage 🖱️

1.  Start your local web server in the project directory.
2.  Open the provided URL (e.g., `http://localhost:8000`) in your web browser.
3.  Type a message into the input field at the bottom.
4.  Click the "Send" button or press the `Enter` key.
5.  Your message will appear, followed by a loading indicator, and then the AI's response.
