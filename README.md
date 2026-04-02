# Event-Management-
1.  AIM To design and develop a fully functional Event Management Website using HTML, CSS, JavaScript (front-end) and Python Flask (back-end), enabling users to create, browse, register for, and manage events through a dynamic and responsive web interface.



# 🎟 EventHub — Event Management Website
**Experiment 4 | Web Development Laboratory | B.Tech Semester IV**

---

## 🗂 Project Structure

```
event_management_website/
├── app.py                          ← Flask backend (all routes + DB logic)
├── requirements.txt                ← Python dependencies
├── events.db                       ← SQLite DB (auto-created on first run)
├── README.md
├── templates/
│   ├── base.html                   ← Base layout (navbar, footer)
│   ├── index.html                  ← Landing / home page
│   ├── events.html                 ← Events listing with search & filter
│   ├── register.html               ← Registration form + JS validation
│   ├── admin.html                  ← Admin dashboard
│   ├── admin_login.html            ← Admin login
│   └── admin_event_form.html       ← Add / Edit event form
└── static/
    ├── css/style.css               ← Complete CSS (responsive)
    └── js/script.js                ← Global JavaScript
```

---

## 🚀 Setup & Run

### 1. Install Python (3.8+)
Download from https://python.org

### 2. Install Flask
```bash
pip install -r requirements.txt
```

### 3. Run the App
```bash
python app.py
```

### 4. Open in Browser
```
http://127.0.0.1:5000
```

---

## 🔑 Admin Access
- URL: `http://127.0.0.1:5000/admin`
- Password: `admin123`

---

## 📡 REST API Routes

| Method | Route                    | Description             |
|--------|--------------------------|-------------------------|
| GET    | `/`                      | Home / landing page     |
| GET    | `/events`                | Browse all events       |
| GET    | `/events?search=...`     | Search events           |
| GET    | `/events?category=...`   | Filter by category      |
| GET    | `/event/<id>`            | Event detail page       |
| GET    | `/register`              | Registration form       |
| POST   | `/register`              | Submit registration     |
| GET    | `/admin`                 | Admin dashboard         |
| GET    | `/admin/add`             | Add event form          |
| POST   | `/admin/add`             | Save new event          |
| GET    | `/admin/edit/<id>`       | Edit event form         |
| POST   | `/admin/edit/<id>`       | Save edited event       |
| POST   | `/admin/delete/<id>`     | Delete event            |
| GET    | `/api/events`            | JSON API (all events)   |

---

## 🗄 Database Schema

```sql
CREATE TABLE events (
    id          INTEGER  PRIMARY KEY AUTOINCREMENT,
    name        TEXT     NOT NULL,
    description TEXT,
    date        TEXT     NOT NULL,
    time        TEXT     NOT NULL DEFAULT '10:00',
    venue       TEXT     NOT NULL,
    category    TEXT     NOT NULL DEFAULT 'General',
    image_url   TEXT     DEFAULT '',
    capacity    INTEGER  DEFAULT 100,
    rsvp_count  INTEGER  DEFAULT 0,
    created_at  TEXT     DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE registrations (
    id          INTEGER  PRIMARY KEY AUTOINCREMENT,
    event_id    INTEGER  NOT NULL,
    full_name   TEXT     NOT NULL,
    email       TEXT     NOT NULL,
    phone       TEXT     NOT NULL,
    tickets     INTEGER  NOT NULL DEFAULT 1,
    created_at  TEXT     DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (event_id) REFERENCES events(id)
);
```

---

## ✅ Tasks Completed

| Task | Description | Status |
|------|-------------|--------|
| 1 | Project setup, Flask config, landing page | ✅ |
| 2 | Events listing with Jinja2 templates | ✅ |
| 3 | Responsive CSS with Flexbox/Grid | ✅ |
| 4 | Registration form with JS validation + Flask POST | ✅ |
| 5 | Admin panel — Add/Edit/Delete events with session auth | ✅ |
| 6 | Live search, category filter, RSVP counter (Bonus) | ✅ |

---

## 📚 References
- Flask Documentation: https://flask.palletsprojects.com
- Jinja2 Templates: https://jinja.palletsprojects.com
- MDN Web Docs (HTML/CSS/JS): https://developer.mozilla.org
- Google Fonts (Playfair Display, Outfit): https://fonts.google.com
- Unsplash (sample images): https://unsplash.com
