<script>
    export let question_result
</script>
<div class="over-question-result">
    <p>{question_result.question.text}</p>
    <ul class="over-answers">
        {#each question_result.question.answers as answer}
            {#if answer.id === question_result.answer.id}
                <li class:correct-not-chosen={answer.correct} class:incorrect={!answer.correct}>
                    {answer.text}
                </li>
            {:else}
                <li class:correct={answer.correct}>
                    {answer.text}
                </li>
            {/if}
        {/each}
    </ul>
</div>
<style>
    li {
        padding: 5px;
        margin: 8px;
    }

    .correct-not-chosen{
        border: solid green;
        color: green;
    }

    .correct {
        /*background: #aaaaaa;*/
        border: dashed green;
        color: green;
    }

    .incorrect {
        border: solid red;
        color: red;
        /*background: #FFdcce;*/
    }

    .over-question-result {
        display: flex;
        flex-direction: column;
        border: solid var(--text-color);
        padding: 20px;
        width: 500px;
    }

    .over-answers {
        padding-left: 20px;
    }
</style>