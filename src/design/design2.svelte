<script>
    export let colors;
</script>

<main>
    <div id="show">
        <div id="paper" style="box-shadow: #fff;">
            <div style="width:320px; height:10px;"></div>
            <svg width="320px" height="320px">
                <circle cx="80" cy="80" r="70" fill="#{colors[0]}" />
                <circle cx="240" cy="80" r="70" fill="#{colors[1]}" />
                <circle cx="80" cy="240" r="70" fill="#{colors[2]}" />
                <circle cx="240" cy="240" r="70" fill="#{colors[3]}" />
                <text x="140" y="150" fill="black">1</text>
                <text x="170" y="150" fill="black">2</text>
                <text x="140" y="180" fill="black">3</text>
                <text x="170" y="180" fill="black">4</text>
            </svg>
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
        box-shadow: 3px 3px 10px;
        border-radius: 20px;

        display: flex;
        flex-direction: column;
        align-items: center;
    }
    
</style>