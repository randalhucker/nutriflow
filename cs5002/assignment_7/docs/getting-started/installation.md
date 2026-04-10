# Installation

NutriFlow is a cross-platform application built with Expo (React Native). It runs on the web, iOS, and Android. For most users, you will access NutriFlow through the hosted web application — no installation required. This page covers the developer setup for running locally.

## Requirements

- **Node.js** 18 or later
- **npm** (included with Node.js)
- A **GitHub personal access token** (`NUTRIFLOW_GH_TOKEN`) with `read:packages` scope — required to install the private `@randalhucker/nutriflow-contract` package

## Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/randalhucker/nutriflow_expo.git
   cd nutriflow_expo
   ```

2. **Configure your GitHub token:**

   Create or edit the `.npmrc` file in the project root and add your token. This is required to install the private contract package from GitHub Packages.

3. **Install dependencies:**

   ```bash
   npm install
   ```

4. **Set up environment variables:**

   Create a `.env` file in the project root:

   | Variable | Description | Default |
   |---|---|---|
   | `EXPO_PUBLIC_API_BASE_URL` | Backend API URL | `http://127.0.0.1:3000` |

5. **Start the backend API** (separate repository — see the NutriFlow API docs).

## Running the App

| Command | Description |
|---|---|
| `npm start` | Start Expo dev server with tunnel |
| `npm run web` | Start for web only |
| `npm run ios` | Start for iOS simulator |
| `npm run android` | Start for Android emulator |

Once running, the web app is available at `http://localhost:8081` (or the port shown in your terminal).

## Accessing NutriFlow Online

If NutriFlow is deployed, simply open the web URL in your browser — no local setup needed. The application supports modern browsers (Chrome, Firefox, Safari, Edge).

## Common Installation Issues

See: [Troubleshooting](../help/troubleshooting.md)
