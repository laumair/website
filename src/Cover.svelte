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
        position: relative;
        width: 100%;
        height: 100vh;
        min-height: 600px;
        text-align: center;
        display: flex;
        justify-content: center;
        align-items: center;
        color: var(--cover-fg);
        background-color: var(--cover-bg);
    }

    .container {
        margin-top: 5rem;
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
    }

    .wrapper .down-arrow {
        display: none;
    }

    @media (min-height: 600px) {
        .wrapper .down-arrow {
            display: block;
            position: absolute;
            bottom: 2rem;
            left: 50vw;
            transform: translateX(-50%);
        }
    }

    @media (max-width: 767px) {
        .quote {
            visibility: hidden;
        }
    }

    .quote {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        flex-wrap: wrap;
        margin: auto;
        max-width: 75%;
        line-height: 1.5rem;
    }

    .quote > p > span {
        margin-left: 0.1rem;
        white-space: nowrap;
        font-weight: 500;
    }

    .quote > p > i {
        font-weight: 500;
    }
</style>

<div class="wrapper">
    <div class="container">
        <h1>{Content.name}</h1>
        <div>
            <img src="/images/me.jpg"
                 width="250px"
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
        <div class="quote">
            <p>
                <i>"{Content.quote.text}"</i>
                <span>— {Content.quote.by}</span>
            </p>
        </div>
    </div>
    <div on:click={scroll} class="down-arrow">
        <Icon icon="arrowDown"/>
    </div>
</div>
