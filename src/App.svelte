<script>
    import Header from "./components/Header.svelte";
import Footer from "./components/Footer.svelte";
import PollList from "./components/PollList.svelte";
import CreatPollForm from "./components/CreatPollForm.svelte";
import Tabs from "./shared/Tabs.svelte";

let items = ['Current Polls', 'Add New Poll'];
let activeItem = 'Current Polls';

function tabChange(e) {
    activeItem = e.detail;
}

// polls
let polls = [
    {
        id: 1,
        question: 'Python or Javascript',
        answerA: 'Python',
        answerB: 'Javascript',
        votesA: 9,
        votesB: 15,
    }
];

function handleAdd (e) {
    const poll = e.detail;
    polls = [poll, ...polls];
    console.log(polls);
    activeItem = 'Current Polls';
}

function handleVote(e) {
    const { id, option } = e.detail;
    let copiedPolls = [...polls];
    let upvotedPoll = copiedPolls.find((poll) => poll.id == id);

    if (option === 'a') {
        upvotedPoll.votesA++;
    } else if (option === 'b') {
        upvotedPoll.votesB++;
    }

    polls = copiedPolls;
}
</script>


<Header></Header>
    <main>
        <Tabs {activeItem} {items} on:tabChange={ tabChange }></Tabs>
            {#if activeItem === 'Current Polls'}
                <PollList {polls} on:vote={handleVote}></PollList>
            {:else if activeItem === 'Add New Poll'}
                <CreatPollForm on:add={handleAdd}></CreatPollForm>
            {/if}
    </main>
    <Footer></Footer>


<style>
    main {
        max-width: 960px;
        margin: 40px auto;
    }
</style>
