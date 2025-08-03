# E-Commerce Backend API

A robust, scalable Django REST API for managing an e-commerce product catalog with advanced features including user authentication, product management, cart functionality, and order processing.

## 🚀 Features

### Core Features
- **User Authentication & Authorization**: JWT-based authentication with secure user management
- **Product Management**: Complete CRUD operations for products and categories
- **Advanced Filtering & Search**: Multi-parameter filtering, sorting, and search functionality
- **Cart & Wishlist**: Session-based cart management with wishlist functionality
- **Order Processing**: Complete order lifecycle management with status tracking
- **Product Reviews & Ratings**: User-generated reviews with rating system
- **Database Optimization**: Comprehensive indexing for high-performance queries

### Technical Features
- **RESTful API Design**: Clean, consistent API endpoints following REST principles
- **Comprehensive Documentation**: Auto-generated Swagger/OpenAPI documentation
- **Advanced Pagination**: Efficient pagination for large datasets
- **Data Validation**: Robust input validation and error handling
- **Performance Optimization**: Database query optimization with select_related and prefetch_related
- **Security**: JWT authentication, password validation, and secure endpoints

## 🛠 Technology Stack

- **Framework**: Django 5.2.4
- **API**: Django REST Framework 3.16.0
- **Authentication**: JWT (djangorestframework-simplejwt 5.5.1)
- **Database**: PostgreSQL
- **Documentation**: Swagger/OpenAPI (drf-yasg 1.21.10)
- **Filtering**: django-filter 25.1
- **Database Driver**: psycopg2-binary 2.9.10

## 📋 Prerequisites

- Python 3.8+
- PostgreSQL
- pip

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone <repository-url>
cd Alx-E-Commerce-Backend
```

### 2. Create Virtual Environment
```bash
python -m venv venv
# On Windows
venv\Scripts\activate
# On macOS/Linux
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Database Setup
Create a PostgreSQL database and update the database settings in `ecommerce_backend/settings.py`:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'your_db_name',
        'USER': 'your_db_user',
        'PASSWORD': 'your_db_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

### 5. Run Migrations
```bash
cd ecommerce_backend
python manage.py makemigrations
python manage.py migrate
```

### 6. Create Superuser
```bash
python manage.py createsuperuser
```

### 7. Run the Development Server
```bash
python manage.py runserver
```

The API will be available at `http://127.0.0.1:8000/`

## 📚 API Documentation

### Base URL
```
http://127.0.0.1:8000/api/
```

### Authentication Endpoints

#### Register User
```http
POST /api/users/register/
Content-Type: application/json

{
    "username": "john_doe",
    "email": "john@example.com",
    "password": "secure_password123",
    "password_confirm": "secure_password123",
    "first_name": "John",
    "last_name": "Doe"
}
```

#### Login
```http
POST /api/users/login/
Content-Type: application/json

{
    "email": "john@example.com",
    "password": "secure_password123"
}
```

#### Refresh Token
```http
POST /api/token/refresh/
Content-Type: application/json

{
    "refresh": "your_refresh_token"
}
```

### Product Endpoints

#### List Products
```http
GET /api/products/
Authorization: Bearer <access_token>
```

**Query Parameters:**
- `category`: Filter by category ID
- `min_price`: Minimum price filter
- `max_price`: Maximum price filter
- `min_rating`: Minimum rating filter
- `in_stock`: Filter by stock availability (true/false)
- `on_sale`: Filter sale items (true/false)
- `search`: Search in name, description, SKU
- `ordering`: Sort by name, price, rating, created_at, review_count
- `page`: Page number for pagination

#### Get Product Details
```http
GET /api/products/{product_slug}/
Authorization: Bearer <access_token>
```

#### Create Product
```http
POST /api/products/
Authorization: Bearer <access_token>
Content-Type: application/json

{
    "name": "Product Name",
    "description": "Product description",
    "price": "99.99",
    "stock": 100,
    "category_id": 1
}
```

### Category Endpoints

#### List Categories
```http
GET /api/products/categories/
Authorization: Bearer <access_token>
```

#### Get Category with Products
```http
GET /api/products/categories/{category_slug}/
Authorization: Bearer <access_token>
```

### Cart Endpoints

#### View Cart
```http
GET /api/cart/
Authorization: Bearer <access_token>
```

#### Add to Cart
```http
POST /api/cart/add/
Authorization: Bearer <access_token>
Content-Type: application/json

{
    "product_id": "uuid",
    "quantity": 2
}
```

#### Update Cart Item
```http
PUT /api/cart/items/{item_id}/
Authorization: Bearer <access_token>
Content-Type: application/json

{
    "quantity": 3
}
```

#### Remove from Cart
```http
DELETE /api/cart/items/{item_id}/delete/
Authorization: Bearer <access_token>
```

### User Profile Endpoints

#### Get User Profile
```http
GET /api/users/profile/
Authorization: Bearer <access_token>
```

#### Update Profile
```http
PUT /api/users/profile/
Authorization: Bearer <access_token>
Content-Type: application/json

{
    "first_name": "John",
    "last_name": "Doe",
    "phone_number": "+1234567890"
}
```

#### Manage Addresses
```http
GET /api/users/addresses/
POST /api/users/addresses/
PUT /api/users/addresses/{address_id}/
DELETE /api/users/addresses/{address_id}/
Authorization: Bearer <access_token>
```

### Product Reviews

#### List Product Reviews
```http
GET /api/products/{product_slug}/reviews/
Authorization: Bearer <access_token>
```

#### Create Review
```http
POST /api/products/{product_slug}/reviews/
Authorization: Bearer <access_token>
Content-Type: application/json

{
    "rating": 5,
    "title": "Great Product!",
    "comment": "This product exceeded my expectations."
}
```

## 🔍 Advanced Features

### Search & Filtering
The API supports advanced search and filtering capabilities:

- **Text Search**: Search across product names, descriptions, and SKUs
- **Price Range**: Filter products by minimum and maximum price
- **Category Filter**: Filter by specific categories
- **Rating Filter**: Filter by minimum rating
- **Stock Filter**: Filter by availability
- **Sale Items**: Filter products on sale
- **Sorting**: Sort by name, price, rating, creation date, review count

### Pagination
All list endpoints support pagination with configurable page sizes:

```http
GET /api/products/?page=2&page_size=20
```

### Database Optimization
- **Indexing**: Comprehensive database indexes for optimal query performance
- **Select Related**: Optimized queries to reduce database hits
- **Prefetch Related**: Efficient loading of related objects

## 🗄 Database Schema

### Core Models
- **User**: Extended user model with profile information
- **Category**: Product categories with hierarchical structure
- **Product**: Comprehensive product information with pricing and inventory
- **ProductImage**: Multiple images per product with ordering
- **ProductReview**: User reviews with ratings
- **Cart**: Shopping cart with session support
- **CartItem**: Individual items in cart
- **Order**: Complete order information with status tracking
- **OrderItem**: Individual items in orders
- **Payment**: Payment information and processing
- **UserAddress**: User address management

## 🔐 Security Features

- **JWT Authentication**: Secure token-based authentication
- **Password Validation**: Strong password requirements
- **Permission Classes**: Granular access control
- **Input Validation**: Comprehensive data validation
- **SQL Injection Protection**: Django ORM protection
- **XSS Protection**: Built-in Django security features

## 📊 Performance Features

- **Database Indexing**: Optimized indexes for common queries
- **Query Optimization**: Efficient database queries with select_related
- **Caching Ready**: Prepared for Redis/memcached integration
- **Pagination**: Efficient handling of large datasets
- **Lazy Loading**: Optimized loading of related objects

## 🧪 Testing

Run the test suite:
```bash
python manage.py test
```

## 📝 API Documentation

Interactive API documentation is available at:
```
http://127.0.0.1:8000/swagger/
```

## 🚀 Deployment

### Production Settings
Update `settings.py` for production:
- Set `DEBUG = False`
- Configure `ALLOWED_HOSTS`
- Use environment variables for sensitive data
- Set up proper database credentials
- Configure static file serving

### Environment Variables
```bash
export SECRET_KEY="your-secret-key"
export DATABASE_URL="postgresql://user:password@localhost/dbname"
export DEBUG="False"
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Support

For support and questions:
- Check the API documentation at `/swagger/`
- Review the Django REST Framework documentation
- Open an issue in the repository

## 🎯 Project Goals Achieved

✅ **CRUD APIs**: Complete CRUD operations for all entities
✅ **Filtering & Sorting**: Advanced filtering, sorting, and search
✅ **Pagination**: Efficient pagination for large datasets
✅ **Database Optimization**: Comprehensive indexing and query optimization
✅ **Authentication**: Secure JWT-based authentication
✅ **API Documentation**: Comprehensive Swagger documentation
✅ **Performance**: Optimized queries and database design
✅ **Security**: Secure endpoints and data validation
✅ **Scalability**: Production-ready architecture

This project demonstrates industry best practices for building scalable, secure, and performant e-commerce backend APIs.
