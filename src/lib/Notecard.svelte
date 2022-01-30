<script lang="ts">

    let showCardBack = false;
    export let note = {id: 0, prompt: 'side_a', answer: 'side_b'}

    function flipCard() {
        showCardBack = !showCardBack
    }


</script>

<div class="notecard" on:click={() => flipCard()}>
    <div class="notecard-inner" class:flip-it={showCardBack}>
        <div class="notecard-front">
            <p>{note.prompt}</p>
        </div>
        <div class="notecard-back" class:conceal-answer={showCardBack}>
            <p>{note.answer}</p>
        </div>
    </div>
</div>

<style>
    .notecard {
        height: 200px;
        width: 400px;
    }

    .notecard-inner {
        position: relative;
        width: 100%;
        height: 100%;
        text-align: center;
        transition: transform 0.8s;
        transform-style: preserve-3d;
    }

    /* Do an horizontal flip on button click */
    .flip-it {
        transform: rotateY(180deg);
    }


    /* Position the front and back side */
    .notecard-front, .notecard-back {
        position: absolute;
        width: 100%;
        height: 100%;
        backface-visibility: hidden;
        box-shadow: -1px 1px 3px black;
    }

    /* Style the front side (fallback if image is missing) */
    .notecard-front {
        background-color: #DDDDDD;
        color: black;
    }

    /* Style the back side */
    .notecard-back {
        background-color: #CCCCCC;
        color: white;
        transform: rotateY(180deg);
    }

    .conceal-answer {
        animation: revealTextSlowly .3s forwards;
    }
    @keyframes revealTextSlowly {
        to { color: white }
    }
</style>