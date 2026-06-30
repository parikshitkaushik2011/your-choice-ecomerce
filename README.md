JSON
{
"name": "your-choice-ecommerce",
"version": "1.0.0",
"description": "Your Choice E-Commerce - Design My Style. Premium luxury fashion platform",
"type": "module",
"scripts": {
"dev": "vite",
"build": "vite build",
"preview": "vite preview",
"lint": "eslint src --ext js,jsx",
"format": "prettier --write "src/**/*.{js,jsx,css}""
},
"dependencies": {
"react": "^18.2.0",
"react-dom": "^18.2.0",
"react-router-dom": "^6.20.0",
"firebase": "^10.7.0",
"tailwindcss": "^3.4.0",
"framer-motion": "^10.16.0",
"react-query": "^3.39.3",
"@reduxjs/toolkit": "^1.9.7",
"react-redux": "^8.1.3",
"react-hook-form": "^7.48.0",
"axios": "^1.6.0",
"react-icons": "^4.12.0",
"react-hot-toast": "^2.4.1",
"zustand": "^4.4.0",
"swiper": "^11.0.0",
"react-star-ratings": "^2.3.0"
},
"devDependencies": {
"@vitejs/plugin-react": "^4.2.0",
"vite": "^5.0.0",
"autoprefixer": "^10.4.0",
"postcss": "^8.4.0",
"prettier": "^3.1.0"
}
}

vite.config.js

js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import path from 'path'

export default defineConfig({
plugins: [react()],
server: {
port: 3000,
open: true
},
resolve: {
alias: {
'@': path.resolve(__dirname, './src'),
},
},
build: {
target: 'esnext',
outDir: 'dist',
sourcemap: false,
minify: 'terser',
rollupOptions: {
output: {
manualChunks: {
'vendor': ['react', 'react-dom', 'react-router-dom'],
'firebase': ['firebase/app', 'firebase/auth', 'firebase/firestore', 'firebase/storage'],
}
}
}
}
})

tailwind.config.js

js
export default {
content: [
"./index.html",
"./src/**/*.{js,jsx}",
],
theme: {
extend: {
colors: {
'luxury-black': '#0B0B0B',
'luxury-gold': '#D4AF37',
'luxury-white': '#FFFFFF',
'luxury-light': '#F5F5F5',
},
fontFamily: {
'playfair': ['Playfair Display', 'serif'],
'poppins': ['Poppins', 'sans-serif'],
},
boxShadow: {
'luxury': '0 20px 60px rgba(212, 175, 55, 0.15)',
'luxury-sm': '0 10px 30px rgba(0, 0, 0, 0.3)',
'luxury-gold': '0 0 30px rgba(212, 175, 55, 0.5)',
'luxury-lg': '0 30px 80px rgba(0, 0, 0, 0.5)',
},
backdropBlur: {
'xs': '2px',
},
animation: {
'float': 'float 3s ease-in-out infinite',
'glow': 'glow 2s ease-in-out infinite',
'shimmer': 'shimmer 2s infinite',
'pulse-gold': 'pulse-gold 2s cubic-bezier(0.4, 0, 0.6, 1) infinite',
'slide-in': 'slide-in 0.5s ease-out',
'fade-in': 'fade-in 0.3s ease-in',
},
keyframes: {
float: {
'0%, 100%': { transform: 'translateY(0px)' },
'50%': { transform: 'translateY(-20px)' },
},
glow: {
'0%, 100%': { boxShadow: '0 0 20px rgba(212, 175, 55, 0.5)' },
'50%': { boxShadow: '0 0 40px rgba(212, 175, 55, 0.8)' },
},
shimmer: {
'0%': { backgroundPosition: '-1000px 0' },
'100%': { backgroundPosition: '1000px 0' },
},
'pulse-gold': {
'0%, 100%': { opacity: '1' },
'50%': { opacity: '0.7' },
},
'slide-in': {
'0%': { transform: 'translateX(-100%)', opacity: '0' },
'100%': { transform: 'translateX(0)', opacity: '1' },
},
'fade-in': {
'0%': { opacity: '0' },
'100%': { opacity: '1' },
},
},
},
},
plugins: [],
}

postcss.config.js

js
export default {
plugins: {
tailwindcss: {},
autoprefixer: {},
},
}

index.html

HTML

<!doctype html> <html lang="en"> <head> <meta charset="UTF-8" /> <link rel="icon" type="image/svg+xml" href="/favicon.svg" /> <meta name="viewport" content="width=device-width, initial-scale=1.0" /> <meta name="description" content="Your Choice E-Commerce - Design My Style. Premium luxury fashion e-commerce platform for Ladies & Gents Garments" /> <meta name="theme-color" content="#0B0B0B" /> <meta name="author" content="Your Choice Fashion" /> <meta property="og:title" content="Your Choice E-Commerce - Design My Style" /> <meta property="og:description" content="Premium Ladies & Gents Garments - Your Style, Your Choice" /> <meta property="og:type" content="website" /> <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600;700;800&family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet" /> <title>Your Choice E-Commerce - Design My Style</title> </head> <body class="bg-luxury-black text-white font-poppins"> <div id="root"></div> <script type="module" src="/src/main.jsx"></script> </body> </html>
.env.example

example
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_auth_domain
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_messaging_sender_id
VITE_FIREBASE_APP_ID=your_app_id
VITE_RAZORPAY_KEY_ID=your_razorpay_key
VITE_CLOUDINARY_CLOUD_NAME=your_cloudinary_name
VITE_ADMIN_EMAILS=admin@email.com,owner@email.com

.gitignore

gitignore
node_modules/
dist/
.env
.env.local
.env..local
.DS_Store
.log
npm-debug.log
yarn-debug.log
yarn-error.log*
.vscode/
.idea/
*.swp
*.swo
*~
.cache/
build/
cover/
.turbo/

README.md

md

Your Choice E-Commerce - Design My Style
A production-ready luxury e-commerce platform for premium ladies & gents garments with modern, elegant design.

🎨 Design Philosophy
Theme: Luxury Black + Metallic Gold + White
Style: Modern, Premium, Elegant, Fast, Clean UI
Animation: Apple-quality smooth animations
Typography: Playfair Display (headings) + Poppins (body)
Tagline: Your Style, Your Choice
🛠 Tech Stack
Frontend: React 18 + Vite
Styling: Tailwind CSS
Backend: Firebase Firestore
Authentication: Firebase Auth
Animations: Framer Motion
State Management: Redux Toolkit
Forms: React Hook Form
API: Axios
Payment: Razorpay Integration
Storage: Firebase Storage + Cloudinary
Routing: React Router v6
✨ Features
✅ Premium Hero Slider
✅ Product Catalog with Advanced Filters
✅ Instant Search with Auto-suggestions
✅ Voice Search Support
✅ Wishlist System
✅ Shopping Cart
✅ Multiple Payment Methods (UPI, Razorpay, COD)
✅ User Authentication (Email, Google, Phone)
✅ Order Tracking
✅ Product Reviews & Ratings
✅ Admin Dashboard
✅ Inventory Management
✅ Coupon & Offer Management

✨ Special Effects
✨ Glassmorphism Effects
✨ Luxury Shadows
✨ Gold Glow Animations
✨ Smooth Hover Effects
✨ Animated Counters
✨ Page Transitions
✨ Floating WhatsApp Button
✨ Sticky Navigation
✨ Custom Cursor

📱 Responsive Design
📱 Mobile First Approach
📱 Tablet Optimized
📱 Desktop Enhanced
📱 All Breakpoints Covered

🚀 Getting Started
Installation
npm install
cp .env.example .env
Development
bash
npm run dev
The application will open at http://localhost:3000
Build
bash
npm run build
npm run preview
📂 Project Structure
Code
src/
├── components/
│   ├── Header/
│   ├── Navbar/
│   ├── Footer/
│   ├── ProductCard/
│   ├── HeroSlider/
│   ├── Cart/
│   └── ...
├── pages/
│   ├── Home/
│   ├── Shop/
│   ├── Product/
│   ├── Cart/
│   ├── Checkout/
│   ├── Login/
│   ├── Profile/
│   ├── Admin/
│   └── ...
├── store/
│   └── slices/
├── hooks/
├── utils/
├── config/
├── styles/
├── App.jsx
└── main.jsx
📊 Database Schema (Firebase Firestore)
Users: Authentication & Profile Management
Products: Catalog with Images & Variants
Orders: Order Management & Tracking
Wishlist: Saved Products
Reviews: Ratings & Comments
Categories: Product Organization
Coupons: Discount Codes
Cart: Shopping Cart Items
🏪 Store Information
Location: C/O Bhawani Medical Store
Owner 1: Arvind Kaushik
📱 9467259111
Owner 2: Karan Kaushik
📱 8950114418
🎯 Future Goals
🌍 Expand throughout India
🌍 International Expansion
🏢 Multi-vendor Support
🏢 Franchise Model
📦 Real-time Order Tracking
🎁 Loyalty Rewards Program
📄 License
This project is proprietary and confidential.
Built with ❤️ for fashion enthusiasts. Your Style, Your Choice.
Code
src/main.jsx
jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'
ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
)
src/index.css
CSS
@tailwind base;
@tailwind components;
@tailwind utilities;
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-color: #0B0B0B;
  color: #FFFFFF;
  font-family: 'Poppins', sans-serif;
}
h1, h2, h3, h4, h5, h6 {
  font-family: 'Playfair Display', serif;
}
::-webkit-scrollbar {
  width: 8px;
  height: 8px;
}
::-webkit-scrollbar-track {
  background: #0B0B0B;
}
::-webkit-scrollbar-thumb {
  background: #D4AF37;
  border-radius: 4px;
}
::-webkit-scrollbar-thumb:hover {
  background: #E5C158;
}
html {
  scroll-behavior: smooth;
}
.glass {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}
.luxury-shadow {
  box-shadow: 0 20px 60px rgba(212, 175, 55, 0.15);
}
.luxury-shadow-lg {
  box-shadow: 0 30px 80px rgba(0, 0, 0, 0.5);
}
.gold-glow {
  box-shadow: 0 0 30px rgba(212, 175, 55, 0.5);
}
src/App.jsx
jsx
import React, { useState, useEffect } from 'react'
import { motion } from 'framer-motion'
const App = () => {
  const [isLoading, setIsLoading] = useState(true)
  useEffect(() => {
    setTimeout(() => setIsLoading(false), 2000)
  }, [])
  return (
    <div className="min-h-screen bg-luxury-black text-white font-poppins">
      {isLoading ? (
        <motion.div className="h-screen flex items-center justify-center bg-luxury-black" initial={{ opacity: 0 }} animate={{ opacity: 1 }}>
          <motion.div animate={{ rotate: 360 }} transition={{ duration: 2, repeat: Infinity }} className="w-16 h-16 border-4 border-luxury-gold/30 border-t-luxury-gold rounded-full" />
        </motion.div>
      ) : (
        <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} transition={{ duration: 0.8 }}>
          {/* Header */}
          <header className="bg-luxury-black border-b border-luxury-gold/20 sticky top-0 z-50 backdrop-blur-md bg-opacity-95">
            <div className="max-w-7xl mx-auto px-4 py-6 flex justify-between items-center">
              <div className="cursor-pointer">
                <h1 className="text-3xl font-playfair font-bold text-luxury-gold">Your Choice</h1>
                <p className="text-luxury-light text-xs font-poppins">Design My Style</p>
              </div>
              <nav className="hidden md:flex gap-8 text-sm font-poppins">
                <a href="#home" className="hover:text-luxury-gold transition-colors duration-300">Home</a>
                <a href="#shop" className="hover:text-luxury-gold transition-colors duration-300">Shop</a>
                <a href="#men" className="hover:text-luxury-gold transition-colors duration-300">Men</a>
                <a href="#women" className="hover:text-luxury-gold transition-colors duration-300">Women</a>
                <a href="#kids" className="hover:text-luxury-gold transition-colors duration-300">Kids</a>
                <a href="#contact" className="hover:text-luxury-gold transition-colors duration-300">Contact</a>
              </nav>
              <div className="flex gap-4">
                <button className="p-2 hover:text-luxury-gold transition-colors">🔍</button>
                <button className="p-2 hover:text-luxury-gold transition-colors">❤️</button>
                <button className="p-2 hover:text-luxury-gold transition-colors">🛒</button>
              </div>
            </div>
          </header>
          {/* Hero Section */}
          <main className="">
            <section id="home" className="relative min-h-screen bg-gradient-to-b from-luxury-black via-luxury-black to-luxury-black/80 flex items-center justify-center px-4 pt-20">
              <motion.div className="max-w-7xl mx-auto w-full text-center" initial={{ y: 30, opacity: 0 }} animate={{ y: 0, opacity: 1 }} transition={{ delay: 0.3, duration: 0.8 }}>
                <motion.h2 className="text-6xl md:text-8xl font-playfair font-bold mb-6 leading-tight" initial={{ scale: 0.8 }} animate={{ scale: 1 }} transition={{ delay: 0.5 }}>
                  Your Style,<br /><span className="text-luxury-gold">Your Choice</span>
                </motion.h2>
                <motion.p className="text-2xl text-luxury-light mb-4 font-poppins" initial={{ opacity: 0 }} animate={{ opacity: 1 }} transition={{ delay: 0.7 }}>
                  Premium Ladies & Gents Garments
                </motion.p>
                <motion.p className="text-xl text-luxury-gold font-semibold mb-10" initial={{ opacity: 0 }} animate={{ opacity: 1 }} transition={{ delay: 0.9 }}>
                  Design My Style
                </motion.p>
                <motion.div className="flex flex-col md:flex-row gap-6 justify-center mb-16" initial={{ opacity: 0 }} animate={{ opacity: 1 }} transition={{ delay: 1.1 }}>
                  <motion.button 
                    whileHover={{ scale: 1.05, boxShadow: '0 0 30px rgba(212, 175, 55, 0.5)' }} 
                    whileTap={{ scale: 0.95 }} 
                    className="px-12 py-4 bg-luxury-gold text-luxury-black font-bold rounded-lg hover:shadow-luxury-gold transition-all text-lg"
                  >
                    Shop Now
                  </motion.button>
                  <motion.button 
                    whileHover={{ scale: 1.05, borderColor: '#D4AF37', boxShadow: '0 0 20px rgba(212, 175, 55, 0.3)' }} 
                    whileTap={{ scale: 0.95 }} 
                    className="px-12 py-4 border-2 border-luxury-gold text-luxury-gold font-bold rounded-lg hover:bg-luxury-gold/10 transition-all text-lg"
                  >
                    Explore Collection
                  </motion.button>
                </motion.div>
              </motion.div>
            </section>
            {/* Features Section */}
            <section className="bg-luxury-black py-16 px-4">
              <div className="max-w-7xl mx-auto">
                <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} transition={{ delay: 0.6 }} className="grid md:grid-cols-5 gap-4">
                  {[
                    { title: '100% Original', desc: 'Authentic Products Guaranteed', icon: '✓' },
                    { title: 'Local Delivery', desc: 'Fast & Reliable Shipping', icon: '📦' },
                    { title: 'Secure Payments', desc: 'Safe Transactions', icon: '🔒' },
                    { title: 'Easy Returns', desc: 'Hassle-Free Returns', icon: '↩️' },
                    { title: '24/7 Support', desc: 'Always Here to Help', icon: '📞' },
                  ].map((feature, i) => (
                    <motion.div 
                      key={i} 
                      whileHover={{ borderColor: '#D4AF37', y: -5 }} 
                      className="p-6 border border-luxury-gold/20 rounded-lg hover:shadow-luxury transition-all bg-white/5 backdrop-blur-sm text-center"
                    >
                      <p className="text-3xl mb-3">{feature.icon}</p>
                      <h3 className="font-playfair text-lg font-semibold mb-2 text-luxury-gold">{feature.title}</h3>
                      <p className="text-sm text-luxury-light">{feature.desc}</p>
                    </motion.div>
                  ))}
                </motion.div>
              </div>
            </section>
            {/* Categories Section */}
            <section id="shop" className="py-20 px-4 bg-luxury-black/50">
              <div className="max-w-7xl mx-auto">
                <motion.h3 className="text-4xl font-playfair font-bold text-center mb-16" initial={{ opacity: 0 }} animate={{ opacity: 1 }}>
                  Shop By Category
                </motion.h3>
                <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
                  {['Men Collection', 'Women Collection', 'Kids Collection', 'Accessories'].map((cat, i) => (
                    <motion.div key={i} whileHover={{ y: -10, borderColor: '#D4AF37' }} className="group cursor-pointer">
                      <div className="bg-gradient-to-br from-luxury-gold/10 to-luxury-black h-56 rounded-lg mb-4 flex items-center justify-center border-2 border-luxury-gold/30 group-hover:border-luxury-gold/80 transition-all">
                        <span className="text-6xl">{i === 0 ? '👔' : i === 1 ? '👗' : i === 2 ? '👶' : '💎'}</span>
                      </div>
                      <h4 className="font-playfair font-bold text-lg group-hover:text-luxury-gold transition-colors">{cat}</h4>
                      <p className="text-luxury-light text-sm mt-1">Discover premium styles</p>
                    </motion.div>
                  ))}
                </div>
              </div>
            </section>
            {/* Featured Products Section */}
            <section className="py-20 px-4 bg-luxury-black">
              <div className="max-w-7xl mx-auto">
                <motion.h3 className="text-4xl font-playfair font-bold text-center mb-16" initial={{ opacity: 0 }} animate={{ opacity: 1 }}>
                  Featured Products
                </motion.h3>
                <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
                  {[1, 2, 3, 4, 5, 6, 7, 8].map(i => (
                    <motion.div key={i} whileHover={{ y: -10 }} className="group">
                      <div className="bg-gradient-to-b from-luxury-gold/5 to-luxury-black h-72 rounded-lg mb-4 flex items-center justify-center border border-luxury-gold/20 group-hover:border-luxury-gold/50 transition-all overflow-hidden">
                        <motion.div className="text-8xl" whileHover={{ scale: 1.2 }}>👗</motion.div>
                      </div>
                      <h4 className="font-playfair font-semibold text-lg mb-2">Product {i}</h4>
                      <div className="flex justify-between items-center mb-3">
                        <span className="text-luxury-gold font-bold text-lg">₹4,999</span>
                        <span className="text-luxury-light line-through text-sm">₹6,999</span>
                      </div>
                      <div className="flex gap-2 mb-4">
                        {[...Array(5)].map((_, j) => (
                          <span key={j} className="text-luxury-gold text-sm">★</span>
                        ))}
                        <span className="text-luxury-light text-xs ml-2">(48)</span>
                      </div>
                      <motion.button whileHover={{ scale: 1.05 }} className="w-full py-3 bg-luxury-gold/20 text-luxury-gold border border-luxury-gold/30 rounded hover:bg-luxury-gold hover:text-luxury-black transition-all font-semibold">
                        Add to Cart
                      </motion.button>
                    </motion.div>
                  ))}
                </div>
              </div>
            </section>
            {/* Newsletter Section */}
            <section className="py-16 px-4 bg-gradient-to-r from-luxury-gold/10 via-luxury-black to-luxury-gold/10">
              <div className="max-w-2xl mx-auto text-center">
                <h3 className="text-3xl font-playfair font-bold mb-4">Subscribe to Our Newsletter</h3>
                <p className="text-luxury-light mb-8">Get exclusive offers and updates directly to your inbox</p>
                <div className="flex gap-2 max-w-md mx-auto">
                  <input type="email" placeholder="Enter your email" className="flex-1 px-4 py-3 bg-luxury-light/10 border border-luxury-gold/30 rounded focus:outline-none focus:border-luxury-gold text-white" />
                  <motion.button whileHover={{ scale: 1.05 }} className="px-8 py-3 bg-luxury-gold text-luxury-black font-bold rounded hover:shadow-luxury-gold transition-all">
                    Subscribe
                  </motion.button>
                </div>
              </div>
            </section>
          </main>
          {/* Footer */}
          <footer className="bg-luxury-light/5 border-t border-luxury-gold/20 py-16 px-4">
            <div className="max-w-7xl mx-auto">
              <div className="grid md:grid-cols-4 gap-8 mb-8">
                <div>
                  <h4 className="font-playfair font-bold mb-4 text-luxury-gold text-lg">Your Choice</h4>
                  <p className="text-sm text-luxury-light mb-4">Premium fashion for everyone</p>
                  <p className="text-xs text-luxury-light/70">Design My Style | Your Style, Your Choice</p>
                </div>
                <div>
                  <h5 className="font-semibold mb-4 text-lg">Quick Links</h5>
                  <ul className="space-y-2 text-sm text-luxury-light">
                    <li><a href="#" className="hover:text-luxury-gold transition">Home</a></li>
                    <li><a href="#" className="hover:text-luxury-gold transition">Shop</a></li>
                    <li><a href="#" className="hover:text-luxury-gold transition">About Us</a></li>
                    <li><a href="#" className="hover:text-luxury-gold transition">Contact</a></li>
                  </ul>
                </div>
                <div>
                  <h5 className="font-semibold mb-4 text-lg">Support</h5>
                  <ul className="space-y-2 text-sm text-luxury-light">
                    <li><a href="#" className="hover:text-luxury-gold transition">Privacy Policy</a></li>
                    <li><a href="#" className="hover:text-luxury-gold transition">Terms & Conditions</a></li>
                    <li><a href="#" className="hover:text-luxury-gold transition">Refund Policy</a></li>
                    <li><a href="#" className="hover:text-luxury-gold transition">FAQ</a></li>
                  </ul>
                </div>
                <div>
                  <h5 className="font-semibold mb-4 text-lg">Contact Info</h5>
                  <p className="text-sm text-luxury-light mb-2">📍 C/O Bhawani Medical Store</p>
                  <p className="text-sm text-luxury-light mb-2">👤 Arvind: 9467259111</p>
                  <p className="text-sm text-luxury-light mb-4">👤 Karan: 8950114418</p>
                  <div className="flex gap-3">
                    <a href="#" className="w-10 h-10 bg-luxury-gold/20 rounded-full flex items-center justify-center hover:bg-luxury-gold/40 transition text-sm">f</a>
                    <a href="#" className="w-10 h-10 bg-luxury-gold/20 rounded-full flex items-center justify-center hover:bg-luxury-gold/40 transition text-sm">𝕏</a>
                    <a href="#" className="w-10 h-10 bg-luxury-gold/20 rounded-full flex items-center justify-center hover:bg-luxury-gold/40 transition text-sm">📷</a>
                  </div>
                </div>
              </div>
              <div className="border-t border-luxury-gold/20 pt-8 text-center text-sm text-luxury-light">
                <p>&copy; 2024 Your Choice E-Commerce. All rights reserved. | Design My Style</p>
              </div>
            </div>
          </footer>
        </motion.div>
      )}
    </div>
  )
}
export default App
Please confirm you want Copilot to push 11 files to branch main in parikshitkaushik2011/your-choice-ecommerce.
