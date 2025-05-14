# 🧾 Coupon System MVP (Go Backend)

A production-ready, modular Coupon System built in Go for a **medicine ordering platform**. This MVP supports **admin-side coupon creation** and **coupon validation** based on a wide variety of constraints (e.g., expiry, usage type, category, inventory, and time windows).

---

## 📦 Features

- ✅ Admin coupon creation and management
- 🧠 Complex coupon validation logic
- 📋 Supports one-time, multi-use, and time-based coupons
- ⏱️ Validates based on expiry, time windows, cart content, and order value
- 🔁 Concurrency-safe operations
- 💾 Persistent storage (SQLite/Postgres)
- ⚡ LRU cache for performance boost
- 🌐 RESTful API with Swagger documentation
- 🐳 Fully Dockerized

---

## 🔗 API Endpoints

### `POST /admin/coupons`
- **Create a coupon** (Admin-only)
- Fields: `coupon_code`, `expiry_date`, `usage_type`, `applicable_medicine_ids`, `applicable_categories`, `min_order_value`, `valid_time_window`, `terms_and_conditions`, `discount_type`, `discount_value`, `max_usage_per_user`

---

### `GET /coupons/applicable`
Returns a list of coupons applicable to a specific cart context.

**Request Body:**
```json
{
  "cart_items": [
    { "id": "med_123", "category": "painkiller" }
  ],
  "order_total": 700,
  "timestamp": "2025-05-05T15:00:00Z"
}
