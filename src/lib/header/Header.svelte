<script>
    import {page} from "$app/stores";
</script>
<svelte:head>
    <title>Patent Title</title>
</svelte:head>
<header>
    <nav>
        <ul>
            <li class:active={$page.url.pathname === '/'}>
                <a class:active={$page.url.pathname === '/'}
                   sveltekit:prefetch href="/"><p>Home</p></a>
            </li>
            <li class:active={$page.url.pathname === '/course'}>
                <a class:active={$page.url.pathname === '/course'}
                        sveltekit:prefetch href="/course"><p>Course</p></a>
            </li>
            <li class:active={$page.url.pathname === '/quizzes'}>
                <a class:active={$page.url.pathname === '/quizzes'}
                        sveltekit:prefetch href="/quizzes"><p>Quizzes</p></a>
            </li>
            <li class:active={$page.url.pathname === '/flashcards'}>
                <a class:active={$page.url.pathname === '/flashcards'}
                        sveltekit:prefetch href="/flashcards"><p>Flashcards</p></a>
            </li>
        </ul>
    </nav>
</header>
<style>
    header {
        display: flex;
        justify-content: center;
    }
    nav {
        display: flex;
        justify-content: center;
        --background: var(--primary-color);
        /*--background: rgba(255, 255, 255, 0.7);*/
    }
    nav a p:hover {
        border-bottom: solid;
        padding: 1em 1em 0.7em;
    }
    nav a {
        display: flex;
        height: 100%;
        align-items: center;
        color: var(--heading-color);
        font-weight: 700;
        font-size: 0.8rem;
        text-transform: uppercase;
        letter-spacing: 0.1em;
        transition: color 0.2s linear;
        padding: 0 1em;
    }
    nav a p {
        display: flex;
        height: 30%;
        align-items: center;
        color: var(--heading-color);
        font-weight: 700;
        font-size: 0.8rem;
        text-transform: uppercase;
        letter-spacing: 0.1em;
        transition: color 0.2s linear;
        padding: 5px 1em 5px;
    }
    path {
        fill: var(--background);
    }

    ul {
        position: relative;
        padding: 0;
        margin: 0;
        height: 3em;
        display: flex;
        justify-content: center;
        align-items: center;
        list-style: none;
        background: var(--background);
        background-size: contain;
    }

    li {
        position: relative;
        height: 100%;
    }

    a.active p{
        border-bottom: solid;
        padding: 1em 1em 0.7em;
        /*text-underline: #111111;*/
        /*text-decoration: underline;*/
    }

    li.active::before {
        /*text-underline: #111111;*/
        /*text-decoration: underline;*/
        /*--size: 6px;*/
        /*content: '';*/
        /*width: 0;*/
        /*height: 0;*/
        /*position: absolute;*/
        /*top: 0;*/
        /*left: calc(50% - var(--size));*/
        /*border: var(--size) solid transparent;*/
        /*border-top: var(--size) solid var(--accent-color);*/
    }
</style>