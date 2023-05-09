<script lang="ts">
    let s = "Welcome to my repo".split("")
    let o = []

   function delay(ms: number) {
        return new Promise( resolve => setTimeout(resolve, ms) );
    }

    for(let i = 0; i < s.length; i++){
        o.push(s[i])
       async () => {
           await delay(1000)
       }
       console.log(o)
    }



</script>
<div class="w-[100%] h-[10%] flex">
    <p class="w-[10%] text-center ml-[15px] mr-[15px]" >myportfolio@user > </p>

        <p>Welcome to my Portfolio,<br>
        pls enter help to display all available commands </p>

</div>