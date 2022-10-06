# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнила:
- Шупенко Арина Максимовна
- Институт опережающих технологий, major IT, 3 курс
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | # | 20 |
| Задание 3 | # | 20 |

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
Познакомиться с программными средствами для организции
передачи данных между инструментами google, Python и Unity.

## Задание 1
### Реализовать совместную работу и передачу данных в связке Python - Google-Sheets – Unity. 

1. В облачном сервисе google console подключаем API для работы с Google Sheets и Google Drive.

Страница проекта с добавленными "ключами":
![image](https://user-images.githubusercontent.com/114181594/194279588-0d9f1ea6-0d99-4624-b2b6-f96f2e9c9e53.png)


2. Реализовала запись данных из скрипта на python в google-таблицу. Данные описывают изменение темпа инфляции на протяжении 11 отсчётных периодов, с учётом стоимости игрового объекта в каждый период.



```Python
import gspread
import numpy as np
gc=gspread.service_account(filename='unitydatascience-364617-0d68894d132d.json')
sh= gc.open("UnityDataScienseSheets")
price= np.random.randint(2000,10000,11)
mon= list(range(1,11))
i=0
while i<=len(mon):
    i+=1
    if i ==0:
        continue
    else:
        tempInf =((price[i-1]-price[i-2])/price[i-2])*100
        tempInf = str(tempInf)
        tempInf= tempInf.replace('.',',')
        sh.sheet1.update(('A'+str(i)), str(i))
        sh.sheet1.update(('B' + str(i)), str(price[i-1]))
        sh.sheet1.update(('C' + str(i)), str(tempInf))
        print(tempInf)
```

Вот так выглядит таблица:

![image](https://user-images.githubusercontent.com/114181594/194279282-33d7ad3d-94c5-4b95-9b5c-0bee5ab187ca.png)


3. Создать новый проект на Unity, который будет получать данные из google- таблицы, в которую были записаны данные в предыдущем пункте.

4. Написать функционал на Unity, в котором будет воспризводиться аудио- файл в зависимости от значения данных из таблицы.



```C#

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Networking;
using SimpleJSON;

public class NewBehaviourScript : MonoBehaviour
{
    public AudioClip goodSpeak;
    public AudioClip normalSpeak;
    public AudioClip badSpeak;
    private AudioSource selectAudio;
    private Dictionary<string,float> dataSet = new Dictionary<string, float>();
    private bool statusStart = false;
    private int i = 1;

    // Start is called before the first frame update
    void Start()
    {
        StartCoroutine(GoogleSheets());
    }

    // Update is called once per frame
    void Update()
    {
        if (dataSet["Mon_" + i.ToString()] <= 10 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioGood());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }

        if (dataSet["Mon_" + i.ToString()] > 10 & dataSet["Mon_" + i.ToString()] < 100 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioNormal());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }

        if (dataSet["Mon_" + i.ToString()] >= 100 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioBad());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }
    }

    IEnumerator GoogleSheets()
    {
        UnityWebRequest curentResp = UnityWebRequest.Get("https://sheets.googleapis.com/v4/spreadsheets/1-ogpBCBt_nPP0dRAcbIG4NmJRlcLCOvOf5kt7vdd44w/values/Лист1?key=AIzaSyCVRKrvZMq5C6LsQI1RXaHuFFMLtndDS24");
        yield return curentResp.SendWebRequest();
        string rawResp = curentResp.downloadHandler.text;
        var rawJson = JSON.Parse(rawResp);
        foreach (var itemRawJson in rawJson["values"])
        {
            var parseJson = JSON.Parse(itemRawJson.ToString());
            var selectRow = parseJson[0].AsStringList;
            dataSet.Add(("Mon_" + selectRow[0]), float.Parse(selectRow[2]));
        }
    }

    IEnumerator PlaySelectAudioGood()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = goodSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(3);
        statusStart = false;
        i++;
    }
    IEnumerator PlaySelectAudioNormal()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = normalSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(3);
        statusStart = false;
        i++;
    }
    IEnumerator PlaySelectAudioBad()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = badSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(4);
        statusStart = false;
        i++;
    }
}

```

Так это выглядит в Unity, при этом с каждым выводом в консоль появляется звук:

![image](https://user-images.githubusercontent.com/114181594/194281482-dd2b5b94-cb56-4f68-9b1e-13bc6458fd2f.png)





## Задание 2
### Написать программу Hello World в Unity.

Ход работы:
Установить Unity с официального сайта. Установить VS Code. Установить пакеты .NET Framework 4.8 Developer Pack и .NET 6 SDK. В VS Code устанавливаем Unity Tools и
Unity Code Snippets. Создать новый проект в Unity. Соединить программы и вывести Hello Word.



## Задание 3
### Разобрать код. Понять значение переменной Lr и ответить на поставленный вопрос.
Ход работы:

```Python
def model(a, b, x):
  return a*x + b
  
def loss_function(a, b, x, y):
  num = len(x)
  prediction=model(a,b,x)
  return (0.5/num) * (np.square(prediction-y)).sum()
  
loss = loss_function(a, b, x, y)
```



## Вывод
Установила и разобралась в утилитах для работы с Unity. Написала простейшую программу. Объединила VS Code и Unity, установила соответствующие паки. Вывела "Hello World"  в Unity на C# и в Colab на Python. Разобралась в понятии линейной регресии, методе градиентного спуска, а также в из реализации на Python.


| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |
