<script>
    import CourseCard from "$lib/CourseCard.svelte";

    let courses = [
        {
            id: 1,
            course_title: 'title one',
            course_description: 'description one'
        },
        {
            id: 2,
            course_title: 'title two',
            course_description: 'description two'
        },
        {
            id: 3,
            course_title: 'title three',
            course_description: 'description three'
        },
    ]
</script>

<div class="card-stack">
    {#each courses as course}
        <CourseCard course={course}/>
    {/each}
</div>
<style>
    .card-stack {
        display: flex;
        flex-wrap: wrap;
    }
</style>