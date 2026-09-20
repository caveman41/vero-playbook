# SEO/GEO — шаблон сторінки послуги

Рецепт для створення будь-якої money-сторінки VeroCleaning. Усі числа тут — виміряні на реальному еталоні (`vero-deep-cleaning-CONTENT-MOCKUP.html`), не оцінені на око.

**Читати разом із:** `vero-facts.json` (ціни й факти) · `schema-templates.json` (structured data) · `content-strategy.html` (які сторінки взагалі існують) · `design-system-v3.md` (як це виглядає)

---

## Крок 1 · Визначити, під що сторінка

Перш ніж писати — відповісти на три питання:

| Питання | Де шукати відповідь |
|---|---|
| Який головний запит закриває сторінка? | `search-demand-analysis.html` |
| Чи не дублює вона сусідню сторінку? | `content-strategy.html` §анти-канібалізація |
| Яка ціна «від» для цієї послуги? | `vero-facts.json` §canonical_table_studio_1bath |

⚠ **Якщо на сторінку немає окремого пошукового запиту — сторінки не робимо.** Вона канібалізуватиме сусідні й обидві просядуть.

---

## Крок 2 · Мета-теги

### Title
```
[Послуга] [Місто] · Fixed Price from $[ціна] | VeroCleaning
```
**Ліміт:** 55–60 символів до пайпа. Довше — Google обріже.
**Приклад:** `Deep Cleaning Toronto · Fixed Price from $180 | VeroCleaning`

### Meta description
```
[Що входить, 1 фраза]. [УТП: fixed price / pay after]. [CTA або охоплення].
```
**Ліміт:** 140–155 символів.
**Приклад:** `Vetted, insured cleaners for a full home reset in Toronto and the GTA. See your fixed price in 60 seconds and pay only after the clean.`

### Open Graph
Обов'язково на кожній сторінці. Картинка 1200×630, реальне фото результату.
```html
<meta property="og:title" content="[той самий Title без бренду]">
<meta property="og:description" content="[той самий description]">
<meta property="og:image" content="https://verocleaning.ca/[шлях]">
<meta property="og:url" content="https://verocleaning.ca/[url]">
<meta property="og:type" content="website">
```

---

## Крок 3 · Структура заголовків

**Один H1 на сторінку. Без винятків.**

| Рівень | Формула | Ліміт |
|---|---|---|
| H1 | `[Послуга] [Місто]` | ≤ 30 символів |
| H2 | 4–6 слів, містить послугу або місто | 10 на сторінку |
| H3 | підкатегорії всередині чеклиста | 4 |

⚠ **Кожен H2 має працювати на пошук.** Заголовки на кшталт «Why clients choose us» або «Three simple steps» порожні — у них немає ні послуги, ні міста. Правильно: `Why Toronto homeowners choose us`, `How to book a cleaning in 60 seconds`.

---

## Крок 4 · Зони сторінки

**12 універсальних + 2 умовні.** Порядок не міняти без причини.

| # | Зона | H2 (приклад) |
|---|---|---|
| 1 | Hero | — (H1 + lede + price chip + CTA) |
| 2 | Intro | A full reset for your home |
| 3 | Калькулятор | Build your [service] |
| 4 | Чеклист | Every room, every corner |
| 5 | Before/After | Before & after |
| 6 | Ціноутворення | Priced for heavy-duty work |
| 7 | How it works | How to book in 60 seconds |
| 8 | Why us | Why Toronto homeowners choose us |
| 9 | Service areas | Toronto & the GTA |
| 10 | FAQ | [Service] questions |
| 11 | Related services | Related services |
| 12 | Final CTA | Ready for the reset? |

**Умовні зони — додавати тільки за тригером:**

| Зона | Коли додавати |
|---|---|
| Порівняльна таблиця | Є окремий high-intent запит «X vs Y» у дослідженні попиту |
| Тематичні якорі | Послуга має підтипи, які поки не заслуговують окремих сторінок |

---

## Крок 5 · Ліміти контенту

Ці числа виміряні. Якщо текст не влазить — коротшає текст, не росте блок.

### Hero
| Елемент | Ліміт |
|---|---|
| H1 | ≤ 30 символів |
| Lede | 90–120 символів, одне речення |
| Price chip | ціна + одиниця + одна фраза довіри |

### Чеклист
| Елемент | Ліміт |
|---|---|
| Підкатегорій (H3) | 4 |
| Пунктів усього | 28 |
| Пунктів на підкатегорію | 6–8, нерівномірно — не ділити порівну штучно |
| Довжина пункту | 20–30 символів, дієслово першим |

Приклад пункту: `Detail kitchen cabinets`, `Scrub heavy grease zones`

### FAQ
| Елемент | Ліміт |
|---|---|
| Кількість питань | 7 |
| Довжина питання | 32–56 символів |
| Довжина відповіді | 110–229 символів |

🔴 **Перше речення відповіді має містити число.** Саме такі відповіді цитують ChatGPT, Perplexity і Google AI Overviews. Це головний важіль GEO на всій сторінці.

### Related services
3 картки · 20–32 символи на фразу · іконка + назва + фраза з ціною

### Service areas
20 міст, 4 регіони + Bradford окремо. Повний список — `vero-facts.json §service_areas`.

---

## Крок 6 · Structured data

Набір для money-сторінки:

| Блок | Джерело |
|---|---|
| `Service + Offer` | `schema-templates.json §2` |
| `FAQPage` | `schema-templates.json §3` |
| `BreadcrumbList` | `schema-templates.json §4` |

🔴 **Три жорсткі правила:**
1. `AggregateRating` і `Review` не вставляти — реальних верифікованих відгуків немає, фейкові = ручні санкції Google
2. Ціна в `Offer` збігається з видимою на сторінці до долара
3. Текст FAQ у розмітці дослівно збігається з видимим на сторінці

Перед деплоєм прогнати через `search.google.com/test/rich-results` — нуль помилок.

---

## Крок 7 · Перелінковка

| Правило | Деталі |
|---|---|
| Із головної на сторінку | Картка в блоці Popular services веде на сторінку, **не** на `/book?service=` |
| Зі сторінки на інші | 3 картки Related services |
| Зі сторінки на `/book` | CTA в hero, після калькулятора, у Final CTA |
| Хлібні крихти | Home → [Сторінка], дворівнево |

⚠ **Типова помилка:** усі посилання ведуть у форму бронювання, контентні сторінки не отримують ваги. На головній зараз 28 посилань на `/book` проти 4 на money-сторінки — це перекіс, який варто виправляти.

---

## Крок 8 · GEO-шар

Окремо від звичайного SEO. Мета — потрапити в цитати AI-асистентів.

**Формула абзацу, який цитують:**
```
[Хто] + [що робить] + [де] + [скільки коштує] + [чим відрізняється]
```

**Приклад:**
> VeroCleaning provides deep cleaning in Toronto and the GTA at a fixed price starting at $180 for a studio condo. The full price is shown before booking and payment is taken after the clean.

**Куди ставити:** Intro-зона, перший абзац. Плюс продублювати ключові факти в `sr-only` списку, якщо на сторінці є ротаційний тікер.

**Чого не робити:** ховати текст, якого немає у видимій частині. Прихований шар дублює видиме, не замінює його.

---

## Чек-ліст перед деплоєм

- [ ] Title 55–60 символів, містить послугу + місто + ціну
- [ ] Meta description 140–155 символів
- [ ] Open Graph + картинка 1200×630
- [ ] Один H1, ≤30 символів
- [ ] Кожен H2 містить послугу або місто
- [ ] FAQ: 7 питань, у кожній відповіді число в першому реченні
- [ ] Чеклист: 4 підкатегорії, 28 пунктів
- [ ] Ціни звірені з `vero-facts.json`
- [ ] Schema: Service + FAQPage + BreadcrumbList, без AggregateRating
- [ ] Rich Results Test — нуль помилок
- [ ] Alt-тексти описові, не `image1`
- [ ] Зображення в медіатеці, не base64 в коді
- [ ] 3 Related services ведуть на сторінки, не у форму

---

## Окремі випадки

**`/commercial-cleaning-toronto`** — модель quote-based, фіксованої ціни немає.
Відмінності: блок `Offer` у schema не вставляється · price chip у hero замінюється на «Custom quote» · калькулятор не потрібен · FAQ під B2B-інтент (контракти, після годин, страхування).

**Cost guide (`/cleaning-prices-toronto`)** — інформаційна, не money.
Відмінності: немає `Service + Offer` · головний блок — таблиця цін · опційно `ItemList` у schema · мета — зібрати трафік із запитів «how much does X cost» і вести на money-сторінки.

**Add-ons (`/cleaning-add-ons`)** — каталог SKU.
Відмінності: сітка цін замість чеклиста · опційно `OfferCatalog` · ціни з `vero-facts.json §step_5_extras`.
