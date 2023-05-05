<script lang="ts">
    import ProjectComponent from "$lib/TerminalSpecificEntries/ProjectComponent.svelte";
    import StartUpComponent from "$lib/TerminalSpecificEntries/StartUpComponent.svelte";
   export let data;

   export let userinput;
   console.log("Input:" + userinput)
   console.log("Data:" + data.toString())

    function clear(){
       console.log("Clear")
       const Window = document.getElementById("TerminalWindow");
       Window.innerHTML = "";
    }
</script>

<div id="TerminalWindow">
    <div class="w-[100%] h-[10%] flex">
        <p class="w-[10%] text-center ml-[15px] mr-[15px]" >myportfolio@user: </p>
        <p class="w-[90%]">
            {userinput}
        </p>
    </div>
    <div class="w-[100%] h-[10%] flex">
        <p class="w-[10%] text-center ml-[15px] mr-[15px]" >myportfolio@user: </p>


        {#if userinput in data}

            <ul class="w-[90%]" >
                {#if userinput === "projects"}
                    <ProjectComponent />
                    {:else if userinput === "clear"}
                    <li on:load={clear()}></li>

                    {:else}
                    {#each data[userinput] as da}
                        <li>{da}</li>
                    {/each}
                {/if}
            </ul>
            {:else}
            <ul class="w-[90%]" >
                <li>pls enter a valid command or type help to see all commands</li>
            </ul>

        {/if}


    </div>

</div>