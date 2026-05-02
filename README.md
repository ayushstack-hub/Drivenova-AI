# 🚗 Drivenova AI — Smart Car Rental Platform

A modern, full-stack premium Indian car rental web application powered by 
AI assistant Nova. Book premium cars across 10+ Indian cities with 
transparent pricing, real-time trip tracking, and instant email confirmations.

![Drivenova AI](https://img.shields.io/badge/Drivenova-AI%20Car%20Rental-blue?style=for-the-badge)
![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript)
![Supabase](https://img.shields.io/badge/Supabase-Backend-3ECF8E?style=for-the-badge&logo=supabase)
![Tailwind](https://img.shields.io/badge/Tailwind-CSS-06B6D4?style=for-the-badge&logo=tailwindcss)

---

## 🌟 Live Demo

> Run locally at `http://localhost:8080` after setup

---

## ✨ Features

- 🤖 **Nova AI Assistant** — Groq-powered LLaMA chatbot for instant
  customer support and car recommendations
- 🚗 **11+ Premium Cars** — Hatchbacks, Sedans, SUVs, MUVs available
  across 10+ Indian cities
- 📅 **Smart Booking System** — Real-time car availability with
  transparent pricing including GST and insurance breakdown
- 📧 **Email Notifications** — Automatic booking confirmation emails
  to customers and admin via Resend API
- 📍 **Google Maps Integration** — Pickup location display and
  directions after booking confirmation
- 🛡️ **Admin Dashboard** — Complete fleet management, revenue
  analytics, customer tracking, and booking monitoring
- 👤 **Role-Based Access** — Separate dashboards for customers
  and admin users
- 🔔 **Real-Time Notifications** — In-app booking and payment
  notifications
- 🎟️ **Coupon System** — Create and manage discount coupons
- 📊 **Revenue Analytics** — Visual revenue charts with
  monthly breakdown
- 🔐 **Secure Authentication** — Supabase Auth with email
  verification and JWT tokens

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + TypeScript |
| Styling | Tailwind CSS + shadcn/ui |
| Backend | Supabase (PostgreSQL) |
| Authentication | Supabase Auth |
| AI Chatbot | Groq API (LLaMA 3) |
| Email Service | Resend API |
| Maps | Google Maps Embed |
| Edge Functions | Supabase Deno Functions |
| Build Tool | Vite |
| Charts | Recharts |
| Icons | Lucide React |

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ and npm
- Supabase account (free)
- Groq API key (free — 14,400 requests/day)
- Resend API key (free — 3,000 emails/month)

### Installation

```sh
# Step 1: Clone the repository
git clone https://github.com/yourusername/drivenova-ai.git

# Step 2: Navigate to project directory
cd drivenova-ai

# Step 3: Install dependencies
npm i

# Step 4: Create environment file
cp .env.example .env

# Step 5: Add your environment variables to .env
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key

# Step 6: Start development server
npm run dev
```

---

## 🔑 Environment Variables

Create a `.env` file in the root directory:

```env
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

### Supabase Edge Function Secrets

Add these in Supabase Dashboard → Edge Functions → Secrets:
GROQ_API_KEY=your_groq_api_key
RESEND_API_KEY=your_resend_api_key

---

## 📁 Project Structure
drivenova-ai/
├── src/
│   ├── components/
│   │   ├── Navbar.tsx           # Navigation with auth state
│   │   ├── AIChatWidget.tsx     # Nova AI chat widget
│   │   ├── NotificationBell.tsx # Real-time notifications
│   │   └── TripTracker.tsx      # Trip progress tracker
│   ├── pages/
│   │   ├── Landing.tsx          # Home page with car search
│   │   ├── Auth.tsx             # Login and register
│   │   ├── Cars.tsx             # Car listing with filters
│   │   ├── CarDetail.tsx        # Car details and booking form
│   │   ├── Booking.tsx          # Complete booking flow
│   │   ├── Dashboard.tsx        # My Trips dashboard
│   │   ├── Admin.tsx            # Admin panel
│   │   ├── About.tsx            # About page
│   │   └── Contact.tsx          # Contact page
│   ├── contexts/
│   │   └── AuthContext.tsx      # Global auth state management
│   ├── data/
│   │   └── cars.ts              # Car data and pricing logic
│   └── integrations/
│       └── supabase/
│           └── client.ts        # Supabase client config
├── supabase/
│   └── functions/
│       ├── ai-assistant/        # Nova AI edge function (Groq)
│       └── send-email/          # Email notification function
├── public/
├── .env.example
├── package.json
├── tailwind.config.ts
├── vite.config.ts
└── README.md

---

## 🗄️ Database Schema

```sql
-- Cars table
cars (id, name, brand, type, fuel_type, transmission,
      seats, price_per_day, included_km_per_day,
      extra_km_price, image_url, rating, available_cities,
      features, is_available, is_featured)

-- Bookings table
bookings (id, user_id, car_id, pickup_city, pickup_date,
          drop_date, driver_name, driver_phone,
          driver_license, base_price, duration_days,
          total_amount, status, payment_status,
          trip_status, estimated_km)

-- User roles table
user_roles (id, user_id, role)

-- Notifications table
notifications (id, user_id, title, message, type, is_read)

-- Coupons table
coupons (id, code, discount_type, discount_value,
         description, is_active)
```

---

## 🔌 Supabase Edge Functions

### Deploy Functions

```sh
# Deploy AI assistant function
supabase functions deploy ai-assistant \
  --project-ref your-project-ref

# Deploy email notification function
supabase functions deploy send-email \
  --project-ref your-project-ref
```

---

## 🤖 Nova AI Assistant

Nova is powered by **Groq API** using the **LLaMA 3** model.
It helps customers:

- Find the right car based on budget and city
- Check pricing and included kilometers
- Answer booking related queries
- Suggest cars for specific trips like Goa, Manali, etc.

---

## 📧 Email Notifications

Powered by **Resend API**, the system sends:

- ✅ Welcome email on new user registration
- ✅ Booking confirmation email to customer
- ✅ New booking alert email to admin

---

## 👨‍💼 Admin Features

Access admin panel at `/admin` with admin credentials:

- 📊 Overview with total bookings, revenue, active trips
- 📋 All bookings table with driver details and status
- 🚗 Fleet management — enable/disable cars
- 👥 Customer list with total bookings and spending
- 🎟️ Coupon creation and management
- 🎫 Support ticket management

---

## 📱 Pages Overview

| Route | Page | Description |
|-------|------|-------------|
| `/` | Landing | Hero, search, stats |
| `/auth` | Auth | Login and register |
| `/cars` | Cars | Browse and filter cars |
| `/cars/:id` | CarDetail | Car info and booking |
| `/booking/:id` | Booking | Complete booking |
| `/dashboard` | Dashboard | My trips |
| `/admin` | Admin | Admin panel |
| `/about` | About | About Drivenova |
| `/contact` | Contact | Contact page |

---

## 🧪 Test Cases

Tested modules include:

- ✅ User Registration and Login
- ✅ Car Search and Filtering
- ✅ Booking Form Validation
- ✅ Email Notification Delivery
- ✅ Admin Dashboard Access Control
- ✅ Trip Status Updates
- ✅ Nova AI Assistant Responses

---

## 🚢 Deployment

### Deploy on Vercel

```sh
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel --prod
```

### Deploy on Netlify

```sh
# Build the project
npm run build

# Deploy dist folder to Netlify
```

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch
   `git checkout -b feature/AmazingFeature`
3. Commit your changes
   `git commit -m 'Add some AmazingFeature'`
4. Push to the branch
   `git push origin feature/AmazingFeature`
5. Open a Pull Request

---

## 👨‍💻 Author

**Ayush** — TYBSc IT Student, Mumbai University

- GitHub: [@ayushtech92](https://github.com/ayushtech92)

---

## 📄 License

This project is licensed under the MIT License.

---

## 🙏 Acknowledgements

- [Supabase](https://supabase.com) — Backend and authentication
- [Groq](https://groq.com) — AI inference for Nova chatbot
- [Resend](https://resend.com) — Email delivery service
- [shadcn/ui](https://ui.shadcn.com) — UI components
- [Tailwind CSS](https://tailwindcss.com) — Styling
- [Lucide React](https://lucide.dev) — Icons
- [Recharts](https://recharts.org) — Charts and analytics

---

⭐ Star this repo if you found it helpful!
<img width="1920" height="920" alt="Screenshot 2026-03-22 135843" src="https://github.com/user-attachments/assets/ddd4191f-bf3c-40cb-abc6-3f53dfcc664a" />
<img width="1920" height="932" alt="Screenshot 2026-03-22 181340" src="https://github.com/user-attachments/assets/0eb6881a-2673-4d3d-8885-0157c8b85733" />
<img width="1920" height="922" alt="Screenshot 2026-03-22 181813" src="https://github.com/user-attachments/assets/e4e09ec5-8600-462b-9a5b-42d19ee3f3c8" />
<img width="1920" height="930" alt="Screenshot 2026-03-22 182244" src="https://github.com/user-attachments/assets/7fb1109a-7c6c-4f9c-b41f-13ce1ce76bca" />
<img width="1920" height="925" alt="Screenshot 2026-03-22 182814" src="https://github.com/user-attachments/assets/a761272b-0129-4706-896b-02458cf5075a" />
<img width="1920" height="928" alt="Screenshot 2026-03-22 183305" src="https://github.com/user-attachments/assets/12a67244-1dac-495f-b04e-d80f416b7017" />
<img width="1920" height="921" alt="Screenshot 2026-03-22 183702" src="https://github.com/user-attachments/assets/db0b327c-54f8-4e52-882b-6e646adfbbbc" />
