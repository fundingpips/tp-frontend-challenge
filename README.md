# Frontend Trading Terminal Challenge

## Overview

This is a senior/lead frontend developer challenge designed to test core skills required for building real-time trading applications. The challenge focuses on WebSocket integration, real-time data handling, and React/TypeScript proficiency.

**Important**: Approach this task as if it will be used in production by real users. A certain degree of ownership and attention to detail is expected.

## Challenge Requirements

Build a **Real-Time Cryptocurrency Pairs List** that displays live market data with detailed symbol information.

### Core Features (Required)

#### 1. Trading Pairs List
- Fetch and display available trading pairs from **Binance REST API**
- Show initial list of at least 20-30 major USDT pairs (BTC/USDT, ETH/USDT, etc.)
- Display in a clean table/list format with columns:
  - **Symbol** (e.g., BTCUSDT)
  - **Current Price**
  - **24h Change %** (with color coding: green for positive, red for negative)
  - **24h Volume**

#### 2. Real-Time Price Updates
- Connect to **Binance WebSocket API** for live price tickers
- Update prices in real-time without page refresh
- Implement proper WebSocket connection management:
  - Connection status indicator
  - Automatic reconnection on disconnect
  - Error handling for connection failures

#### 3. Symbol Detail Popup/Modal
- **Click on any trading pair** to open detailed information
- Display in a modal/popup/sidebar:
  - **Symbol details** (base/quote currencies)
  - **Current price** (real-time)
  - **24h statistics**: high, low, volume, change %
  - **Price precision** and **minimum order quantity**
  - **Real-time price updates** within the modal

#### 4. Basic UI/UX Features
- **Search/filter** functionality for trading pairs
- **Loading states** while fetching initial data
- **Error handling** with user-friendly messages

### Technical Requirements

#### Core Tech Stack
- **React 18** with **TypeScript**
- **Vite** for build tooling
- State management of your choice (React hooks, Redux Toolkit, Zustand, etc.)
- Styling solution of your choice (CSS modules, Tailwind, styled-components, etc.)

#### WebSocket Integration
- Native **WebSocket** or any WebSocket library
- Handle multiple symbol subscriptions efficiently
- Proper cleanup on component unmount
- Connection resilience (reconnect logic)

#### Code Quality
- **TypeScript interfaces** for all API responses
- **Error boundaries** for graceful error handling
- **Custom hooks** for WebSocket and data management
- **Clean component structure** with separation of concerns

## API Resources

### REST API - Get Trading Pairs
```
GET https://api.binance.com/api/v3/exchangeInfo
```
- Returns all available trading pairs and their details
- Filter for USDT pairs for simplicity
- No API key required

### WebSocket API - Real-time Prices
```
wss://stream.binance.com:9443/ws/!ticker@arr
```
- Streams all 24hr ticker statistics for all symbols
- Real-time updates every second
- No API key required

### Alternative single symbol ticker:
```
wss://stream.binance.com:9443/ws/btcusdt@ticker
```

## Getting Started

### Prerequisites
- Node.js 18+ and npm/yarn
- Basic understanding of WebSocket APIs

### Quick Setup
1. **Install dependencies**:
   ```bash
   npm install
   ```

2. **Start development**:
   ```bash
   npm run dev
   ```

3. **Test API endpoints**:
   ```bash
   # Test REST API
   curl https://api.binance.com/api/v3/exchangeInfo

   # Test WebSocket (in browser console)
   const ws = new WebSocket('wss://stream.binance.com:9443/ws/btcusdt@ticker');
   ws.onmessage = (event) => console.log(JSON.parse(event.data));
   ```

## Evaluation Criteria

### Technical Implementation (40%)
- WebSocket connection management and error handling
- Real-time data updates efficiency
- TypeScript usage and type safety
- Component architecture and reusability

### Code Quality (35%)
- Clean, readable, and maintainable code
- Proper error handling and edge cases
- Performance considerations
- Code organization and structure

### User Experience (25%)
- Intuitive and functional interface
- Smooth real-time updates
- Loading states and error messages
- Modal/popup implementation

**Note on Design**: We will not judge visual design or aesthetics, but the application should be reasonably well-presented. Any significant UX/UI flaws that impact usability will be considered in the evaluation.

## Time Expectations

- **Minimum viable solution**: 3-4 hours
- **Complete implementation**: 6-8 hours
- **Polished with extras**: 10+ hours

## Deliverables

1. **Complete source code** with clear Git commits
2. **README** with setup instructions and architecture notes
3. **Working application** that runs with `npm run dev` and `npm run build`
4. **TypeScript** properly configured and used throughout

## Bonus Points (Optional)

- **Performance optimization** for handling many real-time updates
- **Advanced filtering/search** with debouncing
- **Price change animations** (flash green/red on updates)
- **Virtualized list** for handling large datasets
- **Unit tests** for key components
- **Error monitoring** or logging implementation

---

Focus on building a production-quality solution that demonstrates your ability to handle real-time financial data effectively.

Good luck! 🚀
