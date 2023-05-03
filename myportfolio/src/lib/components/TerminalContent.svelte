<script>

    let input ="";
    let terminalInput;

    const allcommands = [
        "help",
        "profile",
        "projects",
        "contact"
    ]
    function commandSubmit(e) {
        if (e.code === "Enter") {
            input = terminalInput.value;
            allcommands.includes(input) ? console.log(input) : "";
            terminalInput.value = "";

        }

    }
</script>


<div style="height: 100%; width: 100%; border: 2px solid white; grid-row: 2; ">
    <div style="row-span: 1; height: 95%; text-align: justify-all ;">
        
    </div>
    <div style="row-span: 2; ">
        <div style="width: 100%; margin: 0; padding: 0; display: flex; justify-content: flex-end">
            <p style=" padding-right: 20px; padding-left: 20px; text-align: justify; font-size: 15px ">myportfolio@user:</p>
            <input  type="text" style="width: 90%;" bind:this={terminalInput}  on:keydown={commandSubmit} >

        </div></div>
</div>
