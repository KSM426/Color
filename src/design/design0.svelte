<script>
    export let colors;
</script>

<main>
    <div id="paper" style="box-shadow: #fff;">
        {#each colors as color, idx}
            {#if idx==0}
                <div id="in"
                style="background-color: #{color};
                margin-top: 10px;
                border-top-left-radius: 20px;
                border-top-right-radius: 20px;">{idx+1}</div>
            {:else if idx==3}
                <div id="in"
                style="background-color: #{color};
                border-bottom-left-radius: 20px;
                border-bottom-right-radius: 20px;">{idx+1}</div>
            {:else}
                <div id="in" style="background-color: #{color};">{idx+1}</div>
            {/if}
        {/each}
    </div>
</main>

<style>
    main{
        text-align: center;
    }
    #paper{
        width: 340px;
        height: 340px;
        display: flex;
        flex-direction: column;
        align-items: center;
        box-shadow: 3px 3px 10px;
        border-radius: 20px;
    }
    #in{
        margin: 0;
        padding: 0;
        width: 320px;
        height: 80px;

        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>