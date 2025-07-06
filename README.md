# Recruitment Task Frontend

## Setup Instructions

1. **Install dependencies**  
   Run the following command:
   ```bash
   npm install
   ```

2. **Start the local development server**  
   To run the local server, execute:
   ```bash
   npm run dev
   ```

3. **Backend API configuration**  
   If you have already configured and started the *Recruitment Task Backend*,  
   you can update the API URL in the `src/App.vue` file from:
   ```js
   "./module.json"
   ```
   to:
   ```js
   "http://localhost/wp-json/api/v1/module"
   ```
