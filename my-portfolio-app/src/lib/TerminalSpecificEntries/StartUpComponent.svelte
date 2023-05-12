<script lang="ts">
    import {tick} from "svelte";

    let s = "Welcome to my repo".split("")
    let o = []


    for (let i = 0; i < s.length; i++) {

       async () => {
           o = [...o, s[i]];
           await tick();
       }
    }



</script>
<div class="w-[100%] h-[10%] flex">
    <p class="w-[10%] text-center ml-[15px] mr-[15px]" >myportfolio@user > </p>



           <p class="flex">{o}</p>




</div>