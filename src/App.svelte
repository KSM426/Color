<script>
	import D0 from "./design/design0.svelte"
	import D1 from "./design/design1.svelte"
	import D2 from "./design/design2.svelte"
	import D3 from "./design/design3.svelte"
	import "./app.css"

	let title = "TITLE";
	let colors = [
		"A0C49D", "C4D7B2", "E1ECC8", "000000"
	];
	let designs = [
		"Base", "Line", "Circle", "Frame"
	];

	let dataN = 1;
	let design = 0;

	function saveColor(){
		localStorage.setItem("data"+dataN, JSON.stringify(colors));
		
		let value = localStorage.getItem('data'+dataN);
		if (value !== null) {
			const retrievedColors = JSON.parse(value);
			console.log('값:', dataN, retrievedColors);
		} 
		else {
			console.log('데이터가 없습니다.');
		}
		
		dataN++;
	}

	function changeDesign(n){
		design = n.idx;
		console.log(design);
	}

	window.onload = function() {
		for (let i = 0; i < 4; i++) {
			let copyButton = document.getElementById("copy" + i);

			copyButton.addEventListener("click", function() {
				navigator.clipboard.writeText(colors[i]);
			});
		}
		document.getElementById("captureButton").addEventListener("click", function() {
            var captureArea = document.getElementById("captureArea");

            html2canvas(captureArea).then(function(canvas) {
                var downloadLink = document.createElement("a");
                downloadLink.href = canvas.toDataURL("image/png");
                downloadLink.download = title + "_" + colors[0] + "_" + colors[1] + "_" + colors[2] + "_" + colors[3] + "_" + designs[design] + ".png" ;
                downloadLink.click();
			});
		});

	const openPopup = document.querySelector(".menu");
	const closePopup = document.getElementById('closePopup');
	const modal = document.getElementById('menuPopup');

	openPopup.addEventListener('click', function() {
		modal.style.display = 'block';
	});

	closePopup.addEventListener('click', function() {
		modal.style.display = 'none';
	});

	window.addEventListener('click', function(event) {
		if(event.target == modal) {
			modal.style.display = 'none';
		}
	});

	}

</script>

<link rel='stylesheet' href='app.css'>

<main>

	<div id="top">
		<button class="menu buttonHover"><img width="20" height="20" src="./images/menu.png" alt="menu"></button>
		<div id="hd">PALETTE</div>
	</div>

	<div id="menuPopup" class="modal">
        <div class="modal-content">
            <span class="close" id="closePopup">&times;</span>
            <p>팝업 내용을 입력하세요.</p>
        </div>
    </div>
	
	<div id="content">
		<div id="captureArea">
			<div style="width: 340px; height: 10px;"></div>
			{#if design==0} <D0 {colors}/>
			{:else if design==1} <D1 {colors}/>
			{:else if design==2} <D2 {colors}/>
			{:else if design==3} <D3 {colors}/>
			{/if}
		</div>

		<div class="design">
			{#each designs as d, idx}
				{#if design == idx}
					<button class="designButton buttonHover" on:click={()=>changeDesign({idx})} style="font-weight: bolder;">{d}</button>
				{:else}
					<button class="designButton buttonHover" on:click={()=>changeDesign({idx})}>{d}</button>
				{/if}
			{/each}
			<!--<button class="designButton buttonHover" id="base" on:click={()=>changeDesign('0')}>Base</button>
			<button class="designButton buttonHover" id="line" on:click={()=>changeDesign('1')}>Line</button>
			<button class="designButton buttonHover" id="circle" on:click={()=>changeDesign('2')}>Circle</button>
			<button class="designButton buttonHover" id="frame" on:click={()=>changeDesign('3')}>Frame</button>-->
		</div>
		
		<div class="board">
			<div class="function">
				<button class="inFunc save buttonHover" on:click={saveColor}><img width="20" height="20" src="./images/save5.png" alt="svae"></button>
				<input class="inFunc title inputTitle" bind:value="{title}" type="text">
				<button class="inFunc download buttonHover" id="captureButton"><img width="20" height="20" src="./images/download.png" alt="download"></button>
				<!--<button class="inFunc share"><img width="20" height="20" src="./images/share4.png" alt="share"></button>-->
			</div>

			{#each colors as color, idx}
			<div class="colorRGB">
				<!--<button class="inFunc colorBoard" id="copy{idx}"><div style="margin-left: 2.8px; width:20px; height:20px; background-color: #{color}"></div></button>-->
				<div class="inFunc colorBoard" id="copy{idx}" style="background-color: #{color}"></div>
				<input class="inputRGB" bind:value="{color}" placeholder="{idx+1}" type="text"/>
				<button class="inFunc copy buttonHover" id="copy{idx}"><img width="20px" height="20px" src="./images/copy.png" alt="copy"></button>
			</div>
			{/each}
		</div>
	</div>
</main>