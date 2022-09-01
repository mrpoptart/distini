<script>
    import Knob from './components/Knob.svelte'
    import Switches from "./components/Switches.svelte";
    import Spells from "./components/Spells.svelte";

    let knobSelection = 'do';
    let switchSelection = 'nothin';

    let options = {
        do: {'nothin': ['ok']},
        assault: {
            "I'm tired of this. I want to kill all of these dudes at once": [
                "Burning Hands",
                "Fireball",
                "Lightning Bolt",
                "Cloudkill",
                "Chain Lightning",
            ],
            "Fuck that one guy in particular": [
                "Produce Flame",
                "True Strike",
                "Phantasmal Killer",
                "Disintegrate",
            ],
            "These guys are boring, but they still need to die": [
                "Electric Arc",
                "Magic Missile",
                "Burning Hands",
                "Sleep",
            ],
            "Oh shit oh shit": [
                "Shield",
                "Resist Energy",
                "Spell Immunity",
            ],
        },
        amaze: {
            "I'm going to get my way, and here's how": [
                "Command",
                "Control Water",
                "Collective Transposition",
            ],
            "That hot girl needs some sweet moves": [
                "Enthrall",
                "Aerial Form",
                "Dragon Form",
            ],
            "Just being near me makes you more awesome": [
                "Counter Performance",
                "Resist Energy",
                "Cloak of Colors",
                "Haste",
            ],
            "Be afraid, be very afraid (of me!)": [
                "Phantasmal Killer",
                "Mask of Terror",
            ]
        },
        annoy: {
            "You don't need your senses for anything, do you?": [
                "Daze",
                "Prismatic Spray",
                "Warp Mind",
            ],
            "Your body isn't the most useful thing when I'm around": [
                "Command",
                "Daze",
                "Sleep",
                "Warp Mind",
                "Prismatic Spray",
            ],
            "It's not you, it's the world that's cruel.": [
                "Spell Immunity",
                "Chromatic Wall",
                "Collective Transposition",
            ],
            "Hey guys, watch this": [
                "Dragon Claws",
                "Collective Transposition",
                "Dancing Lights",
            ],

        },
        amplify: {
            "You can do it!": [
                "Inspire Courage",
                "Counter Performance",
                "Haste",
            ],
            "I'm tired of not looking awesome": [
                "Dragon Claws",
                "Aerial Form",
                "Dragon Form",
            ],
            "I'm not like normal goblins, I can do this:": [
                "Spider Climb",
                "Dragon Claws",
                "Aerial Form",
                "Dragon Form",
            ],
            "It's the world that needs to change, not me": [
                "Enlarge",
                "Haste",
            ],
        },
    }

    function resetClasses(){
        Object.values(document.getElementsByClassName('flipped')).map((el) => {
            el.classList.remove('flipped');
        })
    }

    function handleKnobSelect(e) {
        knobSelection = e.detail.selection;
        switchSelection='nothin';
        resetClasses();
    }

    function handleSwitch(e){
        console.log(e.detail.id)
        switchSelection = e.detail.id;
    }

</script>

<div class="main">
    <Knob on:select={handleKnobSelect}/>
    <Switches resetClasses="{resetClasses}" options="{Object.keys(options[knobSelection])}" knobSelection="{knobSelection}" on:select={handleSwitch}/>
    {#if switchSelection!=='nothin'}
        <Spells spells="{options[knobSelection][switchSelection]}"/>
    {/if}
</div>

<style>
    .main {
        display: flex;
        flex-direction: column;
        gap: 30px;
        align-items: center;
        padding: 50px;
    }
</style>
