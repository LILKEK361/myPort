<script lang="ts">

    import Help from "$lib/Help.svelte";

    let input: String = "";
    let terminalInput;
    let terminalOutput: HTMLAreaElement;


    const allcomands = ["help", "contact", "clear", "whoami", "projects",]

    function scrollToBottom() {
        terminalOutput.scrollTop = terminalOutput.scrollHeight;
    }

    function onekeydown(e) {
        if (e.code === "Enter") {
            input = terminalInput.value;
            terminalOutput.innerHTML += `<div class="w-[100%] h-[10%] flex">
											<p class="w-[10%] text-center ml-[15px] mr-[15px]" >myportfolio@user:</p>
											<p class="w-90% flex" >${terminalInput.value}</p>
										 </div>`


            if (allcomands.includes(input)) {
                checkInput(input)
            } else {

                terminalOutput.innerHTML += `<div class="w-[100%] h-[10%] flex">
											 		<p class="w-[10%] text-center ml-[15px] mr-[15px]" >myportfolio@user: </p>
											 		<p class="">
											 			please enter a valid command or type help for all commands
													</p>
										 		   </div>`
            }
            terminalInput.value = "";
        }

    }

    function checkInput(input) {

        try {
            switch (input.toLowerCase()) {

                case "help":
                    terminalOutput.innerHTML += `<div class="w-[100%] h-[10%] flex ">
                                                    <p class="w-[10%] text-center ml-[15px] mr-[15px]">myportfolio@user: </p>
                                                    <p class="flex">
                                                        Help: displays all commands<br>
                                                        contanct: displays my contacts<br>
                                                        whoami: displays infos about me<br>
                                                        clear: clears the terminal<br>
                                                        projects: displays my GitHub Projects<br>
                                                    </p>
                                                </div>`;

                    break;
                case "whoami":
                    terminalOutput.innerHTML += `<div class="w-[100%] h-[10%] flex">
											 		<p class="w-[10%]  ml-[15px] mr-[15px]" >myportfolio@user: </p>
											 		<p class="flex">
											 			Hello, my Name is Nick Hillmann.<br>
											 		 	I am a Webdeveloper who learns<br>
											 			React, JS, TypeScript, Firebase etc.<br>
											 			I currently don't work but I always<br>
											 			open for new ideas and projects<br>
													</p>
										 		   </div>`
                    break;


                case "projects":
                    terminalOutput.innerHTML += `<div class="w-[100%] h-[10%] flex">
											 		<p class="w-[10%] text-center ml-[15px] mr-[15px]" >myportfolio@user: </p>
											 		<p class="">

													</p>
										 		   </div>`
                    break;


                case "clear":
                    terminalOutput.innerHTML = "";
                    break;
            }
        } catch (e) {
            console.log(e);
        }
        scrollToBottom();


    }
</script>

<div class="container h-full mx-auto flex justify-center items-center bg-surface-900 text-green-700">
    <div class=" w-[100%] h-[90%]  border-2 border-green-400 ">
        <div class=" min-h-[95%] max-h-[95%] bg-surface-900 pt-5 pb-5 overflow-x-hidden overflow-y-scroll"
             bind:this={terminalOutput}></div>
        <div class="h-[5%] w-[100%] bg-surface-600 flex border-2 border-green-400 justify-center items-center -ms ">
            <div class="w-[10%] h-[100%] ml-[15px] mr-2 mt-3.5 text-center ">myportfolio@user:</div>
            <input class="w-[90%] h-[100%] bg-surface-600 " bind:this={terminalInput} on:keydown={onekeydown} placeholder="pls enter command here">
        </div>

    </div>
</div>
