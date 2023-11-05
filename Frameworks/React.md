--------------------------------------------------------------------------------
# React JS
--------------------------------------------------------------------------------
Basic commands               |
   Scaffold react app        | npx create-react-app <app name>
   Start app                 | npm start     -> (within the app folder)
                             |
Install and init Tailwindcss | * install necessary packages
                             |   npm install -D tailwindcss postcss autoprefixer
                             |
                             | * Create the necessary config files 
                             |   npx tailwindcss init -p
                             |
                             | * Within the tailwind.config.js file, make sure in
                             |   contains this:
                             |
                             | -------------------------------------------------
                             | `module.exports = {                             `
                             | `  content: [                                    `
                             | `    "./src/**/*.{js,jsx,ts,tsx}",               `
                             | `  ],                                            `
                             | `  theme: {                                     `
                             | `    extend: {},                                 `
                             | `  },                                             `
                             | `  plugins: [],                                   `
                             | `}                                              `
                             | -------------------------------------------------
                             |
                             | * edit the index.css file in your src folder, 
                             |   delet everything and add these lines
                             |
                             |
                             | -------------------------------------------------
                             | @ tailwind base;
                             | @ tailwind components;
                             | @ tailwind utilities;
                             | -------------------------------------------------
                             |
                             | * run this command:
                             |   npm install postcss@latest
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
