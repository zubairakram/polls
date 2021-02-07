<script>
    /* import { onMount, onDestroy } from "svelte"; */
    import PollStore from "../stores/PollStore.js";
    import PollDetail from "./PollDetail.svelte";
    /* export let polls = []; */

/* const unsub = PollStore.subscribe(data => { */
/*     polls = data; */
/* }); */

/* onMount(() => { */
/*     console.log('component Mounted'); */
/* }) */

/* onDestroy(() => { */
/*     console.log('component deleted'); */
/*     unsub(); */
/* }) */

</script>
<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <div>
            <PollDetail { poll } on:vote></PollDetail>
        </div>
    {/each}
</div>

<style>
    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>
