<script>
    import {onMount} from "svelte";
    import {page} from '$app/stores';
    import Quiz from "$lib/Quiz.svelte";
    let id = $page.params.id
    let question = {id: 3, question: 'question null'}
    let answers = [
        {id: 6, question_id: question, answer: 'answer null'},
        {id: 1, question_id: question, answer: 'answer null two'},
    ]
    let quiz = {id: 0,
        name: '',
        questions:[{question, answers: answers}]}
    onMount(async function () {
        fetch("http://localhost:8080/quiz/" + id)
            .then(response => response.json())
            .then(data => quiz = data)
    })
    let submitted;
</script>
submitted = {submitted}
{#if quiz}
    <Quiz on:submit={submitted}
          quiz={quiz}
            questions_with_answers={quiz.questions}/>
{/if}
