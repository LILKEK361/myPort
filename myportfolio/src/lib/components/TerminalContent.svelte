<script>
    let input;
    function onkeydown(e){
        if(e.keyCode == 69){
            console.log(input)
        }

    }
</script>

<div style="height: 100%; overflow: hidden; width: 100%; background: #242424;  margin: 0; padding: 0;  border: white 2px solid; display: flex; align-items: end" >
    <div style="width: 100%; margin: 0; padding: 0; display: flex; justify-content: flex-end">
        <p style="padding-right: 50px">myportfolio@user:</p>
        <input type="text" style="width: 90%;" bind:value={input} >

    </div>
</div>

