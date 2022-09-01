<script>
    import { createEventDispatcher } from 'svelte';

    import knob from '../assets/knob.svg'
    import plate from '../assets/plate.svg'
    let rotation = 0;
    let selection = '';

    function select() {
        dispatch('select', {
            selection
        });
    }

    const dispatch = createEventDispatcher();

    function handleClick(event){
        let x = event.offsetX;
        let y = event.offsetY;
        console.log(`${x}, ${y}`)
        if(x < 123 && y > 70) {
            rotation = '-90'
            selection = 'assault';
        } else
        if(x < 123 && y <= 70) {
            rotation = '-27'
            selection = 'amaze';
        } else
        if(x > 123 && y <= 70) {
            rotation = '27'
            selection = 'annoy';
        } else
        if(x > 123 && y > 70) {
            rotation = '90'
            selection = 'amplify';
        } else {
            rotation = '0'
            selection = '';
        }
        select();
    }

</script>


<div class="ui">
    <div on:click={handleClick} class="plate">
        <div class="knob" style="transform: rotate({rotation}deg);"></div>
    </div>
</div>

<style>
    .ui {
    }

    .plate {
        background-image: url(/images/plate.svg);
        width: 243px;
        height: 243px;
        position: relative;
    }

    .knob {
        top:20px;
        background-image: url(/images/knob.svg);
        width: 171px;
        height: 171px;
        transition: transform 1s;
        position: absolute;
        top: 37px;
        left: 37px;
    }

</style>