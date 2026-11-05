# Keepsake — landing

Адаптивний односторінковий лендінг дизайн-агенції **Keepsake** (лабораторна робота №7, завдання 4).

**Демо:** https://lxerkdy.github.io/landing-keepsake/

## Технології

- HTML5 (семантика: `header`, `nav`, `main`, `section`, `article`, `figure`, `footer`, `form`), один `h1`
- CSS3: Flexbox для розкладки, CSS Grid лише для сітки портфоліо, CSS-змінні в `:root`
- Без JavaScript, без фреймворків і UI-бібліотек
- Шрифти Oswald (300/400/700), Open Sans (300/400/700), Dancing Script 700 — локально у WOFF2, `font-display: swap`
- Зображення у WebP із `width`/`height` і `loading="lazy"` (крім першого екрана)
- Іконки — інлайн-SVG (спрайт `<symbol>` + `<use>`)

## Адаптивність

Mobile first: базові стилі для 320–767, далі `@media (min-width: 768px)` і `@media (min-width: 1280px)`.
Контейнер: `max-width: 1100px` + бокові поля 20 / 40 / 90 px. Горизонтального скролу немає від 320 до 1920 px.

## Рішення

| Задача | Як зроблено |
|---|---|
| Мобільне меню без JS | `<button popovertarget>` + `<nav popover>`; бургер перетворюється на хрестик через `body:has(:popover-open)`. Атрибут `aria-expanded` браузер виставляє сам для popover-кнопки, `aria-controls` вказано явно |
| Фільтр портфоліо | Приховані `input[type=radio]` + `:checked ~ .works__grid .card:not([data-category="…"])` |
| «Load more works» | Приховане `input[type=checkbox]` + `:checked ~`; на mobile/tablet показує карточки, що не вмістилися (5 / 8 з 9) |
| Ховер карточки | Оверлей через `opacity`; той самий стан для `:focus-visible` і `:focus-within` |
| Форма підписки | Нативна валідація (`required`, `type=email`, `pattern`), стан error через `:user-invalid`, success через `:target` (`action="#subscribed"`) |
| Fixed header | `position: fixed`, тінь при прокручуванні через `animation-timeline: scroll()` (де підтримується) |
| Кнопка «вгору» | `position: fixed`, 44×44, завжди видима |

## Структура

```
landing-keepsake/
├── index.html
├── css/        reset.css, fonts.css, style.css
├── images/     WebP карточок і прев'ю журналу
└── fonts/      WOFF2
```

## Запуск

Відкрити `index.html` у браузері (збірка не потрібна).
