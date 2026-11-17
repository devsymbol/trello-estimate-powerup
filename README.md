# Trello Estimate Power-Up

Минимальный Power-Up: оценка времени (в часах) на карточке, бейдж на лицевой
стороне карточки и суммарная оценка по доске.

Файлы:
- `connector.html` — точка входа Power-Up, регистрирует капабилити.
- `estimate-form.html` — всплывающая форма ввода/очистки оценки.

## 1. Деплой на GitHub Pages

```bash
cd trello-estimate-powerup
git init
git add .
git commit -m "Initial Trello estimate Power-Up"
git branch -M main
git remote add origin https://github.com/<your-username>/trello-estimate-powerup.git
git push -u origin main
```

Затем в настройках репозитория: Settings → Pages → Source: `main` / `/ (root)`.
Через пару минут файлы будут доступны по адресу вида:
`https://<your-username>.github.io/trello-estimate-powerup/connector.html`

## 2. Регистрация Power-Up в Trello

1. Открыть https://trello.com/power-ups/admin
2. "New" → указать название (например, "Estimate") и Workspace.
3. В разделе "Iframe connector URL" вписать ссылку на `connector.html` с хостинга.
4. Иконка (New/Dark icon) — Trello требует загрузить PNG иконку, без неё
   Power-Up не включится на доске. Можно взять любую 24x24/px (или больше,
   квадратную) картинку для старта.
5. Сохранить.

## 3. Включение на доске

Доска → Power-Ups → Custom Power-Ups → найти "Estimate" → Add.

После этого:
- На лицевой стороне карточки появится бейдж `⏱ Nч`, если оценка задана.
- На развороте карточки — пункт "Оценка времени", по клику открывается форма.
- На самой доске — суммарный бейдж `Σ Nч` по всем карточкам (может не
  обновляться мгновенно — Trello кеширует board-badges).

## Что можно добавить дальше

- Хранить также "факт" (потраченное время) отдельным ключом и показывать
  план/факт в одном бейдже.
- Сортировку/фильтр карточек по оценке (`list-sorters` / `card-sorters` в новых
  версиях API — на момент написания основной способ это ручной расчёт в
  `board-badges`).
- Цветовую индикацию (красный бейдж), если сумма оценок в списке превышает
  лимit.
