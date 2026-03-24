---
name: monobrand-scout
description: >
  Поиск и анализ виральных монобрендов (1-5 SKU, один продукт/категория).
  Используй когда: (1) найти хайповый монобренд, (2) оценить виральность бренда/продукта,
  (3) анализ ниши для монобренда, (4) найди монобренд, виральный продукт,
  (5) скоринг бренда по виральности и продажам.
  НЕ для: мультибрендовой аналитики, общего маркетингового анализа.
---

# Monobrand Scout -- поиск виральных монобрендов

## Что такое монобренд
Бренд с 1-5 SKU в одной категории. Фокус на одном продукте, глубокое понимание клиента, виральный потенциал. Примеры: Stanley (термокружки), Ridge Wallet (кошельки), UNCO (детское белье), Crocs (клоги).

---

## Пайплайн поиска

### Вход
- Категория (опционально): детская одежда, косметика, кухня...
- Гео: РФ / глобальный / конкретная страна
- Цель: найти готовый бренд для дистрибуции / найти нишу / контент

### Этап 1. Сбор кандидатов (3 потока параллельно)

**Поток A -- Маркетплейсы (продажи):**
- Wildberries API: топ по категории, фильтр бренды с 1-5 SKU
- Ozon: аналитика через MPStats/Moneyplace
- Amazon: через JungleScout или Product Advertising API

**Поток B -- Соцсети (виральность):**
- TikTok Creative Center: трендовые продукты по категории
- Instagram: хэштеги бренда, количество Reels
- YouTube: обзоры продукта, просмотры

**Поток C -- Тренды (ранние сигналы):**
- Google Trends: растущие запросы
- Exploding Topics: ранние тренды
- Kickstarter/Indiegogo: успешные монопродукты
- Product Hunt: новые продукты

### Этап 2. Фильтрация
ИИ анализирует каждого кандидата:
- SKU count: 1-5?
- Одна категория?
- Есть UGC контент?
- Рост за последние 3-6 месяцев?

### Этап 3. Скоринг виральности

Формула:
```
Virality Score = (TikTok Views x 0.3) + (Google Trends Growth x 0.25) 
  + (UGC Count x 0.2) + (Engagement Rate x 0.15) + (Review Count x 0.1)
```

| Метрика | Источник | Вес |
|---------|----------|-----|
| TikTok просмотры по хэштегу бренда | TikTok Creative Center / API | 0.30 |
| Рост поисковых запросов (3 мес) | Google Trends / SerpAPI | 0.25 |
| Количество UGC | Instagram + TikTok | 0.20 |
| Engagement rate | SocialBlade / Meta API | 0.15 |
| Количество отзывов на маркетплейсах | WB API / Ozon / Amazon | 0.10 |

Шкала:
- 80-100: Вирусный хит (Stanley, Crocs)
- 60-79: Сильный рост (Ridge Wallet)
- 40-59: Перспективный (ранняя стадия)
- 20-39: Нишевый (узкая аудитория)
- 0-19: Нет виральности

### Этап 4. Карточка бренда

```
Бренд: [название]
Страна: [происхождение]
Продукт: [что продают]
SKU: [количество]
Категория: [ниша]
Цена: [диапазон]
Virality Score: [0-100]
Выручка (оценка): [если доступно]
TikTok: [просмотры по хэштегу]
Google Trends: [рост %]
Маркетплейсы РФ: [есть/нет]
Конкуренция: [низкая/средняя/высокая]
Почему виральный: [1-2 предложения]
Потенциал в РФ: [оценка]
```

### Этап 5. Выход
- Shortlist 5-10 монобрендов с карточками
- Рейтинг по Virality Score
- Рекомендация: дистрибуция / запуск аналога / контент

---

## Инструменты

### Бесплатные

| Инструмент | Что дает | URL / Доступ |
|------------|----------|--------------|
| TikTok Creative Center | Трендовые хэштеги, продукты, звуки. Фильтр по стране | ads.tiktok.com/business/creativecenter |
| Google Trends | Рост запросов, сравнение брендов, сезонность | trends.google.com (pytrends) |
| YouTube Data API v3 | Просмотры обзоров, динамика, комментарии | Бесплатный API key (Google Cloud) |
| Meta Graph API | Instagram engagement, посты по хэштегу | Бесплатный (Meta Developer) |
| Pinterest Trends | Визуальные тренды по категориям | trends.pinterest.com |
| SocialBlade (free) | Базовая статистика YouTube/TikTok/Instagram | socialblade.com |
| Wildberries API | Каталог, карточки, отзывы, бренды | Открытый content-api |
| DuckDuckGo Search | Веб-поиск по брендам | Скилл duckduckgo-search |
| Kickstarter | Успешные монопродукты | Парсинг (нет API) |
| Product Hunt | Новые продукты, upvotes | GraphQL API (бесплатный) |
| Reddit / X | Упоминания, discussions | SocialData API (есть) |

### Платные

| Инструмент | Что дает | Цена/мес | Приоритет |
|------------|----------|----------|-----------|
| Exploding Topics | Ранние тренды ДО массового рынка | $39 | ВЫСОКИЙ |
| SerpAPI | Google Trends + Shopping программно | $50 | ВЫСОКИЙ |
| MPStats | Аналитика продаж WB/Ozon: выручка, бренды | ~$50 | ВЫСОКИЙ |
| JungleScout | Amazon: продажи, ниши, конкуренция | $49 | СРЕДНИЙ |
| Tokboard / TokStats | TikTok: просмотры, engagement по хэштегам | $15-50 | СРЕДНИЙ |
| SimilarWeb | Трафик сайта, источники, рост | $100+ | НИЗКИЙ |
| BrandWatch / Mention | Мониторинг упоминаний везде | $100+ | НИЗКИЙ |
| SparkToro | Аудитория бренда, каналы | $50 | НИЗКИЙ |

### Минимальный стек (бесплатный)
DuckDuckGo + Google Trends (pytrends) + YouTube Data API + TikTok Creative Center + WB API + Claude

### Рекомендуемый стек ($139/мес)
Все бесплатное + Exploding Topics ($39) + SerpAPI ($50) + MPStats ($50)

---

## Автоматизация

### Google Trends (pytrends)
```python
from pytrends.request import TrendReq
pytrends = TrendReq(hl='ru', tz=180)
pytrends.build_payload(['бренд1', 'бренд2'], timeframe='today 3-m')
data = pytrends.interest_over_time()
```

### Wildberries API
```bash
curl -s "https://search.wb.ru/exactmatch/ru/common/v7/search?query=КАТЕГОРИЯ&resultset=catalog" \
  | jq '.data.products[:20] | .[] | {brand, name, rating, feedbacks}'
```

### YouTube Data API
```bash
curl -s "https://www.googleapis.com/youtube/v3/search?part=snippet&q=БРЕНД+обзор&type=video&order=viewCount&maxResults=10&key=API_KEY"
```

---

## Секреты

| Ключ | Файл | Статус |
|------|------|--------|
| YouTube Data API | ~/.openclaw/.secrets/youtube.env | Нужен ключ |
| SerpAPI | ~/.openclaw/.secrets/serpapi.env | Нужен (платный стек) |
| SocialData API | настроен в системе | Есть |
