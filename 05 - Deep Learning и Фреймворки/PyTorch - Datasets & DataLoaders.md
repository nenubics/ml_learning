---
title: "PyTorch - Datasets & DataLoaders"
aliases:
  - PyTorch Datasets
  - PyTorch DataLoaders
  - torch.utils.data
  - PyTorch Data Tutorial
tags:
  - ml/frameworks/pytorch
  - ml/deep-learning
  - ml/data
  - type/tutorial
  - difficulty/intermediate
  - status/evergreen
created: 2026-09-14
updated: 2026-09-14
difficulty: 🟡 Средний
related:
  - "[[Предобработка данных и Feature Engineering]]"
  - "[[Градиентный спуск (Gradient Descent)]]"
---

# 🔥 PyTorch: Datasets & DataLoaders

> [!abstract] Архитектурная идея
> В PyTorch код загрузки и предобработки данных намеренно отделен от кода обучения модели (`model`, `optimizer`, `loss`).
> - `Dataset` хранит образцы и соответствующие им метки.
> - `DataLoader` оборачивает `Dataset` в итерируемый объект для батчинга, многопоточной загрузки, перемешивания и передачи в GPU.

---

## 📦 Создание кастомного Dataset

Для создания собственного датасета необходимо унаследоваться от `torch.utils.data.Dataset` и переопределить ровно **три метода**:
1. `__init__`: инициализация путей к файлам, чтение метаданных, сохранение трансформаций.
2. `__len__`: возвращает общее количество объектов в датасете.
3. `__getitem__`: загружает и возвращает один конкретный объект и метку по индексу `idx`.

```python
import os
import pandas as pd
import torch
from torch.utils.data import Dataset
from torchvision.io import read_image

class CustomImageDataset(Dataset):
    def __init__(self, annotations_file, img_dir, transform=None, target_transform=None):
        self.img_labels = pd.read_csv(annotations_file)
        self.img_dir = img_dir
        self.transform = transform
        self.target_transform = target_transform

    def __len__(self):
        return len(self.img_labels)

    def __getitem__(self, idx):
        img_path = os.path.join(self.img_dir, self.img_labels.iloc[idx, 0])
        image = read_image(img_path)
        label = self.img_labels.iloc[idx, 1]

        if self.transform:
            image = self.transform(image)
        if self.target_transform:
            label = self.target_transform(label)

        return image, label
```

---

## ⚡ Подготовка DataLoader для обучения

```python
from torch.utils.data import DataLoader

train_dataset = CustomImageDataset('annotations.csv', 'images_dir/')

train_dataloader = DataLoader(
    dataset=train_dataset,
    batch_size=64,         # Размер мини-батча для Mini-batch GD
    shuffle=True,          # Перемешивание на каждой эпохе
    num_workers=4,         # Количество параллельных процессов CPU для загрузки
    pin_memory=True        # Быстрая перекладка данных в память GPU
)

# Итерация в цикле обучения (Training Loop)
for batch_idx, (features, labels) in enumerate(train_dataloader):
    features = features.cuda(non_blocking=True)
    labels = labels.cuda(non_blocking=True)
    
    # Прямой проход, расчет Loss, шаг оптимизатора...
```

---

## 💡 Полезные параметры DataLoader

- `collate_fn`: функция для кастомного объединения списка отдельных сэмплов в батч (незаменима в NLP и Audio, когда последовательности разной длины и нужен паддинг).
- `drop_last=True`: отбрасывает последний неполный батч, если размер датасета не делится нацело на `batch_size` (актуально для BatchNorm).

---

## 🔗 Рекомендуемые материалы

- 📖 [Официальное руководство PyTorch: Datasets & DataLoaders Tutorial](https://docs.pytorch.org/tutorials/beginner/basics/data_tutorial.html)  
  *Официальный интерактивный туториал с примерами работы с Fashion-MNIST и готовыми трансформациями torchvision.*
- 🧹 [[Предобработка данных и Feature Engineering]] — методы масштабирования и предобработки входных данных.
- 📉 [[Градиентный спуск (Gradient Descent)]] — почему данные подаются батчами (Mini-batch SGD).
