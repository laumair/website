<script>
    import Icon from './Icon.svelte';
    import Content from './content.json';

    export let elementToScrollTo;

    function scroll() {
        elementToScrollTo.scrollIntoView({behavior: "smooth"});
    }
</script>

<style>
    .wrapper {
        width: 100%;
        height: 100vh;
        min-height: 600px;
        text-align: center;
        display: flex;
        justify-content: space-evenly;
        flex-direction: column;
        align-items: center;
        color: var(--cover-fg);
        background-color: var(--cover-bg);
    }

    .wrapper .button-row {
        display: flex;
        justify-content: center;
        margin: 0.5rem;
    }

    .wrapper .button-row a {
        display: block;
        margin: 7px;
        border-radius: 50%;
        max-width: 50px;
        max-height: 50px;
    }

    .shadow {
        box-shadow: 0.5rem 0.5rem 1rem var(--cover-shadow);
    }

    img {
        border-radius: 0.5rem;
        margin: 1rem;
    }

    h1 {
        text-shadow: 0.5rem 0.5rem 1rem var(--cover-shadow);
        font-weight: 600;
        margin-bottom: 0;
    }
</style>

<div class="wrapper">
    <div class="container">
        <h1>{Content.name}</h1>
        <div>
            <img src="/images/me.jpg"
                 width="35%"
                 class="shadow"
                 alt={Content.name}
            />
            <div class="button-row">
                {#each Content.links as link}
                    <a class="shadow" href={link.link} title={link.type}>
                        <Icon auto icon={link.type}/>
                    </a>
                {/each}
            </div>
        </div>
    </div>
    <!-- <div class="quote">
        <p>
            <i>"{Content.quote.text}"</i>
            <span>— {Content.quote.by}</span>
        </p>
    </div> -->
    <div on:click={scroll} class="down-arrow">
        <Icon icon="arrowDown"/>
    </div>
</div>
