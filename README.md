[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Julia](https://img.shields.io/badge/-Julia-%23A270BA?style=flat&logo=julia&logoColor=white)](https://julialang.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Made%20with-Jupyter-orange?logo=Jupyter)](https://jupyter.org/)
[![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)](https://www.linux.org/)
[![Windows](https://img.shields.io/badge/Windows-0078D6?style=flat&logo=windows&logoColor=white)](https://www.microsoft.com/windows)
[![FreeBSD](https://img.shields.io/badge/-FreeBSD-%23870000?style=flat&logo=FreeBSD&logoColor=white)](https://www.freebsd.org/)

# Introduction-to-Julia

### Learn the language basics in this 12-part course

![Julia_mini](https://github.com/user-attachments/assets/539096ea-39a1-4c54-beeb-2625474cf90f)



# **Основы Julia. Слияние Простоты и Мощи** 

### ***🚀 13 Уроков в блокнотах Jupyter***
<br>
<br>
<br>

**Основано на работе Андреаса Ноака Йенсена (MIT & JuliaComputing)**<br>
**С обновлениями, дополнениями и переводом Сергея Соболевского**

<br><br>

### **1️⃣ Julia – революция в вычислениях**

Julia появилась в **2012 году** благодаря **четырём разработчикам**:

- **Джефф Безансон**
  
- **Стефан Карпински**
   
- **Вирал Би Шах**
    
- **Алан Эдельман**
  
<br>

Какова была их цель? - **Создать язык программирования**, который:

- Был бы **таким же лёгким, как Python** 🐍
  
- Работал бы **так же быстро, как C** ⚡
   
- Обладал бы **динамичностью Ruby** 💎
   
- Имел бы **математические возможности MATLAB** 📊
  
- Поддерживал бы **метапрограммирование, как Lisp** 🧠
  
<br>

#### **🔹 Julia = Простота + Скорость + Гибкость**

Julia сочетает **интерпретируемость Python** и **производительность C/Fortran** благодаря **JIT-компиляции через LLVM**.

<br>

📌 **Что делает её мощной?**

1. **JIT-компиляция (Just-In-Time) – высокая скорость выполнения**
   
2. **Гибкость: динамическая и строгая типизация**
     
3. **Множественная диспетчеризация (Multiple Dispatch)**
 
4. **Отличная работа с массивами (Zero-based copy-on-write)**
 
5. **Масштабируемость: от ноутбука до суперкомпьютеров**

6. **Глубокая интеграция с Python, C, R, MATLAB**
  
7. **Машинное обучение (Flux.jl, MLJ.jl, Turing.jl)**

<br>

**Экосистема Julia** содержит более 10 000 пакетов, зарегистрированных в [Общем реестре](https://github.com/JuliaRegistries/General), что означает, что поиск нужного пакета может быть сложной задачей. 

К счастью, существуют сервисы, которые могут помочь ориентироваться в экосистеме, в том числе:

- [JuliaHub](https://juliahub.com/ui/Packages) — a [JuliaHub](https://juliahub.com/) service that includes search of all registered open source package documentation, code search, and navigation by tags/keywords.

- [Julia Packages](https://juliapackages.com/) — просматривайте пакеты Julia, фильтруйте по категориям и сортируйте их по популярности, дате создания или последнего обновления. Также поддерживается просмотр пакетов разработчиков.

- [Julia.jl](https://github.com/svaksha/Julia.jl) — систематизация пакетов Julia, созданная вручную (информация о категориях для JuliaPackages также является производной от этой).
  
  
<br

---

<br>

### **2️⃣ JIT-компиляция: Julia быстрее Python**

Julia использует **JIT-компиляцию через LLVM**, что позволяет выполнять код **сопоставимо с C/Fortran**.

#### **📌 Сравнение скорости выполнения (Python vs Julia)**

```python
#  Цикл в Python
import time
def sum_python(n):
    s = 0
    for i in range(n):
        s += i
    return s

start = time.time()
sum_python(10**7)
print("Python time:", time.time() - start)
```

```julia
# Julia быстрый JIT-компилированный код
function sum_julia(n)
    s = 0
    for i in 1:n
        s += i
    end
    return s
end

@time sum_julia(10^7)  # JIT-компиляция + выполнение
@time sum_julia(10^7)  # Только выполнение (в разы быстрее)
```

✅ **Julia гораздо быстрее, чем Python!** 🏎💨

---

<br>

### **3️⃣ Машинное обучение в Julia**

Julia **активно развивается в области машинного обучения**, предоставляя мощные библиотеки для **нейронных сетей, вероятностных моделей и AutoML**.

#### **📌 Основные библиотеки для ML в Julia**
| **Библиотека** | **Описание** |
|--------------|-------------|
| **Flux.jl** | Глубокое обучение (аналог PyTorch) |
| **MLJ.jl** | Классическое ML (аналог Scikit-Learn) |
| **Turing.jl** | Байесовские модели и вероятностное программирование |
| **Zygote.jl** | Автоматическое дифференцирование |
| **DataFrames.jl** | Работа с табличными данными (аналог pandas) |
| **CUDA.jl** | Запуск нейросетей на GPU (аналог TensorFlow GPU) |

---

<br>

## **4️⃣ Глубокое обучение в Julia с Flux.jl**
Flux.jl – **главная библиотека для нейросетей в Julia**.  
Поддерживает **глубокие нейросети, сверточные сети, рекуррентные сети и трансформеры**.

#### **🔹 Пример: Создание нейросети**
```julia
using Flux

# Определяем модель
model = Chain(
    Dense(28*28, 128, relu),
    Dense(128, 64, relu),
    Dense(64, 10),
    softmax
)

# Функция потерь
loss(x, y) = Flux.Losses.crossentropy(model(x), y)

# Оптимизатор Adam
opt = ADAM(0.001)

# Тренировка
Flux.train!(loss, params(model), [(rand(28*28), rand(10))], opt)
```
✅ **Flux.jl похож на PyTorch, но намного проще!**

---

<br>

### **5️⃣ Julia против Python для машинного обучения**
| **Фактор** | **Julia** | **Python** |
|------------|-----------|------------|
| **Скорость** | 🏎 Почти как C | 🐢 Медленный (интерпретируемый) |
| **JIT-компиляция** | ✅ Есть (LLVM) | ❌ Нет (только Numba) |
| **Глубокое обучение** | Flux.jl, MLJ.jl | PyTorch, TensorFlow |
| **Масштабируемость** | ✅ Отличная (GPU, распределённые вычисления) | ⚠️ Ограниченная (GIL) |
| **Совместимость** | ✅ Вызов C/Python/R | ✅ Совместим с C, R |
| **Множественная диспетчеризация** | ✅ Да | ❌ Нет |

💡 **Выводы**:  
Julia быстрее, легче, мощнее, но Python пока более популярен.

---

<br>

### **6️⃣ AutoML и Probabilistic ML в Julia**
#### **📌 MLJ.jl: Альтернатива Scikit-Learn**
MLJ.jl – мощная библиотека для **классического машинного обучения**.
```julia
using MLJ

# Загружаем датасет
data, schema = @load_iris

# Разделение на train/test
train, test = partition(eachindex(data.species), 0.7)

# Выбираем модель (RandomForest)
DecisionTree = @load DecisionTreeClassifier pkg=DecisionTree

model = DecisionTree(max_depth=3)

# Создаем машину обучения
mach = machine(model, select(data, Not(:species)), data.species)

# Обучаем модель
fit!(mach, rows=train)

# Делаем предсказания
y_pred = predict(mach, rows=test)
```
✅ **MLJ.jl – аналог Scikit-Learn, но мощнее и быстрее.**

---

<br>

### **7️⃣ GPU-ускорение в Julia**
Julia **поддерживает CUDA прямо из коробки**.  

📌 Для работы на GPU используйте `CUDA.jl`:
```julia
using CUDA

# Создаём массив на GPU
X = cu(rand(1000, 1000))

# Ускоряем вычисления на GPU
Y = X .^ 2
```
✅ **Julia может ускорять матричные операции в 100 раз!**

---

<br>

### **8️⃣ Julia в индустрии машинного обучения**

Julia активно используется в **исследовательских центрах и компаниях**:
- **NASA** – моделирование космических аппаратов  
- **MIT** – анализ больших данных  
- **BlackRock** – финансовые модели  

---

<br>

#### **🎯 Подведём итог:**
🔹 **Julia объединяет простоту Python и скорость C**  
🔹 **Flux.jl – мощный инструмент для глубокого обучения**  
🔹 **MLJ.jl – альтернатива Scikit-Learn в Julia**  
🔹 **Julia работает на GPU и суперкомпьютерах**  
🔹 **Будущее машинного обучения за Julia!**  

💡 **Julia – это язык будущего для AI, ML и High-Performance Computing!** 🚀

&nbsp;
