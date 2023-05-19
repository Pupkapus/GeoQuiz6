<p align = "center">МИНИСТЕРСТВО НАУКИ И ВЫСШЕГО ОБРАЗОВАНИЯ
РОССИЙСКОЙ ФЕДЕРАЦИИ
ФЕДЕРАЛЬНОЕ ГОСУДАРСТВЕННОЕ БЮДЖЕТНОЕ
ОБРАЗОВАТЕЛЬНОЕ УЧРЕЖДЕНИЕ ВЫСШЕГО ОБРАЗОВАНИЯ
«САХАЛИНСКИЙ ГОСУДАРСТВЕННЫЙ УНИВЕРСИТЕТ»</p>
<br>
<p align = "center">Институт естественных наук и техносферной безопасности</p>
<p align = "center">Кафедра информатики</p>
<p align = "center">Пак Никита Витальевич</p>
<br>
<p align = "center">Лабораторная работа №6</p>
<p align = "center">«Версии Android SDK и совместимость»</p>
<p align = "center">01.03.02 Прикладная математика и информатика</p>




<br>
<p align = "right" >Научный руководитель</p>
<p align = "right" >Соболев Евгений Игоревич</p>
<p align = "center" >Южно-Сахалинск</p>
<p align = "center" >2023 г.</p>
<p align = "center" ><b>ВВЕДЕНИЕ</b></p>
<p>Kotlin (Ко́тлин) — статически типизированный, объектно-ориентированный язык программирования, работающий поверх Java Virtual Machine и разрабатываемый компанией JetBrains. Также компилируется в JavaScript и в исполняемый код ряда платформ через инфраструктуру LLVM. Язык назван в честь острова Котлин в Финском заливе, на котором расположен город Кронштадт</p>
<p>Авторы ставили целью создать язык более лаконичный и типобезопасный, чем Java, и более простой, чем Scala. Следствием упрощения по сравнению со Scala стали также более быстрая компиляция и лучшая поддержка языка в IDE. Язык полностью совместим с Java, что позволяет Java-разработчикам постепенно перейти к его использованию; в частности, язык также встраивается Android, что позволяет для существующего Android-приложения внедрять новые функции на Kotlin без переписывания приложения целиком.</p>
<p align = "center" >РЕШЕНИЕ ЗАДАЧ</p>

<p align = "center" >Упражнение. Вывод версии Android на устройстве</p>
<p align = "center" >MainActivity</p>
<p>добавил пару строк для отображения API в TextView</p>
```kotlin
    private lateinit var cheatInfo: TextView
```

```kotlin
    apiView = findViewById(R.id.api_string)
    ...
    apiView.setText("API level " + android.os.Build.VERSION.SDK_INT.toString())
```

***

<p align = "center" >Упражнение. Ограничение подсказок </p>
<p align = "center" >MainActivity</p>

```kotlin
private fun checkCheatTries(){

        var counting = 0

        for (i in quizViewModel.isCheated){
            if(i){
                counting++
            }
        }

        if(quizViewModel.allTries - counting <= 0){
            cheatButton.isEnabled = false
        }

        cheatInfo.text = "Попыток осталось " +  (quizViewModel.allTries - counting).toString() + "/3"

    }

```

***

<p align = "center" >Codewars</p>

![Screenshot](https://github.com/Pupkapus/GeoQuiz6/blob/main/cd1.png)

![Screenshot](https://github.com/Pupkapus/GeoQuiz6/blob/main/cd2.png)

![Screenshot](https://github.com/Pupkapus/GeoQuiz6/blob/main/cd3.png)

![Screenshot](https://github.com/Pupkapus/GeoQuiz6/blob/main/cd4.png)

![Screenshot](https://github.com/Pupkapus/GeoQuiz6/blob/main/cd5.png)

![Screenshot](https://github.com/Pupkapus/GeoQuiz6/blob/main/cd6.png)

***
<p align = "center" >ВЫВОД</p>
<p>Подводя итог всему сказанному, могу сделать вывод, что, поработав c kotlin, я узнал многое и применил это на практике, прорешивая задания на Codewars. Все задачи были выполнены.</p>
