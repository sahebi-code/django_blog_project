# Django Blog

![Python](https://img.shields.io/badge/python-3.10+-3776AB?logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-5.2-092E20?logo=django&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?logo=bootstrap&logoColor=white)

A blog application built with Django, featuring a full post publishing workflow, user authentication, and a responsive Bootstrap UI. Built to practice and demonstrate core Django concepts: the MVT pattern, class-based generic views, the ORM, and test-driven development.

## Features

- **Blog post CRUD** — create, read, update, and delete posts through Django's generic class-based views
- **Draft / Published workflow** — each post has a `status` field; only published posts appear in the public list, a rule verified by an automated test
- **Authentication** — sign up, log in, log out, and password reset, combining a custom signup view with Django's built-in `django.contrib.auth` views
- **Admin panel** — manage posts through Django's built-in admin site, with a custom list view (title, status, last modified) sorted by status
- **Responsive UI** — Bootstrap 5 layout with a shared base template and an auth-aware navbar
- **Automated tests** — 13 test cases covering models, URL resolution, view responses, the draft-visibility rule, and full CRUD behavior

## Tech Stack

| Layer      | Technology                          |
|------------|--------------------------------------|
| Backend    | Python, Django 5.2                  |
| Database   | SQLite (default; swappable for Postgres/MySQL) |
| Frontend   | Django Templates, Bootstrap 5       |
| Testing    | Django's built-in test framework    |

## Project Structure

```
django_blog_project/
├── accounts/              # User registration
│   ├── views.py           # SignUpView
│   └── urls.py
├── blog/                  # Core blog app
│   ├── models.py          # Post model
│   ├── views.py           # List / Detail / Create / Update / Delete views
│   ├── forms.py           # PostForm
│   ├── admin.py           # Admin site config
│   ├── tests.py           # Test suite (13 tests)
│   └── templates/blog/
├── config/                # Project settings, root URLs, WSGI/ASGI
├── templates/             # Base template + registration templates
├── manage.py
└── requirements.txt
```

## Getting Started

### Prerequisites
- Python 3.10+
- pip

### Installation

```bash
# Clone the repository
git clone https://github.com/sahebi-code/django_blog_project.git
cd django_blog_project

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Apply migrations
python manage.py migrate

# Create an admin account
python manage.py createsuperuser

# Run the development server
python manage.py runserver
```

The app will be available at `http://127.0.0.1:8000/`, and the admin site at `/admin/`.

## Usage

1. Visit the homepage to browse published posts.
2. **Sign up** or **log in** from the navbar.
3. Click **New Post** to create one — set status to `Draft` to keep it off the public list, or `Published` to make it visible.
4. Open a post's detail page to **edit** or **delete** it.
5. Manage all posts, published or draft, from the Django admin at `/admin/`.

## Running Tests

```bash
python manage.py test
```

The blog app's test suite covers model behavior, URL routing (by path and by name), draft-post visibility, 404 handling, and the create/update/delete flows.

## Roadmap

Honest next steps for taking this from a learning project toward production-ready:

- [ ] Restrict post creation/editing/deletion to authenticated users, and further limit edit/delete to each post's original author
- [ ] Filter the detail view so draft posts aren't reachable by a direct URL (currently only hidden from the list view)
- [ ] Move `SECRET_KEY` and `DEBUG` into environment variables for safe deployment
- [ ] Wire the comment form on the post detail page up to a real `Comment` model (the UI is already in place)
- [ ] Add pagination to the post list
- [ ] Add categories/tags for posts

## License

This project is licensed under the [MIT License](LICENSE).

## Author

**Mohammad** — [@sahebi-code](https://github.com/sahebi-code)
