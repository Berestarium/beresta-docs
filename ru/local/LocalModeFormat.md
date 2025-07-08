# Формат данных

Результат работы сохраняется в файле .ipynb

## Общая структура

```json
{
  "nbformat": 4,
  "nbformat_minor": 0,
  "cells": [],
  "metadata": {
    "beresta": {
    }
  }
}
```

| Параметр       | Тип           | Описание                                               |
|----------------|---------------|--------------------------------------------------------|
| cells          | array[object] | Список ячеек (code, markdown, raw)                     |
| metadata       | object        | Метаданные ноутбука (структура метаданных дополняется) |
| nbformat       | integer       | Версия формата файла                                   |
| nbformat_minor | integer       | Минорная версия формата файла                          |

## Описание блоков/клеток (`cells`)

Виды:

* markdown
* code

Возможное содержимое блоков и их структура описывается ниже

### Блок markdown

```json
{
  "cell_type": "markdown",
  "id": "e44fea60-4f72-4417-ac2b-1fc69111f5bb",
  "metadata": {},
  "source": [
    "Hello world!"
  ]
}
```

| Параметр  | Тип           | Описание                                            |
|-----------|---------------|-----------------------------------------------------|
| cell_type | string        | Тип ячейки (всегда `"markdown"`)                    |
| id        | uuid          | Уникальный идентификатор ячейки                     |
| metadata  | object        | Метаданные ячейки                                   |
| source    | array[string] | Markdown-текст ячейки (построчно или одной строкой) |

### Блок кода

```json
{
  "cell_type": "code",
  "execution_count": null,
  "id": "a490b25b-f0d1-4a5c-9e30-f57fa9b8a269",
  "metadata": {},
  "outputs": [],
  "source": [
    "println(\"text\")"
  ]
}
```

| Параметр        | Тип           | Описание                                          |
|-----------------|---------------|---------------------------------------------------|
| cell_type       | string        | Тип ячейки (всегда `"code"`)                      |
| execution_count | integer       | Порядковый номер выполнения или null              |
| id              | uuid          | Уникальный идентификатор ячейки                   |
| metadata        | object        | Метаданные ячейки                                 |
| outputs         | array[object] | Результаты выполнения кода                        |
| source          | array[string] | Исходный код ячейки (построчно или одной строкой) |

#### outputs (для code cell)

| Параметр        | Тип           | Описание                                                      |
|-----------------|---------------|---------------------------------------------------------------|
| output_type     | string        | Тип вывода (`"stream"`, `"execute_result"`, `"error"`, и др.) |
| name            | string        | Имя потока (`"stdout"` или `"stderr"`) для `stream`           |
| text            | array[string] | Текстовый вывод для `stream`                                  |
| data            | object        | Данные вывода (например, для изображений, HTML и др.)         |
| execution_count | integer       | Порядковый номер выполнения (для `execute_result`)            |
| ename           | string        | Имя исключения (для `error`)                                  |
| evalue          | string        | Сообщение об ошибке (для `error`)                             |
| traceback       | array[string] | Трассировка стека (для `error`)                               |

*Примечание: В зависимости от типа вывода (`output_type`) присутствуют разные параметры.*

