<script>
    import {onMount} from "svelte";

    var quizzes = []
    onMount(async function () {
        fetch("http://localhost:8080/quiz/")
            .then(response => response.json())
            .then(data => quizzes = data)
    })
</script>
<div class="quiz-list">
    <h1>Quizzes</h1>
    <ul>
        {#each quizzes as quiz}
            <li>
                <a sveltekit:prefetch href="/quiz-{quiz.id}">{quiz.name}</a>
            </li>
        {/each}
    </ul>
</div>
<style>
    .quiz-list {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .quiz-list ul li {
        padding-bottom: 10px;
    }
</style>