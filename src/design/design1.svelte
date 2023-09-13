<script>
    export let colors;
</script>

<main>
    <div id="show">
        <div id="paper" style="box-shadow: #fff;">
            {#each colors as color, idx}
                <div style="width: 320px; height: 65px"></div>
                <div class="line" style="background-color: #{color};">{idx+1}</div>
            {/each}
        </div>
    </div>
</main>

<style>
    main{
        text-align: center;
    }
    #show{
        width: 100vw;
        height: 340px;
        display: flex;
        justify-content: center;
        margin-bottom: 15px;
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
    .line {
        width: 250px;
        height: 4px;
        margin: 0;
    }
</style>