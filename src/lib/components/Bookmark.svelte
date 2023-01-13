<script lang="ts">
    export let name: string;
    export let url: string;
</script>

<style>
    .bookmark {
        padding: 20px 60px;
    }

    .bookmark-link {
        text-align: center;
        text-decoration: none;
        color: var(--fg-3);
    }
</style>

<div class="bookmark">
    <a class="bookmark-link" href={ url }>
        { name }
    </a>
</div>
