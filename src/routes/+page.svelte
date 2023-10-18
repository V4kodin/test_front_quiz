<script>
    import "../app.css";

    const questions = [
        {
            question: 'Какая столица России?',
            options: ['Москва', 'Санкт-Петербург', 'Киев', 'Минск'],
            correctAnswer: 'Москва',
            img: './1.jpg',
        },
        {
            question: 'Сколько планет в Солнечной системе?',
            options: ['8', '9', '10', '7'],
            correctAnswer: '8',
        },
        {
            question: 'Какой химический символ у железа?',
            options: ['Fe', 'Ir', 'Au', 'Ag'],
            correctAnswer: 'Fe',
        },
        {
            question: 'Какой год начала Первой мировой войны?',
            options: ['1914', '1918', '1939', '1905'],
            correctAnswer: '1914',
        },
        {
            question: 'Что представляет собой формула H2O?',
            options: ['Вода', 'Углекислый газ', 'Соль', 'Аммиак'],
            correctAnswer: 'Вода',
        },
        {
            question: 'Какой самый большой материк на Земле?',
            options: ['Азия', 'Африка', 'Европа', 'Северная Америка'],
            correctAnswer: 'Азия',
        },
        {
            question: 'Кто написал "Войну и мир"?',
            options: ['Лев Толстой', 'Федор Достоевский', 'Антон Чехов', 'Иван Тургенев'],
            correctAnswer: 'Лев Толстой',
        },
        {
            question: 'Какое химическое вещество в атмосфере Земли защищает от ультрафиолетового излучения?',
            options: ['Озон', 'Кислород', 'Углекислый газ', 'Азот'],
            correctAnswer: 'Озон',
        },
        {
            question: 'Какое животное считается символом Австралии?',
            options: ['Кенгуру', 'Коала', 'Дельфин', 'Пингвин'],
            correctAnswer: 'Кенгуру',
        },
        {
            question: 'Какая планета названа в честь богини красоты и любви?',
            options: ['Венера', 'Марс', 'Юпитер', 'Сатурн'],
            correctAnswer: 'Венера',
        },
    ];
    let index = 0;
    let score = 0;
    let answer = '';
    const questionsCount = questions.length;
    let showResult = false;

    function nextQuestion(event) {
        const clickedtText = event.target.textContent
        if (clickedtText === questions[index].correctAnswer) {
            score++
        } else {
            score--
        }
        index++;
        if (index >= questionsCount) {
            showResult = true;
        }
    }
</script>
<div class="bg-gray-800 text-white flex flex-col items-center justify-center min-h-[calc(100dvh)] max-w-[calc(100dvw)]">
    {#if !showResult}
        <p class="text-4xl mb-4 text-center font-bold font">
            {questions[index].question}
        </p>
        <div class="mb-4">
            <img width="600" src='{questions[index].img}' class="rounded-2xl">
        </div>
        <div class="flex justify-between grid grid-cols-2 gap-4 w-10/12 lg:w-1/2">
            {#each questions[index].options as option}

                <div class="w-full text-sky-700">
                    <button on:click={nextQuestion}
                            class="text-center items-center bg-pink-200 p-4 rounded-2xl w-full text-2xl">
                        {option}
                    </button>
                </div>
            {/each}
        </div>
        <p class="text-2xl mt-4">
            Ваш счет: {score}
        </p>
    {:else}
        <p class="text-6xl mt-4">
            Ваш итоговый счет: {score}
        </p>
    {/if}
</div>
