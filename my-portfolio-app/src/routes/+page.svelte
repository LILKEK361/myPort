<script lang="ts">

    import Help from "$lib/Help.svelte";
    import TerminalEntery from "$lib/TerminalEntery.svelte";
    import TerminalHeader from "$lib/TerminalHeader.svelte";
    import StartUpComponent from "$lib/TerminalSpecificEntries/StartUpComponent.svelte";
    let input: String = "";
    let terminalInput;
    let terminalOutput: HTMLAreaElement;
    



    let inputs = []
    let data = {
        "help" : [
            "help: displays all commands",
            "whoami: displays information about me",
            "projects: displays my projects and projects I worked in",
            "contacts: displays information to contact me"
        ],
        "whoami" : [
            "I am Nick Hillmann," +
            " 18 years old, ",
            "a computer science student at the TBZ Bremen",
            "and very engaged in learning everthing "],
        "projects" : [""],
        "contact" : [""],
        "startup" : [""],

    };

    function scrollToBottom() {
        terminalOutput.scrollTop = terminalOutput.scrollHeight;
    }

    function onekeydown(e) {
        if (e.code === "Enter") {
            input = terminalInput.value;
            if(input != "clear")
            {inputs = [...inputs, input]
                terminalInput.value = ""
                ;}
            else{
                const Window = document.getElementById("TerminalWindow");
                Window.innerHTML = "";
                terminalInput.value = ""
            }
            scrollToBottom();


        }

    }

</script>

<div class="container h-full mx-auto flex justify-center items-center bg-surface-900 text-green-700">
    <div class=" w-[100%] h-[90%]  border-4 border-green-400 ">
        <div class="w-[100%] h-[5%] border-green-600 border-b-2 m-0 p-0">
            <TerminalHeader />
        </div>
        <div id="TerminalWindow" class=" min-h-[90%] max-h-[90%]  pt-5 pb-5 overflow-x-hidden overflow-y-scroll"
             bind:this={terminalOutput}>
                <StartUpComponent/>
                {#each inputs as i}
                <TerminalEntery userinput={i.toLowerCase()} data={data}></TerminalEntery>
                {/each}

        </div>
        <div class="h-[5%] w-[100%] bg-surface-600 flex  border-t-4 border-t-green-600  justify-center items-center content-center">
            <div class="w-[10%] h-[100%] ml-[15px] mt-3.5  flex ">myportfolio@user <p class="text-right"> > </p></div>
            <input class="w-[90%] h-[100%] bg-surface-600  outline-none "   bind:this={terminalInput} on:keydown={onekeydown} placeholder="pls enter command here">

        </div>

    </div>
</div>
