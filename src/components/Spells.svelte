<script>
    export let spells;
    function handleClick(e){
        let url = `https://pf2.d20pfsrd.com/spell/${e.target.innerText.toLowerCase().replace(/[^a-z]/, '-')}/`;
        console.log(url)
        window.location = url;
    }
</script>
<ul>
    {#each spells as spell}
        <li on:click={handleClick}>{spell}</li>
    {/each}
</ul>
<style>
    li {
        font-size: 40px;
        line-height: 50px;
        font-weight: bold;
        text-align: center;
        list-style-type: none;
        border: 1px solid #DDD;
        padding: 10px 40px;
        margin-bottom: 10px;
    }
</style>