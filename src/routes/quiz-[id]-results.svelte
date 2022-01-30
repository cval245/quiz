<script>
    import {page} from "$app/stores";
    import QuizResult from "$lib/QuizResult.svelte";
    import {quizResults} from "../stores.js";
    let id = $page.params.id
</script>
<QuizResult quizResults={$quizResults}/>
