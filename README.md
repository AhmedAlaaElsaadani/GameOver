# 🎮 Game Over — Free-to-Play Games Explorer

A responsive React web app for discovering and tracking the best **free-to-play games**. Browse hundreds of titles, filter by platform and category, sort by popularity or release date, and dive into rich game detail pages with screenshots and system requirements — powered by the [Free-to-Play Games Database](https://www.freetogame.com/api-doc) on RapidAPI.

<p align="left">
  <img alt="React" src="https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=white" />
  <img alt="React Router" src="https://img.shields.io/badge/React%20Router-6-CA4245?logo=reactrouter&logoColor=white" />
  <img alt="React Bootstrap" src="https://img.shields.io/badge/React%20Bootstrap-2-7952B3?logo=bootstrap&logoColor=white" />
  <img alt="Axios" src="https://img.shields.io/badge/Axios-HTTP-5A29E4?logo=axios&logoColor=white" />
  <img alt="Joi" src="https://img.shields.io/badge/Joi-Validation-0F8C5F" />
</p>

🔗 **Live Demo:** https://AhmedAlaaElsaadani.github.io/GameOver

> 🧠 **100% human-written.** This project was designed and coded entirely by hand — **no AI tools or code generators were used** in its development.

> ⚠️ **Heads up:** the games data depends on the third-party **Free-to-Play Games Database (RapidAPI)**. Because the API provider has since changed its access policy, the live demo may **fail to load games**. To run the app with live data, supply your own valid RapidAPI key — see [Configuration (API Key)](#-configuration-api-key).

---

## 📑 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Screenshots](#-screenshots)
- [Getting Started](#-getting-started)
- [Configuration (API Key)](#-configuration-api-key)
- [Available Scripts](#-available-scripts)
- [Project Structure](#-project-structure)
- [API & Backend](#-api--backend)
- [Deployment](#-deployment)
- [Author](#-author)

---

## ✨ Features

- 🔐 **Authentication** — register and log in, with the user token stored in `localStorage`.
- 🛡️ **Route guards** — `ProtectedRoute` keeps the app behind a login, while `InverseProtectedRoute` keeps logged-in users away from the auth pages.
- 🏠 **Home page** — hero section plus personalized game recommendations.
- 🗃️ **Browse all games** — explore the full catalog with a "load more" pagination pattern.
- 🖥️ **Filter by platform** — PC and Web Browser.
- 🔃 **Sort games** — by release date, popularity, alphabetical order, or relevance.
- 🏷️ **Filter by category** — racing, sports, social, shooter, open world, zombie, fantasy, action-RPG, action, fighting, and battle royale.
- 📄 **Game details** — full description, minimum system requirements, a screenshots carousel, developer / publisher / release info, and a direct **Play Now** link.
- ⏳ **Loading states** — a dedicated spinner component while data is fetched.
- 🧩 **Reusable data hook** — a custom `useURL` hook centralizes API calls and pagination.
- 📱 **Fully responsive** — built with Bootstrap 5 and React-Bootstrap.

---

## 🧰 Tech Stack

| Area | Technology |
|------|-----------|
| Framework | React 18 (Create React App) |
| Routing | React Router DOM v6 |
| HTTP client | Axios |
| Form validation | Joi |
| Styling / UI | Bootstrap 5, React-Bootstrap, Font Awesome |
| Carousels | React-Bootstrap Carousel, React Owl Carousel |
| Game data | Free-to-Play Games Database (RapidAPI) |
| Auth backend | Route Academy API |
| Deployment | GitHub Pages (`gh-pages`) |

---

## 🖼️ Screenshots

> _Add your screenshots here, e.g._
>
> | Home | Browse | Game Details |
> |------|--------|--------------|
> | ![Home](docs/home.png) | ![Browse](docs/browse.png) | ![Details](docs/details.png) |

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v16 or newer recommended)
- npm (comes with Node.js)
- A free [RapidAPI](https://rapidapi.com/) account with access to the **Free-to-Play Games Database** API

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/AhmedAlaaElsaadani/GameOver.git

# 2. Move into the project directory
cd GameOver

# 3. Install dependencies
npm install

# 4. Start the development server
npm start
```

The app will open at [http://localhost:3000](http://localhost:3000).

---

## 🔑 Configuration (API Key)

Game data is fetched from the **Free-to-Play Games Database** on RapidAPI, which requires an API key sent via the `X-RapidAPI-Key` header. The request setup lives in [`src/Hooks/useURL.jsx`](src/Hooks/useURL.jsx), where a demo key is already included so the app works out of the box.

> ⚠️ **The API may no longer return data.** The RapidAPI provider has changed its access policy since this project was built, so the bundled key can stop working and the games list may come back empty. If that happens, grab your own key from [RapidAPI](https://rapidapi.com/digiwalls/api/free-to-play-games-database) and replace it in `src/Hooks/useURL.jsx`:
>
> ```js
> // src/Hooks/useURL.jsx
> headers: {
>   "X-RapidAPI-Key": "YOUR_RAPIDAPI_KEY",
>   "X-RapidAPI-Host": "free-to-play-games-database.p.rapidapi.com",
> }
> ```

---

## 📜 Available Scripts

| Script | Description |
|--------|-------------|
| `npm start` | Runs the app in development mode at `localhost:3000`. |
| `npm run build` | Builds the app for production into the `build/` folder. |
| `npm test` | Launches the test runner in interactive watch mode. |
| `npm run deploy` | Builds and publishes the app to GitHub Pages. |
| `npm run eject` | Ejects from Create React App (one-way operation). |

---

## 📂 Project Structure

```
src/
├── Components/
│   ├── Home/                 # Landing page + recommendations
│   ├── All/                  # Full games catalog
│   ├── GameItem/             # Reusable game card
│   ├── GameDetails/          # Single game details + screenshots
│   ├── Platforms/            # PC & Browser filters
│   │   ├── Pc/
│   │   └── Browser/
│   ├── SortBy/               # Release date, popularity, alphabetical, relevance
│   ├── Category/             # Racing, sports, shooter, zombie, ... 11 genres
│   ├── Login/ · Register/    # Authentication pages
│   ├── Navbar/               # Top navigation with dropdowns
│   ├── RootLayout/           # Shared app shell (Outlet)
│   ├── ProtectedRoute/       # Auth route guard
│   ├── InverseProtectedRoute # Reverse guard for auth pages
│   ├── Loading/              # Spinner component
│   └── ErrorPage/            # 404 page
├── Hooks/
│   └── useURL.jsx            # Custom data-fetching & pagination hook
├── images/                   # Static assets
├── App.jsx                   # Routes definition
└── index.js                  # App entry point
```

---

## 🔌 API & Backend

This project uses **two** services:

| Service | Base URL | Used for |
|---------|----------|----------|
| Free-to-Play Games Database (RapidAPI) | `https://free-to-play-games-database.p.rapidapi.com` | Games list, filtering, sorting & details |
| Route Academy API | `https://ecommerce.routemisr.com` | User registration & login (auth) |

---

## ☁️ Deployment

The app is deployed to **GitHub Pages**. To publish your own build:

```bash
npm run deploy
```

This runs `predeploy` (a production build) and pushes the `build/` folder to the `gh-pages` branch. Make sure the `homepage` field in `package.json` matches your GitHub Pages URL.

---

## 👤 Author

**Ahmed Alaa Elsaadani**

- GitHub: [@AhmedAlaaElsaadani](https://github.com/AhmedAlaaElsaadani)

---

> ⭐ If you find this project helpful, consider giving it a star on GitHub!
