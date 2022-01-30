<script>
    import Notecard from "$lib/Notecard.svelte";

    const noteStack = [
        {id: 1, prompt: 'side_a0', answer: 'side_b0'},
        {id: 2, prompt: 'side_a1', answer: 'side_b1'},
    ]
    $: note = noteStack[0]

    function nextSelectCard() {
        let note_index = noteStack.findIndex(n => n.id === note.id)
        let next_index = note_index + 1
        if (next_index > noteStack.length - 1) {
            // cycle around to zero
            next_index = 0
        }
        note = noteStack.at(next_index)
    }
</script>

<div class="over-notecard">
    <Notecard note={note}/>
    <button on:click={() => nextSelectCard()}>Next Card</button>
</div>

<style>
    .over-notecard{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    button {
        margin: 10px;
    }
</style>