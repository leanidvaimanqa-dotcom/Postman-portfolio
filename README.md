# Postman-portfolio
My QA portfolio: Postman collections, API tests, and automation experiments.
## 📚 Проекты

### 1. Postman Collection - API Тестирование фильмов
**Описание:** REST API тесты для сервиса управления фильмами с динамическими переменными и тестовыми сценариями.

**Технологии:** Postman, JavaScript, Dynamic Variables

**Функциональность:**
- ✅ POST запрос для добавления фильма в batch эндпоинт
- ✅ Проверка статус кода 200
- ✅ Генерация случайных данных (названия, режиссеры, жанры, рейтинги)
- ✅ Использование встроенных функций для генерации уникальных значений
- ✅ Pre-request скрипты для подготовки тестовых данных
- ✅ Post-response скрипты для валидации ответа

**Пример Pre-request скрипта:**
```javascript
// Генерируем случайные данные для фильма
pm.environment.set("movie_year", _.random(1980, 2024));
pm.environment.set("movie_rating", _.random(1.0, 10.0, true).toFixed(1));
```

**Пример Post-response теста:**
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

if (pm.response.code === 200) {
    console.log("✅ Коллекция фильмов создана");
}
```

**Данные для batch запроса:**
```json
[
  {
    "title": "{{$randomFirstName}}",
    "director": "{{$randomFullName}}",
    "year": {{movie_year}},
    "genre": "{{$randomLastName}}",
    "rating": {{movie_rating}}
  }
]
```

---

## 🛠️ Навыки и инструменты

- **API Testing:** REST, HTTP методы (GET, POST, PUT, PATCH, DELETE)
- **Postman:** Collections, Tests, Pre-request Scripts, Dynamic Variables, Mock Servers
- **JavaScript:** Postman scripting, assertions, data generation
- **Automation:** Newman CLI для CI/CD интеграции
- **Данные:** JSON, XML, работа с динамическими переменными
- **QA методологии:** Test design, Bug reporting, Test documentation

---

## 📝 Примеры использования

### Запуск Postman коллекции через Newman:
```bash
newman run "Films (My API) Auto.postman_collection.json" --environment environment.json
```

### Интеграция с GitHub Actions:
```yaml
- name: Run Postman tests
  run: newman run collection.json --reporters cli,json
```

---

## 📖 Документация

Для деталей по каждому проекту см. папку проекта или свяжитесь со мной.

---

## 🤝 Контакты

- 🔗 [LinkedIn](https://linkedin.com/in/leonid-v-a585a7394)
- 📧 Email: leanidvaimanqa@gmail.com
- 💼 [GitHub](https://github.com/leanidvaimanqa-dotcom)
