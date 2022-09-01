<script>
    export let spells;
</script>
<ul>
    {#each spells as spell}
        <a href="https://pf2.d20pfsrd.com/spell/{spell.toLowerCase().replace(/[^a-z]/, '-')}/"><li>{spell}</li></a>
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