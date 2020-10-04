<script>
    import Cover from './Cover.svelte';
    import Main from './Main.svelte';
    import Footer from './Footer.svelte';
    import Theme from './Theme.svelte';

    let section;
</script>

<svelte:window/>

<Theme>
    <Cover elementToScrollTo={section}/>
    <div bind:this={section}>
        <Main/>
    </div>
    <Footer/>
</Theme>
