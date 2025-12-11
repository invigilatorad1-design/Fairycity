# Locali - Full Stack Mobile App

## 🎯 Project Overview

**Locali** is a full-stack mobile application that serves as "The Insider's Guide" to exploring Indian cities. It helps both residents find local services and rentals, and tourists discover attractions and food recommendations.

---

## 📱 System Architecture

```
┌─────────────────────────────────────────────────────┐
│                   FRONTEND (React)                   │
│  ├─ Landing Screen (State & City Selection)         │
│  ├─ Resident Dashboard (Services & Rentals)         │
│  └─ Tourist Dashboard (Places & Food)               │
│  Styling: Responsive CSS with Gradients             │
└──────────────────┬──────────────────────────────────┘
                   │ HTTP Requests
                   ↓
┌─────────────────────────────────────────────────────┐
│              BACKEND (Express.js + Node.js)          │
│  ├─ /api/rentals/:city (GET/POST)                  │
│  ├─ /api/services/:city (GET/POST)                 │
│  ├─ /api/places/:city (GET/POST)                   │
│  └─ /api/food/:city (GET/POST)                     │
└──────────────────┬──────────────────────────────────┘
                   │ Database Operations
                   ↓
┌─────────────────────────────────────────────────────┐
│          DATABASE (MongoDB)                          │
│  ├─ Listing Collection (Rentals & Services)        │
│  └─ Place Collection (Attractions & Food)          │
└─────────────────────────────────────────────────────┘
```

---

## 🚀 Quick Start Guide

### Prerequisites
- Node.js 14+ and npm
- MongoDB (local or cloud Atlas)
- Text Editor (VS Code recommended)

### Step 1: Install Backend Dependencies
```bash
cd Workspace
npm install  # For backend
```

### Step 2: Setup Environment Variables
Create `.env` file:
```bash
MONGO_URI=mongodb://localhost:27017/locali_db
PORT=5000
NODE_ENV=development
```

### Step 3: Start MongoDB
```bash
# For Windows with MongoDB installed
mongod

# Or use MongoDB Atlas (cloud)
# Update MONGO_URI in .env with your connection string
```

### Step 4: Start Backend Server
```bash
npm start  # Runs on http://localhost:5000
```

### Step 5: Open Frontend
Open `index.html` in your browser to see the full-stack demo.

---

## 📡 API Endpoints

### Resident Routes

#### 1. Get All Rentals in a City
```
GET /api/rentals/:city
Example: GET /api/rentals/Bangalore
```
**Response:**
```json
[
  {
    "_id": "507f1f77bcf86cd799439011",
    "category": "rental",
    "type": "2BHK Flat",
    "price": 18000,
    "area": "Indiranagar",
    "city": "Bangalore",
    "contactPhone": "9876543210",
    "isVerified": true,
    "ownerName": "John Doe"
  }
]
```

#### 2. Add New Rental Listing
```
POST /api/rentals
```
**Request Body:**
```json
{
  "category": "rental",
  "type": "2BHK Flat",
  "price": 18000,
  "area": "Indiranagar",
  "city": "Bangalore",
  "contactPhone": "9876543210",
  "isVerified": true,
  "ownerName": "John Doe"
}
```

#### 3. Get Services by City
```
GET /api/services/:city
Example: GET /api/services/Bangalore
```

---

### Tourist Routes

#### 1. Get Tourist Spots
```
GET /api/places/:city
Example: GET /api/places/Bangalore
```
**Response:**
```json
[
  {
    "_id": "507f1f77bcf86cd799439012",
    "category": "heritage",
    "name": "Mysore Palace",
    "description": "Historic palace",
    "city": "Bangalore",
    "location": "Mysore",
    "bestTime": "Morning",
    "imageUrl": "https://...",
    "rating": 4.5
  }
]
```

#### 2. Get Food Recommendations
```
GET /api/food/:city
Example: GET /api/food/Bangalore
```

#### 3. Add New Place
```
POST /api/places
```
**Request Body:**
```json
{
  "category": "heritage",
  "name": "Mysore Palace",
  "description": "Historic palace",
  "city": "Bangalore",
  "location": "Mysore",
  "bestTime": "Morning",
  "imageUrl": "https://...",
  "rating": 4.5
}
```

---

## 🗄️ Database Schema

### Listing Collection (for Rentals & Services)
```javascript
{
  category: String,      // "rental" or "service"
  type: String,          // "2BHK", "Plumber", etc.
  price: Number,         // Monthly rent or service cost
  area: String,          // Location area
  city: String,          // City name
  contactPhone: String,  // Contact number
  isVerified: Boolean,   // Verification status
  ownerName: String,     // Owner/Provider name
  createdAt: Date        // Auto-generated timestamp
}
```

### Place Collection (for Attractions & Food)
```javascript
{
  category: String,      // "heritage", "nature", "food", etc.
  name: String,          // Place/Dish name
  description: String,   // Details
  city: String,          // City name
  location: String,      // Address or coordinates
  bestTime: String,      // Best time to visit
  imageUrl: String,      // Image URL
  rating: Number,        // Rating (1-5)
  createdAt: Date        // Auto-generated timestamp
}
```

---

## 🎨 Frontend Features

### Three Main Screens

#### 1. Landing Screen
- Purple gradient background (#667eea → #764ba2)
- State/City selection inputs
- Persona selector (Resident or Tourist)
- Smooth hover animations

#### 2. Resident Screen
- Green-themed background (#f4f9f4)
- Quick services grid (Milk, Veggie, Meds, Repair, etc.)
- Rental listings with verification badges
- Contact buttons for each listing

#### 3. Tourist Screen
- Warm cream background (#fffcf5)
- Orange-red gradient hero banner
- Horizontally scrollable tourist attractions
- Food recommendations with restaurant details

### Responsive Design
- Mobile-first approach
- 375px base mobile frame
- Adapts to tablets and desktops
- Custom scrollbars
- Touch-friendly buttons

---

## 📋 File Structure

```
Workspace/
├── index.html              # Full-stack demo with frontend + backend
├── preview.html            # Static preview (no backend needed)
├── css-responsive-demo.html # CSS demo interface
├── server.js               # Express.js backend
├── package.json            # Frontend dependencies
├── backend-package.json    # Backend dependencies
├── .env.example            # Environment variables template
├── README.md               # Project documentation
├── SETUP_COMPLETE.md       # Setup checklist
│
├── src/
│   ├── App.jsx             # React main component
│   ├── App.css             # All styling
│   ├── main.jsx            # React entry point
│   └── index.css           # Global styles
│
├── .github/
│   └── copilot-instructions.md  # Development guidelines
│
└── CSS/                    # Original CSS file reference
```

---

## 🔧 Installation Details

### Install Frontend Dependencies
```bash
npm install
# Installs: react, react-dom, react-icons, vite
```

### Install Backend Dependencies
```bash
npm install express mongoose cors dotenv
npm install --save-dev nodemon
```

### Run Frontend (React Development)
```bash
npm run dev
# Starts Vite dev server on http://localhost:5173
```

### Run Backend
```bash
npm start
# Starts Express server on http://localhost:5000
```

### Build for Production
```bash
npm run build
# Creates optimized build in dist/ folder
```

---

## 🌐 API Integration Example

### Fetch Rentals from Frontend
```javascript
// In React component
const fetchRentals = async (city) => {
  try {
    const response = await fetch(`http://localhost:5000/api/rentals/${city}`);
    const data = await response.json();
    setRentals(data);
  } catch (error) {
    console.error('Error:', error);
  }
};
```

### Create New Rental Listing
```javascript
const addRental = async (rentalData) => {
  try {
    const response = await fetch('http://localhost:5000/api/rentals', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(rentalData)
    });
    const result = await response.json();
    console.log('Rental added:', result);
  } catch (error) {
    console.error('Error:', error);
  }
};
```

---

## 🧪 Testing the Full Stack

### Using the Demo Page
1. Open `index.html` in browser
2. Left panel shows the mobile app interface
3. Right panel shows API interaction
4. Click buttons to test endpoints:
   - **Get Rentals**: Fetches rental listings
   - **Add Rental**: Creates new rental
   - **Get Places**: Fetches tourist spots
   - **Get Food**: Fetches food recommendations

### Using Postman/cURL
```bash
# Get rentals
curl http://localhost:5000/api/rentals/Bangalore

# Add rental
curl -X POST http://localhost:5000/api/rentals \
  -H "Content-Type: application/json" \
  -d '{
    "category": "rental",
    "type": "2BHK",
    "price": 18000,
    "area": "Indiranagar",
    "city": "Bangalore"
  }'
```

---

## 🎯 Features Implemented

### ✅ Frontend
- [x] Landing screen with state/city selection
- [x] Persona selection (Resident/Tourist)
- [x] Resident dashboard with services and rentals
- [x] Tourist dashboard with attractions and food
- [x] Responsive mobile design
- [x] Smooth animations and transitions
- [x] Custom scrollbars

### ✅ Backend
- [x] Express.js server setup
- [x] MongoDB connection
- [x] CORS enabled for cross-origin requests
- [x] GET endpoints for rentals, services, places, food
- [x] POST endpoints for adding listings
- [x] PUT endpoint for updating listings
- [x] DELETE endpoint for removing listings
- [x] Error handling

### ✅ Database
- [x] Listing schema for rentals and services
- [x] Place schema for attractions and food
- [x] Indexed queries by city
- [x] Timestamps on all documents

---

## 📚 Tech Stack Summary

| Layer | Technology | Version |
|-------|-----------|---------|
| Frontend | React | 18.2 |
| Build Tool | Vite | 5.0 |
| Icons | React Icons | 4.12 |
| Backend | Express.js | 4.18 |
| Database | MongoDB | 7.5 |
| ORM | Mongoose | 7.5 |
| Middleware | CORS | 2.8 |
| Environment | Dotenv | 16.3 |

---

## 🔒 Security Notes

- ✅ CORS enabled for development
- ⚠️ Disable CORS wildcard in production
- ⚠️ Add authentication before deploying
- ⚠️ Validate/sanitize all inputs
- ⚠️ Use HTTPS in production
- ⚠️ Keep MongoDB credentials secure

---

## 🐛 Troubleshooting

### "Cannot GET /api/rentals/Bangalore"
- Backend server not running
- MongoDB connection failed
- Check if port 5000 is available

### "CORS error: Access blocked"
- Backend CORS not configured
- Check `app.use(cors())` in server.js
- Verify frontend URL is allowed

### "MongooseError: Cannot connect"
- MongoDB not running
- Check MONGO_URI in .env
- Verify MongoDB port (default 27017)

### Frontend not loading data
- Backend server not running
- Check network tab in browser dev tools
- Verify API endpoint URLs

---

## 📞 Support

For issues or questions:
1. Check error messages in browser console
2. Check server logs in terminal
3. Verify all services are running (MongoDB, Express)
4. Review the .github/copilot-instructions.md

---

## 📄 License

This project is part of the Hackathon 2k25. All rights reserved.

**Last Updated:** December 11, 2025
