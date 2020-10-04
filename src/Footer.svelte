<script>
    function today() {
        return new Date().getFullYear();
    }
</script>

<style>
    footer {
        color: var(--footer-fg);
        background-color: var(--footer-bg);
        padding: 1rem;
    }

    footer > div {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
</style>

<footer>
    <div>
        <p>
            &copy;
            {today()}
            Umair Sarfraz
        </p>
    </div>
</footer>
