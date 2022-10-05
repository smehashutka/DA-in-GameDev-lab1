# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнила:
- Шупенко Арина Максимовна
- Институт опережающих технологий, major IT, 3 курс
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Задание 1
### Написать программы Hello World на Python
Ход работы:

Скачать и установить дистриутив Python Anaconda. Запустить Jupiter Notebook. В открывшейся файловой системе создать новую папку. Создать в папке файл с кодом, который вывод "Hello Word".

Устанавливаем Anaconda:
![image](https://user-images.githubusercontent.com/114181594/192881977-f974bda2-c055-46b8-9c6b-b8a916b94814.png)


Создаем новую папку на диске:
![image](https://user-images.githubusercontent.com/114181594/192881822-17cc64b8-90ae-440d-8274-0de18686607f.png)


Пишем код и выводим результат:
![image](https://user-images.githubusercontent.com/114181594/192881644-6f47700d-ecc2-423e-8fe9-01f62ca6d4b9.png)

## Вывод
Установила и разобралась в утилитах для работы с Python. Написала простейшую программу.


## Задание 2
### Написать программу Hello World в Unity.

Ход работы:
Установить Unity с официального сайта. Установить VS Code. Установить пакеты .NET Framework 4.8 Developer Pack и .NET 6 SDK. В VS Code устанавливаем Unity Tools и
Unity Code Snippets. Создать новый проект в Unity. Соединить программы и вывести Hello Word.


Устанавливаем VS Code:

![image](https://user-images.githubusercontent.com/114181594/192887248-28316023-0461-43a2-b5b4-38ec3e8b0587.png)

Утснавливаем два дополнительных пакета:

![image](https://user-images.githubusercontent.com/114181594/193766620-a4010e52-a7b8-4ce5-87f9-af63869f8517.png)

Добавляем необходимые extinsions в VS Code:

![image](https://user-images.githubusercontent.com/114181594/193766850-e032499f-3bcc-4246-aad2-12ccd31693c7.png)
![image](https://user-images.githubusercontent.com/114181594/193766970-f91c7b8e-4c28-4f69-b182-f8c10e3cf7cd.png)



Создаем новый проект в Unity:
![image](https://user-images.githubusercontent.com/114181594/192885859-fe4f1e76-288f-4af5-b896-2720f482f85b.png)

Соединяем:
![image](https://user-images.githubusercontent.com/114181594/192887565-1a7277f2-7455-4dd7-9f28-1713f9fb29c8.png)


# Выводим "Hello World" на Python в Google Colab.


![image](https://user-images.githubusercontent.com/114181594/193768166-2decac03-8700-4226-8655-08679890c25f.png)

Файл с кодом сохранен на личном диске:

![image](https://user-images.githubusercontent.com/114181594/193768800-10c31129-9cf3-4aaf-bed7-61d9a7754930.png)

# Выводим "Hello World" в Unity.

В проекте Unity создаем папку Scripts и создаем в ней новый скрипт:

![image](https://user-images.githubusercontent.com/114181594/193769269-d9bc4cb5-66b5-42c8-81b2-a388e0d3731d.png)
![image](https://user-images.githubusercontent.com/114181594/193769654-6923c4de-1c74-497a-a465-3bb4c66a1a88.png)

Код в скрипте:

![image](https://user-images.githubusercontent.com/114181594/193777154-1bedcfa0-7374-47c5-abc8-d8bc52982616.png)


Привязываем скрипт к объекту CubeTest и запускам программу с кодом:

![image](https://user-images.githubusercontent.com/114181594/193781793-f6b66076-7154-44ce-a2ba-82661505cb0a.png)



## Задание 3
### Разобрать код. Понять значение переменной Lr и ответить на поставленный вопрос.

Разберемся с кодом:

Импортируем необходиые библиотеки, упаковываем обучающие данные в массивы. Выводи график с точками на коорд. плоскости.

![image](https://user-images.githubusercontent.com/114181594/194025567-adad74f2-bc03-48fb-8b4b-df94df3a4042.png)

Определяем функции.

![image](https://user-images.githubusercontent.com/114181594/194026306-9484b177-8636-4735-913f-f12756000424.png)


Инициализируем начальные данные - длину шага и коэффициенты.

![image](https://user-images.githubusercontent.com/114181594/194026498-952d23e6-00de-4542-bab9-eb5dd81574b9.png)


Начинаем обучение.

![image](https://user-images.githubusercontent.com/114181594/194026603-77ca9ba8-f519-4580-9e17-08dea18a953a.png)

В итоге получаем график: 

![image](https://user-images.githubusercontent.com/114181594/194026682-38a94eca-a850-4218-82dc-8202329aef33.png)

1) Должна ли величина loss стремиться к нулю при изменении исходных данных? 
Есоли под исходными данными понимать значения, которые входят в функцию loss, то да - будет стремится.
Поскольку величина loss представляет из себя среднеквадратичную ошибку, которая считается как усреднение всех значений ошибки (разности y предсказанного и y фактического) в квадрате - то с каждой итерацией разность будет стремится к нулу, за счет более подобранных значений а и b, которые приближают y предсказанное к y фактическому.

```Python
def model(a, b, x):
  return a*x + b
  
def loss_function(a, b, x, y):
  num = len(x)
  prediction=model(a,b,x)
  return (0.5/num) * (np.square(prediction-y)).sum()
  
loss = loss_function(a, b, x, y)
```


2)Какова роль параметра Lr?
Параметр Lr - это коэффициент скорости (шага обучения). Он влияет на то, как сильно будут меняться коэффциенты в ту или иную сторону (сторона определяется за счет знаков производной da и db).
Это отражено в этой части кода:
![image](https://user-images.githubusercontent.com/114181594/194027472-17cb3a27-e060-46f2-aa92-d6536edef7fa.png)

Исходное значение параметра Lr = 0.00001 - что является тостаточно маленьким шагом, это говорит о необходимости огромного количества итераций.
График в таком случае выглядит так - 

![image](https://user-images.githubusercontent.com/114181594/194030158-7b74351e-a157-4031-8be8-52415bdf3d38.png)

Если задать шаг, например,  Lr=0.003, то график становится более реалистичным, итераций на подбор коэффициентов нужно меньше.
![image](https://user-images.githubusercontent.com/114181594/194026682-38a94eca-a850-4218-82dc-8202329aef33.png)


## Вывод
Установила и разобралась в утилитах для работы с Unity. Написала простейшую программу. Объединила VS Code и Unity, установила соответствующие паки. Вывела "Hello World"  в Unity на C# и в Colab на Python. Разобралась в понятии линейной регресии, методе градиентного спуска, а также в из реалезации на Python.


| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |
