# DecorMind - AI-Based Interior Planning System

## Overview

DecorMind is an AI-powered platform for generating modern interior designs automatically from room images. Users can upload photos of their rooms and receive AI-generated design recommendations with three different visualization types: POP ceiling designs, TV unit designs, and furniture recommendations.

## 🌟 Features

### User Features
- **AI Design Generation** - Upload room images and get AI-generated interior designs
- **Multiple Design Styles** - POP Ceiling Designs, TV Unit Designs, Furniture Recommendations
- **Download Designs** - Save generated designs as images
- **Design History** - View all previously generated designs
- **User Feedback System** - Rate and provide feedback on generated designs (1-5 stars)
- **Responsive Dashboard** - Personal dashboard to manage projects

### Admin Features
- **User Management** - View and manage all platform users
- **User Design Gallery** - View complete design history of any user with gallery view
- **Feedback Management** - View all user feedback with stats, filter by status, and respond to feedback
- **Admin Dashboard** - Statistics and analytics overview
- **User Designs Gallery** - Beautiful gallery view showing:
  - Original room photos
  - All generated design variations
  - Image lightbox viewer
  - Download functionality for all images

### Authentication
- **User Registration** - Create new user accounts
- **Secure Login** - Username/email and password authentication
- **Password Visibility Toggle** - Show/hide password option during login
- **Staff Accounts** - Admin panel access for staff users

## 🛠 Tech Stack

### Backend
- **Framework**: Django 4.2
- **Language**: Python 3.14
- **Database**: SQLite3
- **ORM**: Django ORM

### Frontend
- **CSS Framework**: Bootstrap 5.3.0
- **Icons**: Font Awesome 6.4.0
- **JavaScript**: Vanilla JavaScript (no framework)
- **Styling**: Custom CSS with animations and gradients

### AI/ML
- **Hugging Face Hub** - For model access
- **Pillow** - Image processing

### Environment
- **Environment Variables**: python-dotenv
- **Development Server**: Django Development Server

## 📦 Project Structure

```
DecorMind/
├── DecorMind/                    # Django project settings
│   ├── settings.py              # Project configuration
│   ├── urls.py                  # Main URL router
│   ├── asgi.py                  # ASGI configuration
│   └── wsgi.py                  # WSGI configuration
│
├── core/                         # Main application
│   ├── models.py                # Database models
│   ├── views.py                 # View functions and business logic
│   ├── urls.py                  # App URL routing
│   ├── forms.py                 # Django forms
│   ├── admin.py                 # Django admin configuration
│   ├── context_processors.py    # Template context processors
│   ├── migrations/              # Database migrations
│   └── tests.py                 # Unit tests
│
├── templates/                   # HTML templates
│   ├── base.html                # Base template with navigation
│   ├── index.html               # Home/landing page
│   ├── auth/                    # Authentication templates
│   │   ├── login.html           # Login page
│   │   └── register.html        # Registration page
│   ├── feedback/                # Feedback templates
│   │   ├── submit_feedback.html # Feedback submission
│   │   └── my_feedbacks.html    # User's feedback history
│   ├── admin_panel/             # Admin templates
│   │   ├── feedbacks.html       # Admin feedback management
│   │   ├── feedback_detail.html # Individual feedback view
│   │   ├── user_designs.html    # User designs gallery
│   │   └── admin_users.html     # User management table
│   ├── dashboard/               # User dashboard
│   └── results.html             # Design results page
│
├── media/                       # User uploads and generated images
│   ├── uploads/                 # User uploaded room images
│   └── generated/               # AI-generated design images
│
├── static/                      # Static files (CSS, JS)
├── db.sqlite3                   # SQLite database
├── manage.py                    # Django management script
└── requirements.txt             # Python dependencies
```

## 🚀 Installation & Setup

### Prerequisites
- Python 3.8+
- pip package manager
- Virtual environment (recommended)

### Step 1: Clone Repository
```bash
git clone <repository-url>
cd "DecorMind-AI Based interior Planning System"
```

### Step 2: Create Virtual Environment
```bash
python -m venv .venv
```

### Step 3: Activate Virtual Environment

**Windows (PowerShell):**
```powershell
.\.venv\Scripts\Activate.ps1
```

**Windows (Command Prompt):**
```cmd
.venv\Scripts\activate.bat
```

**macOS/Linux:**
```bash
source .venv/bin/activate
```

### Step 4: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 5: Configure Environment Variables
Create a `.env` file in the project root:
```
DJANGO_SECRET_KEY=your-secret-key
DEBUG=True
ALLOWED_HOSTS=127.0.0.1,localhost
```

### Step 6: Apply Database Migrations
```bash
cd DecorMind
python manage.py migrate
```

### Step 7: Create Superuser (Admin)
```bash
python manage.py createsuperuser
```

### Step 8: Run Development Server
```bash
python manage.py runserver
```

The application will be accessible at `http://127.0.0.1:8000/`

## 📋 Database Models

### User
- Built-in Django User model with username, email, password
- Extended with UserProfile (OneToOne relationship)

### UserProfile
- Stores additional user information
- Links to User model

### RoomDesignRequest
- Room type (Living Room, Bedroom, Kitchen, etc.)
- Category (Traditional, Modern, Minimalist, etc.)
- Room dimensions (length, width, height)
- Original room image
- Timestamps (created_at, updated_at)

### GeneratedDesign
- Linked to RoomDesignRequest
- Design name (Design1, Design2, etc.)
- View type (POP Ceiling, TV Unit, Furniture)
- Generated image file
- Timestamps

### Feedback
- User rating (1-5 stars)
- Feedback message
- Admin reply (optional)
- Read status
- Timestamps (created_at, replied_at)

### ActivityLog
- Tracks user actions for analytics
- Action type, timestamp, user reference

## 🔗 URL Routes

### Public Routes
- `/` - Home page
- `/register/` - User registration
- `/login/` - User login
- `/logout/` - User logout

### User Routes (Authenticated)
- `/dashboard/` - User dashboard
- `/upload/` - Upload room image
- `/results/<int:pk>/` - View design results
- `/my-designs/` - View all user designs
- `/profile/` - Edit user profile
- `/my-feedbacks/` - View user feedback history
- `/feedback/submit/<int:design_id>/` - Submit feedback

### Admin Routes (Staff Only)
- `/management/dashboard/` - Admin dashboard
- `/management/users/` - User management
- `/management/feedbacks/` - All feedbacks management
- `/management/feedback/<int:feedback_id>/` - View/reply to feedback
- `/management/feedback/delete/<int:feedback_id>/` - Delete feedback
- `/admin-panel/users/<int:user_pk>/designs/` - View user's design gallery

## 🎨 Key Features Explained

### AI Design Generation
1. User uploads room image
2. Image is processed and sent to AI model
3. AI generates three design variations
4. Designs are displayed with download options
5. User can provide feedback on quality

### Feedback System
- Users can rate designs 1-5 stars
- Leave detailed feedback messages
- Admin can view all feedback with statistics
- Admin can respond to feedback
- Users see admin responses in their feedback history
- Unread feedback count displayed in admin navbar

### Admin User Designs Gallery
- Admins can view complete design history of any user
- Gallery shows original room photo
- Displays all design variations (POP, TV, Furniture)
- Lightbox modal for full-size image viewing
- Download buttons for all images
- User summary with statistics
- Responsive gallery layout

### Authentication
- Secure password hashing with Django's built-in system
- Password visibility toggle on login page
- Login required decorators on protected views
- Admin-only routes with staff check

## 🎯 Design Philosophy

### Frontend
- **Aesthetic Design**: Navy (#0f1c35) and Gold (#c9a155) color scheme
- **Responsive Layout**: Works on desktop, tablet, and mobile
- **Smooth Animations**: Floating cards, scroll reveals, hover effects
- **User-Friendly**: Intuitive navigation and clear CTAs

### Backend
- **Modular Structure**: Separated views, forms, models
- **Django Best Practices**: Using decorators, context processors, ORM
- **Performance**: Prefetch_related for optimized queries
- **Security**: CSRF protection, secure password handling

## 🧪 Testing

### Run All Tests
```bash
python manage.py test
```

### Run Specific App Tests
```bash
python manage.py test core
```

### Check Django Configuration
```bash
python manage.py check
```

## 📱 API Endpoints Summary

| Method | Endpoint | Purpose |
|--------|----------|---------|
| GET | `/` | Home page |
| POST | `/register/` | Register new user |
| POST | `/login/` | User login |
| GET | `/logout/` | User logout |
| GET | `/dashboard/` | User dashboard |
| POST | `/upload/` | Upload room image |
| GET | `/results/<id>/` | View design results |
| GET | `/my-designs/` | View user designs |
| POST | `/feedback/submit/<id>/` | Submit feedback |
| GET | `/my-feedbacks/` | View feedback history |
| GET | `/management/users/` | Admin: View users |
| GET | `/management/feedbacks/` | Admin: View feedbacks |
| POST | `/management/feedback/<id>/` | Admin: Reply to feedback |
| GET | `/admin-panel/users/<id>/designs/` | Admin: View user gallery |

## 🔐 Security Features

- **CSRF Protection**: All forms include CSRF tokens
- **SQL Injection Prevention**: Django ORM usage
- **XSS Protection**: Template auto-escaping
- **Password Security**: Hashed passwords with Django auth
- **Access Control**: Login required and staff checks on admin routes
- **File Upload Security**: File validation on image uploads

## 🐛 Troubleshooting

### Database Issues
```bash
# Reset database (development only)
rm db.sqlite3
python manage.py migrate
python manage.py createsuperuser
```

### Static Files Not Loading
```bash
python manage.py collectstatic
```

### Port Already in Use
```bash
python manage.py runserver 8001
```

### Permission Errors
Ensure virtual environment is activated and all dependencies are installed.

## 📝 Dependencies

See `requirements.txt` for complete list. Key packages:
- Django==4.2
- Pillow (image processing)
- python-dotenv (environment variables)
- huggingface-hub (AI models)
- requests (HTTP library)

## 🤝 Contributing

1. Create a new branch for features
2. Make changes and test thoroughly
3. Submit pull request with description
4. Wait for review and merge

## 📄 License

This project is provided as-is for educational and commercial use.

## 📧 Support

For issues, questions, or suggestions, please contact:
- **Email**: vidyakarabisti27@gmail.com
- **Location**: hubli, India

---

**DecorMind** - Transform your spaces with AI-generated design solutions ✨
