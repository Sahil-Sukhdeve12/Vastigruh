# Vastigruh

A full-stack Airbnb-inspired property listing platform where users can discover, list, and review rental properties — with map-based location views and cloud image uploads.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Render-brightgreen)](https://vastigruh.onrender.com) [![Node.js](https://img.shields.io/badge/Node.js-18+-green)](https://nodejs.org/) [![Express](https://img.shields.io/badge/Express-4.x-lightgrey)](https://expressjs.com/) [![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-green)](https://www.mongodb.com/)

---

## Features

- Browse and search property listings with interactive map views (Mapbox)
- User authentication — register, login, and logout (Passport.js)
- Create, edit, and delete your own listings with image uploads (Cloudinary)
- Leave and manage reviews on listings
- Server-side input validation (Joi) with flash message feedback
- Ownership-based authorization (only listing owners can edit/delete)
- Responsive UI rendered with EJS templates

---

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| Backend | Node.js, Express.js |
| Templating | EJS, EJS-Mate |
| Database | MongoDB, Mongoose |
| Auth | Passport.js, passport-local-mongoose |
| Storage | Cloudinary, Multer |
| Maps | Mapbox SDK |
| Validation | Joi |
| Session | express-session, connect-mongo |
| Utilities | method-override, connect-flash, dotenv |

---

## Getting Started

### Prerequisites

- [Node.js v18+](https://nodejs.org/)
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) account (free tier)
- [Cloudinary](https://cloudinary.com/) account (free tier)
- [Mapbox](https://www.mapbox.com/) account (free tier)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Sahil-Sukhdeve12/Vastigruh.git
cd Vastigruh

# 2. Install dependencies
npm install

# 3. Configure environment variables
touch .env
# Add your credentials (see below)

# 4. Seed the database (optional)
node init/index.js

# 5. Start the server
node app.js
```

App runs at `http://localhost:8080`

---

## Environment Variables

Create a `.env` file in the root directory:

```env
# MongoDB
ATLASDB_URL=mongodb+srv://<username>:<password>@cluster.mongodb.net/vastigruh

# Session
SECRET=your-session-secret-key

# Cloudinary
CLOUD_NAME=your-cloudinary-cloud-name
CLOUD_API_KEY=your-cloudinary-api-key
CLOUD_API_SECRET=your-cloudinary-api-secret

# Mapbox
MAP_TOKEN=your-mapbox-public-token
```

---

## Project Structure

```
Vastigruh/
├── controllers/        # Route handler logic (listings, reviews, users)
├── models/             # Mongoose schemas (Listing, Review, User)
├── routes/             # Express routers (listings, reviews, users)
├── views/              # EJS templates
│   ├── layouts/        # Base layout (ejs-mate)
│   ├── listings/       # Listing pages (index, show, new, edit)
│   └── users/          # Auth pages (login, register)
├── public/             # Static assets (CSS, JS, images)
├── utils/              # ExpressError class and async error wrapper
├── init/               # Database seed data
├── app.js              # Express app entry point
├── middleware.js        # Auth guards and ownership checks
├── cloudConfig.js      # Cloudinary + Multer configuration
└── schema.js           # Joi validation schemas
```

---

## Deployment

### Render (Recommended)

1. Create a new **Web Service** on [Render](https://render.com) → connect your GitHub repo
2. Set the **Start Command** to `node app.js`
3. Add all environment variables from the section above
4. Set `NODE_ENV=production`

> **Note:** Render free tier spins down after inactivity — first request may take ~30s.

---

## Common Issues

| Problem | Fix |
|---------|-----|
| MongoDB connection error | Verify `ATLASDB_URL`; whitelist `0.0.0.0/0` in Atlas Network Access |
| Images not uploading | Check Cloudinary credentials (`CLOUD_NAME`, `CLOUD_API_KEY`, `CLOUD_API_SECRET`) |
| Map not rendering | Ensure `MAP_TOKEN` is a valid Mapbox **public** token |
| Sessions not persisting | Ensure `SECRET` is set and `connect-mongo` uses the correct DB URL |

---

## License

This project was developed for educational purposes as part of college coursework.
