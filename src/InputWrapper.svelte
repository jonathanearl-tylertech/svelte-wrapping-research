<svelte:options tag="input-wrapper"/>
<script>
	import { onMount, afterUpdate } from 'svelte';

    //MUST BE LOWER CASEING
    export let targetid = "";
    export let clocktitle = "Svelte Clock"

    function toggleVisible() {
        // setTimeout(() => {
        console.log('targetid', targetid); // Hello World!
        let target = document.querySelector(`#${targetid}`);
        console.log('target', target); // Hello World!
        let inputType = target.getAttribute('type');
        // console.log(inputType)
        target.setAttribute('type', 'password');
    }

    onMount(() => {
        // PROPS NOT INITILIZED ON MOUNT, NEED TO WAIT A CYCLE
        setTimeout(() => {
            console.log(clocktitle);
        });
    })

    afterUpdate(() => {
        console.log(clocktitle);
    })
</script>

<h1>{clocktitle}</h1>
<div class="input-wrapper">
    <slot></slot>
    <div class="icon" on:click={toggleVisible}></div>
</div>

<style>
    ::slotted(input) {
        width: calc(100% - 50px) !important;
        border: none;
        inset: none;
        background-color: grey;
    }

    .input-wrapper {
        width: 100%;
        display: flex;
    }

    .icon {
        background-color: white;
        width: 50px;
        height: 50px;
        flex: 0 0 auto;
    }
</style>