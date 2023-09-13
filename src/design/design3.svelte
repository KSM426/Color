<script>
    export let colors;
</script>

<main>
    <div id="show">
        <div id="paper" style="box-shadow: #fff;">
            <div style="width:320px; height:10px;"></div>
            <svg style="width:320px; height:320px;">
                <rect x="0" y="0" width="320" height="320" rx="20" ry="20" fill="#{colors[0]}" />
                <rect x="40" y="40" width="240" height="240" rx="20" ry="20" fill="#{colors[1]}" />
                <rect x="80" y="80" width="160" height="160" rx="20" ry="20" fill="#{colors[2]}" />
                <rect x="120" y="120" width="80" height="80" rx="20" ry="20" fill="#{colors[3]}" />
                <text x="155" y="25" fill="black">1</text>
                <text x="155" y="65" fill="black">2</text>
                <text x="155" y="105" fill="black">3</text>
                <text x="155" y="145" fill="black">4</text>
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
        display: flex;
        flex-direction: column;
        align-items: center;
        box-shadow: 3px 3px 10px;
        border-radius: 20px;
    }
    
</style>