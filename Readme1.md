Решения алгоритмических задач
📚 Содержание

    Climbing Stairs

    Jump Game II

    Pascal's Triangle II

    Best Time to Buy and Sell Stock

    Best Time to Buy and Sell Stock II

    Теория

🪜 Climbing Stairs
Код решения
python

class Solution:
    def climbStairs(self, n: int) -> int:
        memo = {1: 1, 2: 2}
        def f(n):
            if n in memo:
                return memo[n]
            else:
                memo[n] = f(n-2) + f(n-1)
            return memo[n]
        return f(n)

Методология

Оптимальное решение с мемоизацией (Top-Down Dynamic Programming)

Основная идея: Использует рекурсию с мемоизацией для избежания повторных вычислений. Количество способов подняться на n ступенек равно сумме способов подняться на (n-1) и (n-2) ступенек.

Пошаговая методология:

    Инициализация словаря мемоизации с базовыми случаями

    Рекурсивная функция проверяет наличие результата в кэше

    Вычисление и сохранение новых значений

Сложность:

    Время: O(n)

    Память: O(n)

🦘 Jump Game II
Код решения
python

class Solution:
    def jump(self, nums: List[int]) -> int:
        smallest = 0
        n = len(nums)
        end, far = 0, 0
        for i in range(n-1):
            far = max(far, i + nums[i])
            if i == end:
                smallest += 1
                end = far
        return smallest

Методология

Оптимальное решение с жадным подходом (Greedy Algorithm)

Основная идея: Отслеживает две ключевые точки: end (текущая граница прыжка) и far (максимальная достижимая позиция).

Алгоритм:

    Инициализация счетчиков и границ

    Линейное сканирование с обновлением максимальной достижимой позиции

    Увеличение счетчика прыжков при достижении границы

Сложность:

    Время: O(n)

    Память: O(1)

🔺 Pascal's Triangle II
Код решения
python

class Solution:
    def getRow(self, rowIndex: int) -> list[int]:
        row = [1] * (rowIndex + 1)
        
        for i in range(1, rowIndex):
            row[i] = row[i-1] * (rowIndex - i + 1) // i
        
        return row

Методология

Оптимальное решение с комбинаторным подходом

Основная идея: Использует формулу биномиальных коэффициентов для прямого вычисления строки.

Формула: C(n,k) = C(n,k-1) × (n-k+1) / k

Преимущества:

    Эффективность: O(n)

    Точность: целочисленные вычисления

    Простота реализации

💹 Best Time to Buy and Sell Stock
Код решения
python

class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        min_price = float('inf')
        max_profit = 0
        
        for price in prices:
            profit = price - min_price
            min_price = min(price, min_price)
            max_profit = max(profit, max_profit)
                
        return max_profit

Методология

Однопроходный алгоритм (One-Pass Algorithm)

Основная идея: Отслеживает минимальную цену и вычисляет потенциальную прибыль на каждом шаге.

Ключевые моменты:

    Покупка по минимальной цене

    Расчет прибыли для каждой цены

    Обновление максимальной прибыли

Сложность:

    Время: O(n)

    Память: O(1)

💹 Best Time to Buy and Sell Stock II
Код решения
python

class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        i = 0
        lo = prices[0]
        hi = prices[0]
        profit = 0
        n = len(prices)

        while i < n-1:
            while i < n-1 and prices[i] >= prices[i+1]:
                i += 1
            lo = prices[i]

            while i < n-1 and prices[i] <= prices[i+1]:
                i += 1
            hi = prices[i]
            
            profit += hi - lo
        
        return profit

Методология

Подход "Пики и впадины" (Peak-Valley Approach)

Основная идея: Покупка на локальных минимумах и продажа на локальных максимумах.

Алгоритм:

    Поиск дна (покупка)

    Поиск пика (продажа)

    Суммирование всех прибылей

🧠 Теория
Динамическое программирование

Способ решения сложных задач путём разбиения на более простые подзадачи. Применимо к задачам с оптимальной подструктурой и перекрывающимися подзадачами.

Два подхода:

    Сверху вниз: Рекурсия с мемоизацией

    Снизу вверх: Итеративное заполнение таблицы

Big O нотация

Математическая нотация для анализа сложности алгоритмов.

Основные сложности:

    O(1) - константная

    O(log n) - логарифмическая

    O(n) - линейная

    O(n²) - квадратичная

    O(2ⁿ) - экспоненциальная

Мемоизация

Техника оптимизации, которая сохраняет результаты выполнения функций для предотвращения повторных вычислений в рекурсии.