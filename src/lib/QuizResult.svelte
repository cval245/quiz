<script>
    import {onMount} from "svelte";
    import QuizQuestionResult from "$lib/QuizQuestionResult.svelte";

    export let quizResults
    onMount(() => {
        calcPercentCorrect()
    })

    function calcPercentCorrect() {
        let correctResults = quizResults.filter(x => x.answer.correct)
        percent_correct = correctResults.length / quizResults.length * 100
    }

    let percent_correct;
    let review_answers = false;

    function toggleReview() {
        review_answers = !review_answers
    }
</script>
<div class="over-results">
    <h1>Results</h1>
    {#if percent_correct >= 80}
        <p>You Passed!!</p>
    {:else}
        <p>You Failed</p>
    {/if}
    <p>Percent correct: {percent_correct}%</p>
    <button on:click={() => toggleReview()}>Review Questions</button>
</div>
{#if review_answers}
    {#each quizResults as result}
        <div class="quiz-questions">
            <QuizQuestionResult question_result={result}/>
        </div>
    {/each}
{/if}
<style>

    .quiz-questions {
        display: flex;
        justify-content: center;
        margin: 10px;
    }

    button {
        border: solid var(--text-color);
        padding: 5px 15px;
        border-radius: 25px;
    }

    button:hover {
        color: #eeeeee;
        background: var(--text-color);
        border: solid var(--text-color);
    }

    .over-results {
        display: flex;
        flex-direction: column;
        align-items: center;
        border: solid;
        border-color: var(--text-color);
        padding: 30px;
        margin-bottom: 5px;
    }
</style>