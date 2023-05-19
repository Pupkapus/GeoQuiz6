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
<p align = "center">Лабораторная работа №5</p>
<p align = "center">«Вторая activity»</p>
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

<p align = "center" >Упражнение. Лазейка для читера </p>
<p align = "center" >CheatActivity</p>

```kotlin

package com.example.secondapp

import android.app.Activity
import android.content.Context
import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.util.Log
import android.widget.Button
import android.widget.TextView

private const val TAG = "CheatActivity"
private const val KEY_INDEX = "answer"

const val EXTRA_ANSWER_SHOWN = "com.bignerdranch.android.secondapp.answer_shown"
private const val EXTRA_ANSWER_IS_TRUE =
    "com.bignerdranch.android.secondapp.answer_is_true"

class CheatActivity : AppCompatActivity() {

    private lateinit var answerTextView: TextView

    private lateinit var showAnswerButton: Button

    private var answerIsTrue = false

    private var shown = false

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_cheat)

        shown = savedInstanceState?.getBoolean(KEY_INDEX, false) ?: false
        setAnswerShownResult(shown)

        answerIsTrue = intent.getBooleanExtra(EXTRA_ANSWER_IS_TRUE, false)
        answerTextView = findViewById(R.id.answer_text_view)
        showAnswerButton = findViewById(R.id.show_answer_button)
        showAnswerButton.setOnClickListener {
            val answerText = when{
                answerIsTrue -> R.string.true_button
                else -> R.string.false_button
            }
            shown = true
            answerTextView.setText(answerText)
            setAnswerShownResult(shown)
        }
    }

    override fun onSaveInstanceState(savedInstanceState: Bundle) {
        super.onSaveInstanceState(savedInstanceState)
        Log.i(TAG, "onSaveInstanceState")
        savedInstanceState.putBoolean(KEY_INDEX, shown)
    }

    private fun setAnswerShownResult(isAnswerShown: Boolean){
        val data = Intent().apply {
            putExtra(EXTRA_ANSWER_SHOWN, isAnswerShown)
        }

        setResult(Activity.RESULT_OK, data)
    }


    companion object {
        fun newIntent(packageContext: Context, answerIsTrue: Boolean) : Intent {
            return Intent(packageContext, CheatActivity::class.java).apply {
                putExtra(EXTRA_ANSWER_IS_TRUE, answerIsTrue)
            }
        }
    }
}


```

***

<p align = "center" >Упражнение. Отслеживание читов по вопросу  </p>
<p align = "center" >QuizViewModel</p>

```kotlin

package com.example.secondapp

import androidx.lifecycle.ViewModel

class QuizViewModel : ViewModel(){

    private val questionBank = listOf(Questions(R.string.question_australia, true),
        Questions(R.string.question_oceans, true),
        Questions(R.string.question_mideast, false),
        Questions(R.string.question_africa, false),
        Questions(R.string.question_asia, true),
        Questions(R.string.question_america, true)
    )

    var currentIndex = 0

    val isAnswered = IntArray(questionBank.size)

    val isCheated = BooleanArray(questionBank.size)

    val correctAnswer = BooleanArray(questionBank.size)

    val currentQuestionAnswer: Boolean
        get() = questionBank[currentIndex].answer

    val currentQuestionText: Int
        get() = questionBank[currentIndex].textResId

    val currentQuestionSize: Int
        get() = questionBank.size

    fun moveToNext() {
        if(currentIndex == questionBank.size - 1)
        {
            //do nothing
        }
        else {
            currentIndex = (currentIndex + 1) % questionBank.size
        }
    }

    fun moveToPrev() {
        if (currentIndex == 0){
            //do nothing
        }
        else {
            currentIndex = (currentIndex - 1) % questionBank.size
        }
    }

}

```

***

<p align = "center" >Codewars</p>

![Screenshot](https://github.com/Pupkapus/GeoQiuz6/blob/main/cd1.png)

![Screenshot](https://github.com/Pupkapus/GeoQiuz6/blob/main/cd2.png)

![Screenshot](https://github.com/Pupkapus/GeoQiuz6/blob/main/cd3.png)

![Screenshot](https://github.com/Pupkapus/GeoQiuz6/blob/main/cd4.png)

![Screenshot](https://github.com/Pupkapus/GeoQiuz6/blob/main/cd5.png)

![Screenshot](https://github.com/Pupkapus/GeoQiuz6/blob/main/cd6.png)

***
<p align = "center" >ВЫВОД</p>
<p>Подводя итог всему сказанному, могу сделать вывод, что, поработав c kotlin, я узнал многое и применил это на практике, прорешивая задания на Codewars. Все задачи были выполнены.</p>
