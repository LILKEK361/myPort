<script lang="ts">

	import terminalbar from "$lib/terminalbar.svelte";

	let input =  "";
	let terminalInput;
	let terminalOutput : HTMLAreaElement;


	const allcomands = ["help","contact", "clear", "whoami"]

	function onekeydown(e){
		if(e.code === "Enter"){
			input = terminalInput.value;
			allcomands.includes(input) ? checkInput(input) : "";

			terminalInput.value = "";
		}

	}
	function checkInput(input) {

		try {
			switch (input) {
				case "whoami":
						terminalOutput.innerHTML += `<div class="w-[100%] h-[10%] flex">
											 <p class="w-[10%] text-center ml-[15px] mr-[15px]" >myportfolio@user: </p>
											 <p class="w-[90%] text-left">Hello I am Nick Hillmann</p>
										 </div>`
					break;
				case "help":
					terminalOutput.innerHTML += `<div class="w-[100%] h-[10%] flex">
											 <p class="w-[10%] text-center ml-[15px] mr-[15px]" >myportfolio@user: </p>
											 <p class="flex">
											 	Help: displays all commands<br>
											 	Contanct: Displays my contacts<br>
											 	whoami: Displays infos about me<br>
											 	clear: clears the terminal<br>
											</p>
										 </div>`
					break;
				case "clear":
					terminalOutput.innerHTML = "";
					break;




			}
		}catch (e) {
						console.log(e);
		}


	}
</script>

<div class="container h-full mx-auto flex justify-center items-center bg-surface-600">
	<div class=" w-[99%] h-[90%]  border-2 border-amber-50 ">
		<div class="relative min-h-[90%]  max-h-[90%] bg-surface-600 pt-5 pb-5" bind:this={terminalOutput} ></div>
		<div class="h-[10%] w-[100%] bg-surface-600 flex border-tertiary-200-700-token border-amber-50">
			<div  class="w-[10%] text-center ml-[15px] mr-[15px] h-[100%]">myportfolio@user:</div>
			<input class="w-[90%]" bind:this={terminalInput} on:keydown={onekeydown}>
		</div>
	</div>
</div>
