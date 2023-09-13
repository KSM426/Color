<script>
	import D0 from "./design/design0.svelte"
	import D1 from "./design/design1.svelte"
	import D2 from "./design/design2.svelte"
	import D3 from "./design/design3.svelte"

	let title;
	let colors = [
		"A0C49D", "C4D7B2", "E1ECC8", "000000"
	];
	let data=[];
	let design = 3;

	function saveColor(){
		data.push({title, colors})
		data = data
		console.log(data.length)
	}

	function changeDesign(n){
		design = n;
		console.log(design);
	}
</script>

<main>
	<div id="top">
		<div id="menu"><img width="20" height="20" src="./images/menu.png" alt="menu"></div>
		<div id="hd">PALETTE</div>
	</div>

	<div id="content">
		{#if design==0} <D0 {colors}/>
		{:else if design==1} <D1 {colors}/>
		{:else if design==2} <D2 {colors}/>
		{:else if design==3} <D3 {colors}/>
		{/if}

		<div class="design">
			<button class="designButton" id="base" on:click={()=>changeDesign('0')}>Base</button>
			<button class="designButton" id="line" on:click={()=>changeDesign('1')}>Line</button>
			<button class="designButton" id="circle" on:click={()=>changeDesign('2')}>Circle</button>
			<button class="designButton" id="frame" on:click={()=>changeDesign('3')}>Frame</button>
		</div>
		
		<div class="board">
			<div class="function">
				<button class="inFunc save" on:click={saveColor}><img width="20" height="20" src="./images/save5.png" alt="svae"></button>
				<input class="inFunc title inputTitle" bind:value="{title}" placeholder="TITLE" type="text">
				<button class="inFunc download"><img width="20" height="20" src="./images/download.png" alt="download"></button>
				<button class="inFunc share"><img width="20" height="20" src="./images/share4.png" alt="share"></button>
			</div>

			{#each colors as color, idx}
			<div class="colorRGB">
				<input class="inputRGB" bind:value="{color}" placeholder="{idx+1}" type="text"/>
				<button class="inFunc copy"><img width="20" height="20" src="./images/copy.png" alt="copy"></button>
			</div>
			{/each}
		</div>
	</div>
</main>

<style>
	img{
		margin-top: 3px;
	}
	input{
		margin: 0;
		padding: 0;
	}
	button:hover{
		background-color: bisque;
	}
	#top{
		position: relative;
		width: 100vw;
		height: 13vh;
	}
	#menu{
		position: absolute;
		top: 5vh;
		left: 5vw;
		transform: translate(-50%, -50%);
		color: red;
	}
	#hd{
		position: absolute;
		top: 5vh;
		left: 50vw;
		transform: translate(-50%, -50%);
		font-size: 30px;
		margin-top: 10px;
		text-align: center;
	}
	#content{
		width: 100vw;
		text-align: center;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
		.design{
			width: 320px;
			height: 40px;
			margin: 0;

			display: flex;
			flex-direction: row;
		}
			.designButton{
				background-color: beige;
				width: 80px;
				height: 40px;
				margin: 0;
				padding: 0;
			}
		.board{
			width: 340px;
			height: 250px;
			display: flex;
			flex-direction: column;
			align-items: center;
			padding-top: 15px;
			margin-top: 10px;
			/*border-radius: 0px;
			border-left: 1px solid gray;
			border-right: 1px solid gray;
			border: 0.5px solid black;*/
		}
			.function{
				width: 340px;
				height: 40px;
				margin-bottom: 15px;
				display: flex;
				flex-direction: row;
				align-items: center;
			}
				.inFunc{
					height: 40px;
					margin: 0;
				}
				.share{
					margin-left: 5px;
					width: 40px;
					background-color: beige;
					border-radius: 5px;
				}
				.download{
					margin-left: 5px;
					width: 40px;
					background-color: beige;
					border-radius: 5px;
				}
				.save{
					margin-left: 5px;
					width: 40px;
					background-color: beige;
					border-radius: 5px;
				}
				.inputTitle{
					margin-left: 5px;
					height: 40px;
					width: 195px;
					text-align:center
				}
				.colorRGB{
					width: 250px;
					height: 40px;
					display: flex;
					flex-direction: row;
					align-items: center;
					margin-bottom: 5px;
				}
					.copy{
						margin-left: 5px;
						width: 40px;
						background-color: beige;
						border-radius: 5px;
					}
					.inputRGB{
						margin-left: 5px;
						height: 40px;
						width: 195px;
						text-align:center;
					}
</style>