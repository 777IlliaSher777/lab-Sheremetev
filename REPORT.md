# lab-Sheremetev
Repository for Fundamentals of Software Engineering course.

## `REPORT.md` 🧾
| # | Категорія | Де (файл/рядок) | Проблема | Чому це погано | Як виправити |
|---|----------|------------------|---------|----------------|--------------|
| 1 | Security | `main() – логування login` | Логується пароль користувача | Витік секретів у логи, компрометація акаунтів | Прибрати пароль з логів або маскувати |
| 2 | Security | `login()` | SQL Injection (конкатенація рядків) | Можна обійти авторизацію або виконати довільний SQL | Використати PreparedStatement |
| 3 | Security | `buy()` | SQL Injection в INSERT | Можливість підміни або пошкодження даних | Використати параметризований запит |
| 4 | Security | `getPrice()` | SQL Injection | Несанкціонований доступ до даних | PreparedStatement |
| 5 | Security | `DB_URL, DB_USER, DB_PASS` | Hardcoded credentials | Витік доступу до БД при публікації коду | Зберігати в environment variables або config |
| 6 | Security | `cache.put("pw:" + email, password)` | Паролі зберігаються у відкритому вигляді | Критичний ризик витоку даних | Не зберігати пароль або зберігати хеш |
| 7 | Security | `query(), update()` | Логування повного SQL-запиту | Витік персональних даних у логах | Логувати без параметрів або лише технічну інформацію |
| 8 | Correctness | `email == "admin@local"` | Порівняння String через `==` | Працює некоректно (порівняння посилань) | Використати email.equals("admin@local") |
| 9 | Correctness | `buildReport(): email.trim()` | Можливий NullPointerException | Краш програми при null | Перевірити `email == null || email.isBlank()` |
| 10 | Correctness | `for (i <= lines.size())` | Off-by-one помилка | IndexOutOfBoundsException | Замінити на `i < lines.size()` |
| 11 | Correctness | `getPrice() → return -1` | Невалідна ціна використовується в розрахунках | Некоректні суми замовлення | Кидати виняток або використовувати Optional |
| 12 | Correctness | `Integer.parseInt()` | Немає обробки NumberFormatException | Краш при нечисловому вводі | Обгорнути в try-catch |
| 13 | Maintainability | `static Map cache, lastUserEmail` | Глобальний mutable state | Важко тестувати, можливі помилки стану | Інкапсулювати в сервіс або об'єкт |
| 14 | Maintainability | `catch (Exception e) {}` | Порожні catch блоки | Помилки повністю ігноруються | Логувати або пробросити виняток |
| 15 | Maintainability | Магічні числа (1000, 7, 10, 50) | Немає пояснення логіки | Важко підтримувати та змінювати | Винести в константи |
| 16 | Architecture | `BadStoreApp` | God Class (UI + DB + бізнес-логіка + кеш) | Порушення SRP, складність масштабування та тестування | Розділити на Controller / Service / Repository |
| 17 | Architecture | `buy()` використовує lastUserEmail | Залежність від глобального стану | Порушення інкапсуляції | Передавати email параметром |
| 18 | Resource Leak | `query(), update()` | Не закриваються Connection/Statement | Витік ресурсів, можливе падіння БД | Використати try-with-resources |
| 19 | Readability | `if (ok == true)` | Зайва перевірка | Захаращення коду | Замінити на `if (ok)` |
