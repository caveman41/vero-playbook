VeroCleaning, дизайн-система v3.0. База — design-system.html від замовника (07.09), знято з робочого прототипу. Це не пропозиція, це обмеження.

ТОКЕНИ
ink #000500 · muted #4E5C50 · emerald #00B34F · emerald-press #009B44
sand #F8F4EA · sand-deep #E4DFD3 · white #FFFFFF · mint #E4F6E6 · line #DDD6C7
on-dark: body #FFFFFF · mute rgba(255,255,255,.65) · price var(--emerald)
tints: sky #E3F3FD · mint #E4F6E6 · rose #FCE8E9 · butter #FBF5DC
radius: .5rem / .75rem / 1rem / pill 9999px
motion: 140ms cubic-bezier(.4,0,.2,1)

РОЛІ КОЛЬОРУ
emerald       = заливка великих форм: кнопки, лого, плашки. Ніколи текст.
emerald-press = hover/active стан кнопки. Теж заливка, теж не текст.
ink           = увесь текст, включно з текстом на зеленій кнопці (не білий)
muted         = вторинний текст, підписи, eyebrow
mint          = підкладка іконок, бейджі, м'яка підсвітка
sand          = фон сторінки і полів вводу
sand-deep     = заливки: акцентні картки і смуги всередині білих секцій
white         = картки, шапка, білі секції
line          = будь-яка межа

ТИПОГРАФІКА
Nunito 500 — h1, h2, h3. Nunito 700 — рідкісні акценти, не за замовчуванням.
Inter 400 — увесь текст. Inter 500 — інтерфейс і всі цифри (tabular-nums).

h2 моб      2.125rem / 1.12 / -.028em
h2 ≥1024    3rem     / 1.1  / -.032em
lede        1.1875rem / 1.5 / muted / max-width 524px
sub         1rem / 1.5 / muted / max-width 52ch
body        1rem / 1.5 / ink
eyebrow     .6875rem / .11em / uppercase / muted
fine        .75rem / muted

Одна зв'язка правило: цифри — завжди Inter 500, ніколи Nunito. Більше нюансів немає.

СІТКА Й ВІДСТУПИ
Контейнер 75rem, центрується.
Full-bleed смуга: width:100vw; margin-left/right:calc(50% - 50vw).
Секція моб 4rem 1.25rem · секція ≥1024 6rem 2.5rem.
Заголовок → підзаголовок 1rem. Підзаголовок → контент 2.5rem.
Біла смуга завжди з border-top і border-bottom у line.

КНОПКИ
Пігулка: padding .5rem 1rem, min-height 2.5rem, нижче 768 — 2.75rem, pill radius.
primary = emerald / ink-текст · hover = emerald-press · secondary = прозорий, inset 1px ink.
scale(.98) на :active.

ГОТОВИЙ CSS — вставляти першим блоком, нічого кольором не хардкодити

:root{
  --ink:#000500; --muted:#4E5C50;
  --emerald:#00B34F; --emerald-press:#009B44;
  --sand:#F8F4EA; --sand-deep:#E4DFD3; --white:#FFFFFF;
  --mint:#E4F6E6; --line:#DDD6C7;
  --on-dark-body:#FFFFFF; --on-dark-mute:rgba(255,255,255,.65); --on-dark-price:var(--emerald);
  --t-sky:#E3F3FD; --t-mint:#E4F6E6; --t-rose:#FCE8E9; --t-butter:#FBF5DC;
  --r-sm:.5rem; --r-md:.75rem; --r-lg:1rem; --pill:9999px;
}
body{font-family:'Inter',system-ui,-apple-system,sans-serif;font-weight:400;
 background:var(--sand);color:var(--ink);line-height:1.5;-webkit-font-smoothing:antialiased}
h1,h2,h3{font-family:'Nunito',system-ui,sans-serif;font-weight:500;letter-spacing:-.028em;
 line-height:1.12;text-wrap:balance}
h2{font-size:2.125rem;margin-bottom:1rem}
@media(min-width:1024px){h2{font-size:3rem;line-height:1.1;letter-spacing:-.032em}}
.page{max-width:75rem;margin:0 auto}
section.band{padding:4rem 1.25rem;width:100vw;margin-left:calc(50% - 50vw);margin-right:calc(50% - 50vw)}
@media(min-width:1024px){section.band{padding:6rem 2.5rem}}
.band.white{background:var(--white);border-top:1px solid var(--line);border-bottom:1px solid var(--line)}
.pill{display:inline-flex;align-items:center;justify-content:center;font-family:inherit;
 font-size:1rem;font-weight:500;line-height:1;padding:.5rem 1rem;min-height:2.5rem;
 border-radius:var(--pill);border:0;cursor:pointer;letter-spacing:-.01em;text-decoration:none;
 transition:background 140ms cubic-bezier(.4,0,.2,1)}
@media(max-width:767px){.pill{min-height:2.75rem}}
.p-primary{background:var(--emerald);color:var(--ink)}
.p-primary:hover{background:var(--emerald-press)}
.p-secondary{background:transparent;color:var(--ink);box-shadow:inset 0 0 0 1px var(--ink)}

Підключення шрифтів, у <head> до решти CSS:
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500&family=Nunito:wght@500;700&display=swap">

ПЛАСКО
Нуль тіней. Нуль градієнтів. Глибина = hairline-бордер + шар фону.
Виняток один: хедер сайту з backdrop-filter.
Іконки: пласкі, суцільна заливка. У картках послуг допустимі емодзі —
так задано в компоненті .svc замовника, більше не заборонено.

ЛЕЙАУТ
Брейкпоінти 768 і 1024.
Один кольоровий шар за раз: або кольорова смуга з білими картками,
або біла смуга з кольоровими картками. Ніколи обидва.
Виняток, свідомий: тайли калькулятора — біла картка, кольорові тайли.

ЛІМІТИ КОПІРАЙТУ — це верстка, а не тон
H1 4–6 слів · H2 4–6 слів · Lede max-width 34ch
Тіло method-картки 70 символів · тіло тайла калькулятора 40 символів
Eyebrow 2–4 слова · кнопка 1–3 слова · бейдж 2–4 слова
Якщо текст обрізається — коротшає текст, не росте картка.

ЩО ВИДАЄ AI-ЗГЕНЕРОВАНУ СТОРІНКУ — уникати
– eyebrow → H2 → підзаголовок на кожній секції. Максимум 60% секцій.
– метрономна симетрія: завжди 4 переваги, завжди 3 кроки
– абзаци однакової довжини

АУДИТОРІЯ
Торонто і GTA, багато кому 45+. 90% трафіку — телефон.
390px — основний вигляд. Десктоп — похідний.
Контраст: основний текст ≥4.5:1, вторинний ≥7:1, стан ≥3:1.
Тап-таргети нижче 768 ≥2.75rem.

ОДНА АУДИТОРІЯ
Ця ітерація — тільки Residential. Комерційні варіанти не проєктуються.
