<script>
    import Header from "./components/Header.svelte";
import Footer from "./components/Footer.svelte";
import CreatPollForm from "./components/CreatPollForm.svelte";
import Tabs from "./shared/Tabs.svelte";

let items = ['Current Polls', 'Add New Poll'];
let activeItem = 'Current Polls';

function tabChange(e) {
    activeItem = e.detail;
}
</script>


<Header></Header>
    <main>
        <Tabs {activeItem} {items} on:tabChange={ tabChange }></Tabs>
            {#if activeItem === 'Current Polls'}
                <p>Poll List Comp</p>
            {:else if activeItem === 'Add New Poll'}
                <CreatPollForm></CreatPollForm>
            {/if}
    </main>
    <Footer></Footer>


<style>
    main {
        max-width: 960px;
        margin: 40px auto;
    }
</style>
