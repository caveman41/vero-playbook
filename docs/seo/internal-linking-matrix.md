# Внутрішня перелінковка — матриця

Хто на кого посилається. На 20 сторінках перелінковка розповзається без таблиці: одні сторінки збирають усю вагу, інші лишаються сиротами.

**Читати разом із:** `keyword-map.md` · `content-strategy.html` §10

---

## Принцип

Головна — найсильніша сторінка сайту. Її вага передається вглиб **одним стрибком**, не двома. Тому money-сторінки отримують посилання з головної напряму, без проміжних хабів.

---

## 🔴 Поточна проблема: перекіс у бік форми

Виміряно на макеті головної:

| Ціль | Кількість посилань |
|---|---|
| `/book` | **28** |
| `/deep-cleaning-toronto` | 4 |
| решта money-сторінок | 0 |

Головна зливає майже всю вагу у форму бронювання, а контентні сторінки не отримують нічого. Форма не ранжується в пошуку — це тупик для SEO-ваги.

**Виправлення:** картки в блоці Popular services ведуть на **сторінки послуг**, а не на `/book?service=`. Кнопка бронювання лишається на самих money-сторінках, де вона в контексті.

---

## Матриця

### Головна (`/`)

| Куди | Звідки саме | Анкор |
|---|---|---|
| `/deep-cleaning-toronto` | картка Popular services | `Deep Cleaning` |
| `/regular-cleaning-toronto` | картка Popular services | `Regular Cleaning` |
| `/move-out-cleaning-toronto` | картка Popular services | `Move-In / Out` |
| `/post-renovation-cleaning` | картка Popular services | `Post-Renovation Cleaning` |
| `/carpet-cleaning-toronto` | картка Popular services | `Carpet Cleaning` |
| `/cleaning-prices-toronto` | FAQ «how much does it cost» | `See full pricing` |
| `/commercial-cleaning-toronto` | перемикач у хедері | `For business` |
| `/cleaning-add-ons` | каталог послуг | `Add-ons` |
| `/book` | hero CTA, sticky bar, final CTA | `Get my price` |

⚠ **Каталог 32 послуг** на головній — кожна назва потенційне посилання. Ті, що мають сторінку, ведуть на неї. Ті, що ні, ведуть на якір усередині `/cleaning-add-ons`.

### Money-сторінка послуги

| Куди | Звідки | Скільки |
|---|---|---|
| `/book` | hero, після калькулятора, final CTA | 3 |
| 3 суміжні послуги | блок Related services | 3 |
| `/cleaning-prices-toronto` | зона ціноутворення | 1 |
| `/` | хлібні крихти | 1 |

**Related services — не випадкові.** Правило: сусід по scope або по методу.

| Сторінка | Related services |
|---|---|
| `/deep-cleaning-toronto` | Regular · Move-Out · Carpet |
| `/regular-cleaning-toronto` | Deep · Condo · Add-ons |
| `/move-out-cleaning-toronto` | Deep · Post-Renovation · Appliance |
| `/post-renovation-cleaning` | Deep · Move-Out · Carpet |
| `/carpet-cleaning-toronto` | Rug · Upholstery якір · Deep |
| `/condo-cleaning-toronto` | Regular · Deep · Airbnb |
| `/house-cleaning-toronto` | Deep · Regular · Post-Renovation |
| `/airbnb-cleaning-toronto` | Regular · Move-Out · Linen якір |

### Cost guide (`/cleaning-prices-toronto`)

Це **розподільник трафіку**. Збирає інформаційні запити й веде на money-сторінки.

| Куди | Звідки |
|---|---|
| усі 4 основні типи прибирання | таблиця цін, кожен рядок — посилання |
| `/cleaning-add-ons` | секція extras |
| `/book` | final CTA, один раз |

⚠ Не перевантажувати CTA на `/book` — сторінка інформаційна, її завдання передати вагу далі, а не конвертувати напряму.

### Commercial (`/commercial-cleaning-toronto`)

| Куди | Звідки |
|---|---|
| `/office-cleaning-toronto` | картка типу приміщення |
| `/janitorial-cleaning-toronto` | картка типу приміщення |
| `/healthcare-cleaning-toronto` | картка типу приміщення |
| `/retail-cleaning-toronto` | картка типу приміщення |
| `/` | перемикач у хедері |

🔴 **Commercial не посилається на `/book`** — residential-калькулятор не обслуговує комерційні обсяги.

### Add-ons (`/cleaning-add-ons`)

| Куди | Звідки |
|---|---|
| `/deep-cleaning-toronto` | «більшість add-ons входять у Deep» |
| `/carpet-cleaning-toronto` | секція carpet |
| `/book` | кожен SKU-блок |

---

## Правила анкорів

| Правило | Приклад |
|---|---|
| Анкор містить запит цільової сторінки | `Deep Cleaning Toronto`, не `дізнатись більше` |
| Анкор ≠ запит іншої сторінки | не ставити `house cleaning toronto` на посилання, що веде не на головну |
| Не більше 2 однакових анкорів на одній сторінці | інакше виглядає як спам |
| Хлібні крихти — завжди `Home` | не `Головна`, не `VeroCleaning` |

---

## Сторінки-сироти — перевірка

Сторінка-сирота = на неї не веде жодне внутрішнє посилання. Google такі сторінки індексує погано або не індексує взагалі.

**Перевірка після кожного релізу:** кожна опублікована сторінка має щонайменше **2 вхідні посилання** з різних сторінок.

| Сторінка | Мінімум вхідних |
|---|---|
| money-сторінки ядра | головна + 2 Related з інших money |
| cost guide | головна + усі money-сторінки |
| commercial підсторінки | commercial-хаб + суміжні |
| add-ons | головна + money-сторінки |

---

## Чого не робити

| Антипатерн | Чому |
|---|---|
| Усі посилання на `/book` | Форма не ранжується, вага в тупику |
| Посилання «дізнатись більше» | Анкор без ключа не передає сигналу |
| Перехресне посилання всіх на всіх | Розмиває сигнал, виглядає штучно |
| Посилання на якір замість сторінки, коли сторінка є | Якір не ранжується окремо |
| Футер із 20 посиланнями на всі сторінки | Наскрізні футер-посилання знецінені Google |
