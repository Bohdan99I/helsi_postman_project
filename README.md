# Helsi API Testing Project (Postman)

## 📌 Завдання

Протестувати API Helsi за допомогою **Postman**, перевірити основні ендпоінти та налаштувати автоматичні тести.

---

## 📂 Структура проекту

- **helsi_collection.json** — колекція запитів:

  - 🔑 Login (отримання токена)
  - 📋 Appointments (список прийомів)
  - 🧾 Appointment Details (деталі прийому)
  - ➕ Create Appointment (створення нового запису)
  - ❌ Cancel Appointment (скасування запису)

- **helsi_environment.json** — оточення зі змінними:
  - `your_token_here` — зберігає токен після логіну
  - `appointmentId` — використовується у запитах для деталей прийому
- **README.md** — документація з інструкціями

---

## 🚀 Як використовувати

1. Встанови **Postman**.
2. Імпортуй колекцію `helsi_collection.json`.
3. Імпортуй оточення `helsi_environment.json`.
4. Активуй середовище **Helsi API Environment**.
5. Виконай запит **Login**, після чого токен збережеться автоматично.
6. Виконай **Appointments** → у тестах автоматично збережеться `appointmentId`.
7. Виконай **Appointment Details** → підтягнеться `appointmentId`.

---

## ✅ Автотести

У колекції налаштовані тести:

- **Login** → перевірка статусу `200`, збереження `token`.
- **Appointments** → перевірка статусу `200`, наявність масиву прийомів, збереження `appointmentId`.
- **Appointment Details** → перевірка статусу `200`, відповідність `appointmentId`.
- **Create Appointment (POST)** → перевірка статусу `201`, збереження `appointmentId`.
- **Cancel Appointment (DELETE)** → перевірка статусу `200 або 204`.

---

## 🔹 Приклади cURL

### GET /doctors

```bash
curl -X GET "https://api.helsi.me/doctors"
-H "Accept: application/json"
```

### POST /appointments

```bash
curl -X POST "https://api.helsi.me/appointments"
-H "Content-Type: application/json"
-H "Authorization: Bearer <your_token_here>"
-d '{
        "doctorId": "12345",
        "patientId": "67890",
        "datetime": "2025-09-25T10:00:00Z",
        "reason": "Консультація"
      }'
```

### GET /appointments

```bash
curl -X GET "https://api.helsi.me/appointments"
  -H "Authorization: Bearer <your_token_here>"
```

### GET /appointments/:id

```bash
curl -X GET "https://api.helsi.me/appointments/<appointmentId>"
  -H "Authorization: Bearer <your_token_here>"
```

### DELETE /appointments/:id

```bash
curl -X DELETE "https://api.helsi.me/appointments/<appointmentId>"
-H "Authorization: Bearer <your_token_here>"
```

### Як використовувати cURL

1. Замініть `<your_token_here>` на свій токен авторизації.
2. Замініть `<appointmentId>` на ID прийому, який ви хочете скасувати.
3. Виконуйте команди в терміналі (Linux, MacOS) або PowerShell/Command Prompt (Windows).

---

## 🛠️ Вимоги

- Postman 10+
- Активний обліковий запис Helsi (логін + пароль для отримання токена)

---

## 👨‍💻 Автор

Bohdan Voitov

Тестове завдання виконане для перевірки роботи з Postman та API.
