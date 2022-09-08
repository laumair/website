<style>
    @font-face {
        font-family: 'Bitter';
        font-style: normal;
        font-weight: 600;
        font-display: swap;
        src: local('Bitter Bold'), local('Bitter-Bold'),
        url('/fonts/bitter-bold.woff2') format('woff2');
    }
    @font-face {
        font-family: 'Bitter';
        font-style: normal;
        font-weight: 500;
        font-display: swap;
        src: local('Bitter Medium'), local('Bitter-Medium'),
        url('/fonts/bitter-medium.woff2') format('woff2');
    }
    @font-face {
        font-family: 'Bitter';
        font-style: normal;
        font-weight: 400;
        font-display: swap;
        src: local('Bitter Regular'), local('Bitter-Regular'),
        url('/fonts/bitter-regular.woff2') format('woff2');
    }

    :global(body > main) {
        --max-width: 425px;
        --max-height: 680px;

        --quote-fg: #828282;

        --cover-bg: #222;
        --cover-fg: #eee;
        --cover-shadow: #000;

        --footer-fg: #eee;
        --footer-bg: #222;
    }
    :global(html, body) {
        width: 100%;
        height: 100%;
        font-family: 'Bitter', serif;
        font-weight: 400;
        margin: 0;
    }
</style>

<main>
    <slot />
</main>
