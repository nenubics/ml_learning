---
title: "XGBoost (Extreme Gradient Boosting)"
aliases:
  - XGBoost
  - Extreme Gradient Boosting
  - xgb
tags:
  - ml/algorithms/boosting
  - ml/algorithms/ensembles
  - ml/tools/libraries
  - type/tool
  - difficulty/intermediate
  - status/evergreen
created: 2026-09-14
updated: 2026-09-14
difficulty: 🟡 Средний
related:
  - "[[Градиентный бустинг (Gradient Boosting)]]"
  - "[[Случайный лес (Random Forest)]]"
  - "[[Предобработка данных и Feature Engineering]]"
---

# ⚡ XGBoost (Extreme Gradient Boosting)

> [!abstract] Что такое XGBoost?
> **XGBoost** — высокоэффективная, масштабируемая и оптимизированная библиотека градиентного бустинга над решающими деревьями (GBDT). Именно с помощью XGBoost было выиграно рекордное количество соревнований Kaggle на табличных данных.

---

## 🚀 Почему XGBoost быстрее и точнее обычного бустинга?

1. **Аппроксимация Тейлора 2-го порядка**:
   - Обычный бустинг использует только вектор первых производных (градиенты $g_i = \partial \hat{y} L$).
   - XGBoost использует разложение Тейлора до 2-го порядка, вычисляя и гессианы (вторые производные $h_i = \partial^2 \hat{y} L$):
     $$\mathcal{L}^{(t)} \approx \sum_{i=1}^n \left[ g_i f_t(x_i) + \frac{1}{2} h_i f_t^2(x_i) \right] + \Omega(f_t)$$
2. **Встроенная регуляризация деревьев ($\Omega(f_t)$)**:
   $$\Omega(f_t) = \gamma T + \frac{1}{2} \lambda \sum_{j=1}^T w_j^2 + \alpha \sum_{j=1}^T |w_j|$$
   где $T$ — число листьев, $\gamma$ — штраф за создание нового листа (прунинг), $\lambda$ и $\alpha$ — L2 и L1 регуляризация весов в листьях.
3. **Sparsity-aware Split Finding**:
   - Автоматически обрабатывает пропущенные значения (`NaN`): алгоритм пробует отправлять пропуски влево и вправо и выбирает ветку с максимальным приростом (Gain).
4. **Аппаратные оптимизации**:
   - Блочная структура хранения данных в памяти, поддержка многопоточности (OpenMP), кэш-ориентированный доступ к данным и поддержка обучения на GPU (`tree_method='hist'`).

---

## 🎛️ Ключевые гиперпараметры

| Параметр | Значение по умолчанию | Описание и рекомендации |
| :--- | :---: | :--- |
| `n_estimators` | 100 | Число деревьев в ансамбле. Используйте вместе с `early_stopping_rounds`. |
| `learning_rate` (`eta`) | 0.3 | Темп обучения (рекомендуется уменьшать до `0.01`–`0.1` при увеличении `n_estimators`). |
| `max_depth` | 6 | Максимальная глубина деревьев (обычно 3–8 для предотвращения переобучения). |
| `subsample` | 1.0 | Доля объектов выборки для построения каждого дерева (обычно 0.7–0.9). |
| `colsample_bytree` | 1.0 | Доля признаков при сплитах (аналог Random Forest feature bagging, обычно 0.7–0.8). |
| `gamma` (`min_split_loss`) | 0.0 | Минимальное снижение функции потерь для создания нового листа. |
| `reg_lambda` | 1.0 | L2-регуляризация весов листьев. |

---

## 💻 Базовый пример на Python

```python
import xgboost as xgb
from sklearn.model_selection import train_test_split
from sklearn.metrics import roc_auc_score

# Подготовка DMatrix (внутренний оптимизированный формат XGBoost)
dtrain = xgb.DMatrix(X_train, label=y_train)
dval = xgb.DMatrix(X_val, label=y_val)

params = {
    'objective': 'binary:logistic',
    'eval_metric': 'auc',
    'learning_rate': 0.05,
    'max_depth': 5,
    'tree_method': 'hist'
}

model = xgb.train(
    params,
    dtrain,
    num_boost_round=1000,
    evals=[(dval, 'Validation')],
    early_stopping_rounds=50
)
```

---

## 🔗 Рекомендуемые материалы и статьи

- 📖 [Официальная документация XGBoost](https://xgboost.readthedocs.io/en/latest/)  
  *Полная спецификация API, руководства по тюнингу и бенчмарки.*
- 📄 [XGBoost на Хабре: Практическое руководство](https://habr.com/ru/articles/965382/?ysclid=mijatnczm4857275289)  
  *Подробное практическое руководство по применению и настройке в реальных проектах.*
- 📄 [Разбор алгоритма XGBoost и гиперпараметров — Хабр](https://habr.com/ru/articles/799725/?ysclid=mij8q9ts7o726105710)  
  *Математические основания: оптимизация 2-го порядка, формула Gain и прунинг деревьев.*
- 📄 [Python 3: Примеры и практика работы с XGBoost](https://ru.python-3.com/?p=4566)  
  *Готовые сниппеты кода и сценарии интеграции.*
- 🚀 [[Градиентный бустинг (Gradient Boosting)]] — общая теория бустинга над решающими деревьями.
