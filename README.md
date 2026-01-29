# E-Shop - Single Vendor E-commerce Platform

Django-based e-commerce application with SSLCommerz payment integration, product management, cart functionality, and order processing.

## ✨ Features

- User authentication (manual + Google OAuth via Django Allauth)
- Product browsing with category, price, and rating filters
- Shopping cart with persistent session storage
- SSLCommerz payment gateway integration
- Order management with status tracking
- Product ratings and reviews (verified purchasers only)
- Email notifications for order confirmations
- Admin dashboard for inventory and order management

## 🛠 Tech Stack

**Backend:** Django 5.2.7, Python 3.x, SQLite3  
**Frontend:** Django Templates, HTML5, CSS3, JavaScript  
**Integrations:** Django Allauth, SSLCommerz, Pillow, Django Environ

## 📁 Project Structure

```
eshop/
├── eshop/                  # Project settings & configuration
├── shop/                   # Main app (models, views, forms, urls)
├── templates/shop/         # HTML templates
├── static/                 # CSS, JS, images
├── media/products/         # Product images
├── db.sqlite3             # Database
└── requirements.txt       # Dependencies
```

## 🗄 Database Models

- **Category** - Product categories with slug
- **Product** - Products with price, stock, images, availability
- **Rating** - User reviews (1-5 stars) with comments
- **Cart/CartItem** - Shopping cart management
- **Order/OrderItem** - Order processing with status tracking

## 🚀 Quick Start

```bash
# Clone and setup
git clone <repository-url>
cd eshop
python -m venv venv
venv\Scripts\activate  # Windows
pip install -r requirements.txt

# Configure environment
# Create .env in eshop/ directory with:
SECRET_KEY=your-secret-key
DEBUG=True
SSLCOMMERZ_STORE_ID=your-store-id
SSLCOMMERZ_STORE_PASSWORD=your-store-password
SSLCOMMERZ_PAYMENT_URL=https://sandbox.sslcommerz.com/gwprocess/v4/api.php
EMAIL_HOST=smtp.gmail.com
EMAIL_HOST_USER=your-email@gmail.com
EMAIL_HOST_PASSWORD=your-app-password
EMAIL_PORT=587
EMAIL_USE_TLS=True

# Initialize database
python manage.py migrate
python manage.py createsuperuser

# Run server
python manage.py runserver
```

Access at: http://127.0.0.1:8000/ | Admin: http://127.0.0.1:8000/admin/ | Live Link: [Royal Shop](https://royal-shop-uf36.onrender.com)

## 🔌 Key Endpoints

| Endpoint                            | Description                     |
| ----------------------------------- | ------------------------------- |
| `/`                                 | Homepage with featured products |
| `/products/`                        | Product list with filters       |
| `/products/<category_slug>/`        | Category-filtered products      |
| `/products/detail/<slug>/`          | Product details                 |
| `/cart/`                            | Shopping cart                   |
| `/checkout/`                        | Checkout page                   |
| `/payment/process/`                 | Payment initiation              |
| `/profile/`                         | User profile & order history    |
| `/login/`, `/register/`, `/logout/` | Authentication                  |

**Filters:** `?min_price=100&max_price=5000&rating=4&search=keyword`

## 💳 Payment Flow

1. User completes checkout → Order created
2. Redirect to SSLCommerz gateway
3. Payment processed
4. Callback: Success (paid=True, stock updated, email sent) | Fail/Cancel (order canceled)

**Sandbox:** Use SSLCommerz sandbox credentials for testing

## ⚙ Configuration

**Environment Variables Required:**

- `SECRET_KEY`, `DEBUG`, `ALLOWED_HOSTS`
- `SSLCOMMERZ_STORE_ID`, `SSLCOMMERZ_STORE_PASSWORD`, `SSLCOMMERZ_PAYMENT_URL`
- `EMAIL_HOST`, `EMAIL_HOST_USER`, `EMAIL_HOST_PASSWORD`, `EMAIL_PORT`, `EMAIL_USE_TLS`

**Production:**

- Set `DEBUG=False`
- Use PostgreSQL/MySQL
- Configure HTTPS & SSL certificates
- Enable security middleware

## 👨‍💼 Admin Panel

Access `/admin/` to manage:

- Products & Categories (auto-slug generation)
- Orders & status updates
- Users & permissions
- Reviews & ratings
- Cart monitoring

## 🔐 Security

- CSRF protection enabled
- Login required decorators on protected routes
- Password validation
- Environment variables for secrets
- Social auth via OAuth 2.0

---

**Built with Django 5.2.7** | © 2024 E-Shop 
