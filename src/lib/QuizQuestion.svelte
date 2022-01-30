<script>
    import {createEventDispatcher} from "svelte";

    export let selected = 0
    let question = 'question'
    let answers = [{question_id: 0, answer: 'answer_1'}]
    let answer = ''
    let submitted = {question: question, answer: answer}
    export let question_with_answers = {question, answers: answers}

    const dispatch = createEventDispatcher();
    const submit = () => dispatch('submit', submitted);

    function submitAnswer() {
        submitted.question = question_with_answers
        submitted.answer = selected
        submit()
        selected = 0
    }
</script>

<div class="questionCard">
    <form on:submit|preventDefault={submitAnswer}>
        <p class="cardTitle">Question: {question_with_answers.text}</p>
        <div class="answerSection">
            {#each question_with_answers.answers as answer}
                <label>
                    <input type="radio" bind:group={selected} name={selected} value={answer}>
                    {answer.text}</label><br>
            {/each}
        </div>
        <div class="submitButton">
            <button type="submit">Next</button>
        </div>
    </form>
</div>

<style>
    .questionCard {
        border: var(--text-color) solid;
        background: #DDDDDD;
        padding: 20px;
        margin: 20px;
        width: 300px;
    }

    .cardTitle {
        border-bottom: var(--text-color) solid;
        padding: 4px;
        margin-bottom: 5px;
    }

    .answerSection {
        padding: 5px;
    }

    .submitButton {
        margin-top: 10px;
        display: flex;
        justify-content: center;
    }
</style>