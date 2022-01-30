<script lang="ts">
    let showCardBack = false;
    export let course = {id: 0, course_title: 'Course Title', course_description: 'Course Description'}

    function flipCard() {
        showCardBack = !showCardBack
    }

</script>
<div class="course-card" on:click={() => flipCard()}>
    <p class="course-card-title">{course.course_title}</p>
    <div class="course-card-image">image</div>
    <div class="course-card-description">
        <p>{course.course_description}</p>
    </div>
    <div class="course-card-actions">
        <a class="button" sveltekit:prefetch href="/chapter-{course.course_title}">Open</a>
    </div>
</div>
<style>
    .course-card {
        margin: 10px;
        width: 400px;
        border: solid var(--text-color);
    }

    .course-card-title {
        height: 40px;
        margin: 20px;
        font-size: 20px;
        padding-left: 10px;
        padding-right: 10px;
        border-bottom: solid var(--text-color);
        display: flex;
        align-items: center;
    }

    .course-card-description, .course-card-actions {
        margin: 20px;
        height: 20px;
        font-size: 20px;
        padding: 10px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .course-card-description{
        border-bottom: solid var(--text-color);
    }

    .course-card-image {
        height: 200px;
        margin: 20px;
        font-size: 20px;
        padding-left: 10px;
        padding-right: 10px;
        background:#DDDDDD;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>