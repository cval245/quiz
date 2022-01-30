<script>
    import {cloneDeep} from "lodash";
    import QuizQuestion from "$lib/QuizQuestion.svelte";
    import {goto} from "$app/navigation";
    import { quizResults } from "../stores.js"
    export let quiz
    let question = {id: 3, question: 'question null'}
    let answers = [
        {id: 6, question_id: question, answer: 'answer null', correct:false},
        {id: 1, question_id: question, answer: 'answer null two', correct:false},
    ]

    export let questions_with_answers = [
        {
            question,
            answers: answers
        },
    ]
    $: question_with_answers = questions_with_answers[0]
    let selected = 0
    $: selected_arr = []
    let q = {question_id: 0, answer: selected}
    // export const quizResults = writable(selected_arr)

    function submitQuestion(submitted) {
        q = {question: question_with_answers, answer: selected}
        console.log('ff', $quizResults)
        if (!selected_arr.some(x => x.question.id === submitted.detail.question.id)){
            selected_arr.push(cloneDeep(submitted.detail))
            quizResults.set(selected_arr)
        } else {
            selected = selected_arr.find(x => x.question.id === submitted.detail.question.id)
            selected.answer = submitted.detail.answer

            quizResults.set(selected_arr)
        }
        nextQuestion()
    }

    function nextQuestion() {
        let q_index = questions_with_answers.findIndex(q => {
            return q.id === question_with_answers.id
        })
        q_index += 1

        if (q_index >= questions_with_answers.length) {
            goto(`/quiz-${quiz.id}-results`)
            // navigator.
        } else {
            question_with_answers = questions_with_answers.at(q_index)
        }
    }


</script>
<div class="over-question">
    <QuizQuestion question_with_answers={question_with_answers}
                  bind:selected={selected}
                  on:submit={(submitted) => submitQuestion(submitted)}/>
</div>

<style>
    .over-question{
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>