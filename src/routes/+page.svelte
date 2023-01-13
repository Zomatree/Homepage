<script lang="ts">
    import dayjs from "dayjs";
	import { onMount } from "svelte";

    import Bookmark from "$lib/components/Bookmark.svelte";

    import "./styles.scss";

    export let search_text: string;
    export let formatted_time: string = dayjs().format("HH:mm:ss");

    onMount(() => {
        setInterval(() => {
            formatted_time = dayjs().format("HH:mm:ss")
        }, 1000)
    })

    function search() {
        window.location.href = `https://www.google.com/search?q=${encodeURIComponent(search_text)}`
    }

    function checkKey(evt: KeyboardEvent) {
        console.log(evt);
        if (evt.key == "Enter") {
            search()
        }
    }
</script>

<div class="main">
    <div class="centered">
        <div class="time">
            { formatted_time }
        </div>
        <div class="input">
            <input class="search-input" placeholder="Search Google" on:keyup={checkKey} bind:value={search_text}>
            <button class="search-button" on:click={search}>Search</button>
        </div>
        <div class="bookmarks">
            <div class="bookmark-row">
                <Bookmark name="Youtube" url="https://youtube.com"/>
                <Bookmark name="College" url="https://hub.exe-coll.ac.uk/"/>
            </div>
            <div class="bookmark-row">
                <Bookmark name="Github" url="https://github.com"/>
                <Bookmark name="Revolt" url="https://revolt.chat"/>
            </div>
        </div>
    </div>
</div>
