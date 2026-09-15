# 🧠 Machine Learning Knowledge Base (Obsidian Vault)

<p align="center">
  <img src="https://img.shields.io/badge/Obsidian-Vault-7C3AED?style=for-the-badge&logo=obsidian&logoColor=white" alt="Obsidian Vault" />
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-Learn" />
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch" />
  <img src="https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white" alt="TensorFlow" />
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas" />
  <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" alt="NumPy" />
  <img src="https://img.shields.io/badge/XGBoost-15B998?style=for-the-badge" alt="XGBoost" />
  <img src="https://img.shields.io/badge/Status-Active%20Vault-success?style=for-the-badge" alt="Status" />
</p>

---

## 🌟 О репозитории

Этот репозиторий представляет собой современную персональную базу знаний (**Second Brain / PKM**) по **Машинному обучению (Machine Learning)**, **Глубокому обучению (Deep Learning)** и **Инженерии данных (Data Engineering)**, оформленную в стандартах **Obsidian**.

Каждая заметка снабжена строгим **YAML-фронтматтером**, **иерархическими тегами**, краткими теоретическими конспектами, математическими формулами в формате **KaTeX**, интерактивными коллаутами и перекрестными вики-ссылками (`[[...]]`) для построения графа знаний.

---

## 🧭 Архитектура хранилища

```text
ml_learning/
├── README.md                                 # Главный хаб и витрина репозитория
├── .obsidian/                                # Пресет настроек для мгновенного открытия в Obsidian
├── 00 - MOC (Карты знаний)/
│   ├── 00.00 - Главный Индекс ML.md           # Master Map of Content с логикой изучения
│   └── 00.01 - Навигатор по Тегам.md          # Полная таксономия и матрица тегов
├── 01 - Математика и Оптимизация/
│   ├── Градиент функции (Function Gradient).md # Частные производные, геометрический смысл
│   └── Градиентный спуск (Gradient Descent).md # GD, SGD, Mini-batch, Learning Rate
├── 02 - Классический ML/
│   ├── Линейная регрессия (Linear Regression).md # МНК, регуляризация L1/L2
│   ├── Все алгоритмы ML за 17 минут (Overview).md # Сравнительная матрица и обзор методов
│   └── Scikit-learn - Каталог моделей и шпаргалка по выбору.md # 18 моделей с типами данных и примерами
├── 03 - Ансамбли и Бустинги/
│   ├── Случайный лес (Random Forest).md       # Бэггинг, метод случайных подпространств, OOB
│   ├── Градиентный бустинг (Gradient Boosting).md # Последовательное обучение на остатки
│   └── XGBoost.md                             # Оптимизация 2-го порядка, гессианы, прунинг
├── 04 - Предобработка данных/
│   └── Предобработка данных и Feature Engineering.md # Imputation, Encoding, Scaling, признаки
├── 05 - Deep Learning и Фреймворки/
│   └── PyTorch - Datasets & DataLoaders.md    # torch.utils.data, батчинг, многопоточность
├── 06 - Курсы и Сообщества/
│   ├── ZTM - Complete Machine Learning & Data Science Bootcamp (Daniel Bourke).md # Практический буткемп (16 модулей)
│   ├── Вкатываемся в Machine Learning с нуля за 0 рублей (Roadmap).md # Пошаговый гайд с Хабра
│   ├── Курс Машинного Обучения ФКН ВШЭ (Евгений Соколов).md # Золотой академический стандарт
│   ├── girafe-ai.md                           # Открытые курсы от экспертов МФТИ/ВШЭ/ШАД
│   └── Deep Machine Learning (deepmachinelearning.ru).md # Интерактивная база знаний
└── 99 - Архив/
    ├── ml_learning_original.txt              # Исходный список ссылок (для сохранения истории)
    └── ztm_course_notes_original.txt         # Исходный конспект курса Daniel Bourke
```

---

## 🗺️ Карта знаний и Быстрый старт

| Раздел | Тема / Заметка | Ключевые теги | Сложность | Описание |
| :--- | :--- | :--- | :---: | :--- |
| **00. Навигация** | [Главный Индекс ML](00%20-%20MOC%20(Карты%20знаний)/00.00%20-%20Главный%20Индекс%20ML.md) | `#moc` `#ml/overview` | — | Центральная карта связей хранилища |
| **00. Теги** | [Навигатор по Тегам](00%20-%20MOC%20(Карты%20знаний)/00.01%20-%20Навигатор%20по%20Тегам.md) | `#moc` `#meta` | — | Иерархическое дерево всех тегов |
| **01. Математика** | [Градиент функции](01%20-%20Математика%20и%20Оптимизация/Градиент%20функции%20(Function%20Gradient).md) | `#ml/math` | 🟢 Easy | Вектор частных производных и геометрия |
| **01. Оптимизация** | [Градиентный спуск](01%20-%20Математика%20и%20Оптимизация/Градиентный%20спуск%20(Gradient%20Descent).md) | `#ml/optimization` | 🟢 Easy | Сходимость, GD, SGD, Mini-batch, темп $\eta$ |
| **02. Линейные модели** | [Линейная регрессия](02%20-%20Классический%20ML/Линейная%20регрессия%20(Linear%20Regression).md) | `#ml/algorithms/regression` | 🟢 Easy | Обычный МНК, Lasso, Ridge, ElasticNet |
| **02. Обзор алгоритмов** | [Все алгоритмы ML](02%20-%20Классический%20ML/Все%20алгоритмы%20ML%20за%2017%20минут%20(Overview).md) | `#ml/algorithms/classical` | 🟢 Easy | Парадигмы Supervised/Unsupervised, сравнение |
| **02. Каталог моделей** | [Каталог моделей Scikit-learn](02%20-%20Классический%20ML/Scikit-learn%20-%20Каталог%20моделей%20и%20шпаргалка%20по%20выбору.md) | `#ml/frameworks/sklearn` `#ml/cheatsheet` | 🟢 Easy | 18 моделей классификации и регрессии с типами данных |
| **03. Ансамбли** | [Случайный лес](03%20-%20Ансамбли%20и%20Бустинги/Случайный%20лес%20(Random%20Forest).md) | `#ml/algorithms/ensembles` | 🟡 Medium | Бэггинг деревьев, уменьшение дисперсии |
| **03. Бустинг** | [Градиентный бустинг](03%20-%20Ансамбли%20и%20Бустинги/Градиентный%20бустинг%20(Gradient%20Boosting).md) | `#ml/algorithms/boosting` | 🟡 Medium | Последовательное обучение на остатки ошибки |
| **03. SOTA Библиотеки** | [XGBoost](03%20-%20Ансамбли%20и%20Бустинги/XGBoost.md) | `#ml/algorithms/boosting` | 🟡 Medium | Гессианы, оптимизация второго порядка, GPU |
| **04. Данные** | [Предобработка данных](04%20-%20Предобработка%20данных/Предобработка%20данных%20и%20Feature%20Engineering.md) | `#ml/preprocessing` | 🟢 Easy | Пропуски, Scaling, One-Hot/Target Encoding |
| **05. Фреймворки** | [PyTorch Datasets](05%20-%20Deep%20Learning%20и%20Фреймворки/PyTorch%20-%20Datasets%20&%20DataLoaders.md) | `#ml/frameworks/pytorch` | 🟡 Medium | Потоковая загрузка, батчинг, пайплайн |
| **06. Буткемп ZTM** | [ZTM ML Bootcamp (Daniel Bourke)](06%20-%20Курсы%20и%20Сообщества/ZTM%20-%20Complete%20Machine%20Learning%20&%20Data%20Science%20Bootcamp%20(Daniel%20Bourke).md) | `#ml/resources/bootcamp` `#ml/frameworks/sklearn` | 🟢 Easy | 16 модулей: NumPy, Pandas, Sklearn, Milestone Projects, DE, TF |
| **06. Роадмапы** | [Вкат в ML с нуля](06%20-%20Курсы%20и%20Сообщества/Вкатываемся%20в%20Machine%20Learning%20с%20нуля%20за%200%20рублей%20(Roadmap).md) | `#ml/resources/roadmap` | 🟢 Easy | Бесплатные курсы: Stepik, 3b1b, ODS, Kaggle |
| **06. Курсы ВШЭ** | [Курс ML ФКН ВШЭ](06%20-%20Курсы%20и%20Сообщества/Курс%20Машинного%20Обучения%20ФКН%20ВШЭ%20(Евгений%20Соколов).md) | `#ml/resources/courses` | 🟡 Medium | Фундаментальный университетский курс |
| **06. Сообщества** | [girafe-ai](06%20-%20Курсы%20и%20Сообщества/girafe-ai.md) | `#ml/resources/community` | 🟡 Medium | Открытые материалы МФТИ, ВШЭ, ШАД |
| **06. Порталы** | [Deep Machine Learning](06%20-%20Курсы%20и%20Сообщества/Deep%20Machine%20Learning%20(deepmachinelearning.ru).md) | `#ml/resources/knowledge-base` | 🟢 Easy | Интерактивные статьи и треки по DL |

---

## 💻 Как открыть хранилище в Obsidian

1. Склонируйте репозиторий:
   ```bash
   git clone https://github.com/nenubics/ml_learning.git
   ```
2. Откройте приложение **Obsidian**.
3. Нажмите **Open folder as vault** (Открыть папку как хранилище) и выберите склонированную папку `ml_learning`.
4. Включите режим **Graph view** (`Ctrl/Cmd + G`) для просмотра интерактивного графа связей между алгоритмами, математикой и фреймворками!

### Рекомендуемые плагины Obsidian:
- **Dataview**: для генерации динамических таблиц по тегам (`tag:#ml/algorithms/boosting`).
- **Omnisearch**: полнотекстовый мгновенный поиск по конспектам и формулам.
- **Excalidraw**: визуальные схемы и зарисовки архитектур нейросетей прямо внутри заметок.

---

## 🏷️ Стандарт структуры заметки

Каждая заметка в хранилище придерживается единого формата:

```yaml
---
title: "Название темы"
aliases: ["Синоним 1", "Аббревиатура"]
tags:
  - ml/category/subcategory
  - type/concept
  - difficulty/beginner
  - status/evergreen
created: 2026-09-14
updated: 2026-09-15
difficulty: 🟢 Начальный
related:
  - "[[Связанная заметка 1]]"
---
```

---

## 🤝 Вклад в развитие базы (Contributing)

Если вы хотите дополнить базу новыми заметками, алгоритмами или полезными материалами:
1. Создайте ветку (`git checkout -b feature/new-topic`).
2. Добавьте заметку в соответствующую категорию с YAML-фронтматтером и тегами.
3. Добавьте ссылку на новую заметку в `00.00 - Главный Индекс ML.md`.
4. Сделайте Pull Request!
