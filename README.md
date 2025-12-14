# Practical Assignment 3: Hw-agent

Агент для ответов на вопросы о питательной ценности блюд с использованием LLM и Tool Calling.

## Стек

- **LLM**: Qwen2.5:3b через Ollama (< 4B параметров, open weights)
- **Recipe API**: api-ninjas.com
- **Nutrition API**: calorieninjas.com
- **Framework**: LangChain + LangGraph

## Установка

### 1. Установка Ollama

```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama pull qwen2.5:3b
```

### 2. Установка зависимостей

```bash
pip install -r requirements.txt
```

### 3. Настройка API ключей

Скопируйте `.env.example` в `.env` и заполните ключи:

```bash
cp .env.example .env
```

Получить бесплатные ключи:
- Recipe API: https://api-ninjas.com/
- Nutrition API: https://calorieninjas.com/api

## Запуск

```bash
jupyter notebook hw_agent_nutrition.ipynb
```

Выполнить ячейки последовательно. Результат: `submission_grbn.csv`

## Результат

**Accuracy: 0.74**

## Инструменты

| Tool | Описание |
|------|----------|
| `get_recipe(dish_name)` | Получить рецепт: ингредиенты и порции |
| `get_nutrition(food_query)` | Получить калории и макросы (напр. "100g chicken") |

## Формат вывода

- Калории: kcal
- Белки/Жиры/Углеводы: граммы
- Округление: до 2 знаков после запятой

## Структура проекта

```
.
├── hw_agent_nutrition.ipynb  # Основной ноутбук (LangChain + Qwen2.5:3b)
├── baseline.ipynb            # Baseline решение (Qwen3-4B + transformers)
├── requirements.txt
├── .env.example
├── .env                      # API ключи (gitignored)
├── test.csv                  # Входные вопросы
├── sample.csv                # Формат ответа
└── submission_grbn.csv       # Результат
```
