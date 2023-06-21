<script>
	import D0 from "./design0.svelte"
	let colors = [
		'A0C49D', 'C4D7B2', 'E1ECC8', '000000'
	];
	let design = 0;
</script>

<main>
	<div id="top">
		<div id="menu">mm</div>
		<div id="hd">PALETTE</div>
	</div>

	<div id="content">
		<D0 {colors}/>

		<div id="function">
			<div class="inFunc" id="share"></div>
			<div class="inFunc" id="space"></div>
			<div class="inFunc" id="copy"></div>
			<div class="inFunc" id="save"></div>
		</div>

		{#each colors as color, idx}
			<div>{idx+1} : <input bind:value="{color}" type="text"/></div>
		{/each}
	</div>
</main>

<style>
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
	#function{
		width: 340px;
		height: 50px;
		background-color: #F7FFE5;
		margin-bottom: 15px;
		border: solid 0.5px black;
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.inFunc{
		height: 40px;
		background-color: gray;
	}
	#share{
		margin-left: 5px;
		width: 40px;
	}
	#space{
		margin-left: 5px;
		width: 195px;
	}
	#copy{
		margin-left: 5px;
		width: 40px;
	}
	#save{
		margin-left: 5px;
		width: 40px;
	}
</style>