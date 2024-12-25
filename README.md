# Object Validation

## Автор

- Дяченко Данііл
- Група ІО-25

## Опис проєкту

Цей проєкт демонструє реалізацію системи валідації полів об’єктів у Java з використанням кастомних анотацій та рефлексії.

-- Валідація полів об'єкта за критеріями, заданими через анотації (наприклад, перевірка на null, обмеження довжини рядків або діапазон чисел).
-- Автоматичне визначення типів полів і перевірка їх відповідності анотаціям. У разі помилкової конфігурації (наприклад, застосування анотації для рядка до числового поля) система видає відповідну помилку.
-- Проєкт порівнює продуктивність валідації через рефлексію та без неї.

## Основні класи

### `NotNull`

Анотація для перевірки, що поле не має бути `null`.

### `StringLength`

Анотація для перевірки довжини String. Приймає параметри:

- `min` — мінімальна довжина рядка (за замовчуванням `0`).
- `max` — максимальна довжина рядка (за замовчуванням `Integer.MAX_VALUE`).

### `MaxValue`

Анотація для перевірки, що значення числового поля не перевищує певного максимуму. Приймає параметр:

- `value` — максимальне значення.

### `MinValue`

Анотація для перевірки, що значення числового поля не менше певного мінімуму. Приймає параметр:

- `value` — мінімальне значення.

### `Validator`

Клас, що реалізує валідацію об'єктів через рефлексію. Перевіряє всі анотації, застосовані до полів об'єкта, і викликає відповідні методи валідації.

### Демонстраційні класи

1. **`Gamer`**  
   Поля:
    - `username`(тип: String, перевірка на null).
    - `age`(тип: int, перевірка на мінімальне значення 12 та максимальне значення 100).

2. **`Item`**  
   Поля:
    - `title`(тип: String, перевірка на null).
    - `description` (тип: String, перевірка на довжину від 3 до 100 символів).

3. **`Plane`** (без рефлексії)  
   Поля:
    - `model` (тип: String, перевірка на null та на довжину від 3 до 25 символів).
    - `year`(тип: int, перевірка на діапазон від 1970 до 2024 років).

## Продуктивність

Вимірюється час виконання для обох варіантів валідації (через рефлексію та без неї) і порівнюється, щоб показати накладні витрати на продуктивність при використанні рефлексії.

## Очікувані результати

Використання рефлексії для валідації має серйозні накладні витрати на продуктивність у порівнянні з традиційною статичною валідацією (як у класі Plane), де перевірка полів здійснюється без використання рефлексії.
Проєкт демонструє різницю в часі виконання між валідацією через рефлексію та без неї.

# Як запустити проект

1. Клонувати репозиторій:
   ```bash
   git clone https://github.com/Daniil-Dyachenko/JavaAdvancedSoftwareLab1
   
2. Перейти в директорію проекту у кореневу папку
3. Виконати команди Maven для збірки проекту:
   ```bash
   mvn clean install
   mvn dependency:resolve
4. Запустити головний клас Main вручну через IDE, або виконати команду:
   ```bash
   mvn exec:java -Dexec.mainClass="org.example.Main"