# 📊 django-utm-tracker

A lightweight Django middleware package to track and store UTM parameters in the user's session, enabling attribution tracking for performance marketing and analytics workflows.

---

## 🚀 Features

- ✅ Automatically captures common UTM parameters from URL queries.
- ✅ Stores them in session for use across multiple views.
- ✅ Simple, non-intrusive middleware integration.
- ✅ Fully extensible and pluggable.

---

## 🔧 Installation

Install the package using pip:

```bash
pip install django-utm-tracker
```

---

## ⚙️ Setup

### 1. Add Middleware

In your Django settings, add the middleware to your `MIDDLEWARE` list:

```python
MIDDLEWARE = [
    ...
    'django_utm_tracker.middleware.UTMMiddleware',
]
```

Make sure it comes **before any middleware** that processes sessions or modifies redirects.

---

### 2. (Optional) Custom UTM Parameters

By default, it tracks:

- `utm_source`
- `utm_medium`
- `utm_campaign`
- `utm_term`
- `utm_content`
- `utm_content`
- `utm_content`
- `utm_content`
- `utm_content`
- `utm_content`
- `gclid`
- `aclk`
- `fbclid'`
- `msclkid`
- `dclid`
- `yclid`
- `gclsrc`
- `utm_id`
- `utm_referrer`
- `twcli`

You can override these by defining `UTM_PARAMETERS` in your `settings.py`:

```python
UTM_PARAMETERS = [
    'utm_source',
    'utm_medium',
    'utm_campaign',
    'utm_term',
    'utm_content',
    'ref',  # example of a custom parameter
]
```

---

## 🧪 Usage in Views

You can access UTM data from the session like this:

```python
def my_view(request):
    source = request.session.get("utm_source")
    campaign = request.session.get("utm_campaign")
    ...
```

You can then store these in your models (like a `Lead`, `Order`, etc.) if needed.

---

## 🧱 Project Structure

```text
django_utm_tracker/
├── __init__.py
├── conf.py
└── middleware.py
```

---

## 💡 Use Cases

- Tracking UTM for lead generation forms
- Measuring ad performance across landing pages
- Associating user behavior with marketing campaigns

---

## ✅ Example

For a URL like:

```
https://yourdomain.com/?utm_source=google&utm_medium=cpc&utm_campaign=spring_sale
```

The middleware will automatically populate `request.session` with:

```python
{
    'utm_source': 'google',
    'utm_medium': 'cpc',
    'utm_campaign': 'spring_sale'
}
```

---

## 🧰 Future Enhancements

- Model integration via signals or mixins
- Cookie fallback if session is cleared
- Expiry timeout for UTM session values
- Admin visibility of tracked UTM data

---

## 📜 License

MIT License

---

## 👨‍💻 Author

Built with 💙 by [Preet Sonpal](mailto:preet@weirdlabs.in)  
Brought to you by [Weird Labs](https://weirdlabs.in/)