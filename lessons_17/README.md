## 1. Аналіз кіберзагроз і вибір проблеми:
    
    Одним з єлементом виявлення кібербезпекової вразливості або загрози можна вирішити за допомогою GenAI(LLM моделі) на прикладі - "Виявлення фішингових атак" через фішингові сайти.

## 2. Розробка концепції рішення:
    
    1. За основу візьмемо датасет фішингових сайтів з вже розділеними 'Safe' (0) or 'Phishing' (1) даними - https://huggingface.co/datasets/imanoop7/phishing_url_classification
        
    2. Також для вирішення задачі виберемо платну LLM модель OpenAI(gpt-4o-mini). Ця модель вже добре навчена та є відносно не дорогою в обробці таких запитів(Приблизна вартість такого рішення на датасеті в 100 запитів обійшлось в 0,00276$ або ж 0,11 копійок)

    3. Основною функціональністю такого рішення є виявлення небезпечник(фішингових) сайтів для запобігання проникнення в великі корпоративні системи.

## 3. Реалізація прототипу:

    Були використані такі фреймворки як: Hugging Face та OpenAI

## 4. Тестування і оцінка:

### Як добре вона виявляє загрозу?

| METRICS | RESULT |
|----------------|:---------:|
|Accuracy | 99.00% |
|Precision | 100.00% |
|Recall | 98.18% |
|F1 Score | 99.08% |

З метрик ми бачимо, що модель дуже гарно розпізнає де є фішинговий сайт, а де ні.

### Чи можна її адаптувати до інших сценаріїв?

Так, ми можемо її адаптувати задачу, які детектить фішингові розсилки, це також є одним з єлементом кібербезпекової вразливості через отримання небезпечних листів з сайтами та їх відкриттям.

### Чи можлива помилкова генерація?

Так, як і будь-яка LLM модель може видавати неправдиву інформацію(бути упередженим або ж галюцинувати) або наприклад навчитися на "отруєних даних" і видавати погані результати. 

### Чи є ризик зловживання?

Так, але щоб запобігати такими зловживанням необхідно:
    1. Мати обмежений доступ до ресурсу використання OpenAI(бажано мати Private Tenet в Microsoft Azure), який вирішує багато вразливостей(кібератак на систему, витоку даних, гранульований доступ).
    2. Обмежити доступ до prompt інструкції, щоб забезпечити дане рішення від prompt injections.

## 5. Рекомендації щодо використання та подальшого розвитку:

1) Дане рішення можна використовувати для виявлення загрози співробітників крупної компанії. Наприклад: співробітник заходить в інтернет на невідомий сайт, внутрішньо-безпекові протоколи не спрацювали, але маємо додаткову перевірку через дане рішення, яке повернула відповідь, що сайт може мати шкідливу інформацію і відноситься до фішингового.

2) Одним з єлементом масштабування даного рішення може бути детекція фішингових листів з текстом та посиланням на фішинговий сайт.