# Jewel Simple Next.js 10 + BFF + React Swiper

A complete implementation of the Jewel ML recommendation system using an intermediate server to interate with Jewel ML APIs, Next.js 10 with Server-Side Rendering and React Swiper carousels.

## Architecture

This example demonstrates a BFF (Backend for frontend) pattern with:
- **Frontend**: Next.js 10 application with SSR
- **Backend**: Express.js BFF server handling Jewel ML API calls
- **UI**: React Swiper carousels for product recommendations
- **API Integration**: Jewel ML recommendation service

## Features

- 🎠 Interactive product carousels with Swiper
- 🔄 Multi-model recommendation support (You May Like, Similar Items, etc.)
- 🖥️ Server-Side Rendering for better SEO and performance  
- 🌐 Backend-for-Frontend architecture separating concerns
- 📱 Responsive design with navigation controls
- 🔍 Model selection with multiselect dropdown
- 📊 Raw API response viewer for debugging

## Getting Started

### Prerequisites
- Node.js >= 18.18.0 (with OpenSSL legacy provider support)
- npm >= 9.0.0

### Installation & Setup

1. Install dependencies for both server and Next.js:
```bash
npm run dev
```

This will automatically:
- Install server dependencies
- Install Next.js dependencies  
- Start the BFF server on port 3002
- Start the Next.js app on port 3003

### Manual Setup

If you prefer to run components separately:

1. **Install server dependencies:**
```bash
cd server && npm install
```

2. **Install Next.js dependencies:**
```bash
cd nextjs && npm install  
```

3. **Start the BFF server:**
```bash
cd server && npm start
```

4. **Start the Next.js application:**
```bash
cd nextjs && npm run dev:port
```

## Project Structure

```
jewel-simple-nextjs-10-bff-react-swiper/
├── server/                 # Express.js BFF server
│   ├── server.js          # Main server file with API endpoints
│   ├── package.json       # Server dependencies
│   └── README.md          # Server documentation
├── nextjs/                # Next.js 10 application  
│   ├── pages/
│   │   └── index.js       # Main page with SSR
│   ├── components/
│   │   ├── ProductCarousel.js     # Swiper carousel component
│   │   └── SearchControls.js      # Model selection controls
│   └── package.json       # Frontend dependencies
├── package.json           # Project scripts and workspace config
└── README.md              # This file
```

## Available Scripts

- `npm run dev` - Start both server and Next.js (recommended)
- `npm run dev:server` - Start only the BFF server
- `npm run dev:nextjs` - Start only the Next.js app
- `npm run server:install` - Install server dependencies
- `npm run nextjs:install` - Install Next.js dependencies
- `npm run server:start` - Start server in production mode
- `npm run nextjs:start` - Start Next.js on port 3003
- `npm run build` - Build Next.js for production

## API Integration

The BFF server (`server/server.js`) handles all Jewel ML API communication:
- Aggregates multiple model requests
- Provides unified error handling
- Formats responses for frontend consumption
- Runs on port 3002

The Next.js application fetches data via Server-Side Rendering from the BFF server instead of directly calling the Jewel ML API.

## Model Types

Available recommendation models:
- **L_prod** - You May Like
- **B_prod** - Similar Items  
- **F_prod** - Frequently Bought Together
- **T_prod** - Top Sellers

## Node.js Compatibility

This project requires Node.js 18+ with OpenSSL legacy provider flags to handle webpack compatibility issues:

```json
"scripts": {
  "dev": "NODE_OPTIONS='--openssl-legacy-provider' next dev",
  "dev:port": "NODE_OPTIONS='--openssl-legacy-provider' next dev -p 3003"
}
```

## Ports

- **BFF Server**: http://localhost:3002
- **Next.js App**: http://localhost:3003  
- **Health Check**: http://localhost:3002/health