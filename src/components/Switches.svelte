<script>
    import toggle from '../assets/switch.svg';
    import {createEventDispatcher} from "svelte";

    export let knobSelection = 'do';
    export let options;

    export let resetClasses;

    function handleClick(e) {
        resetClasses();
        e.target.classList.add('flipped')
        dispatch('select', {
            id:e.target.id
        });
    }
    const dispatch = createEventDispatcher();
</script>
<h1> YEAH LET'S {knobSelection.toUpperCase()} SOME SHIT</h1>
{#if knobSelection !== 'do'}
<div class="switches">
    {#each options as switchName}
        <div style="width: 200px; text-align: center;">
            <img alt="a switch" id="{switchName}" on:click={handleClick} src="{toggle}"/>
            <p>{switchName}</p>
        </div>
    {/each}
</div>
{/if}


<style>
    .switches {
        display: flex;
        flex-direction: row;
        gap: 10px;
    }

    img {
        width: 50px;
    }

    p {
        font-weight: 900;
    }

</style>