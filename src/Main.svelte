<script>
    import Content from './content.json';
</script>

<style>
    .container {
        width: 80%;
        margin-left: auto;
        margin-right: auto;
        max-width: 75rem;
    }

    .inner {
        margin: 2rem 0;
    }

    .intro {
        padding: 2rem 0;
    }
</style>

<div class="container">
    <div class="inner">
        <p class="intro">{Content.intro}</p>
        <h3>Programming</h3>
        <p>{Content.programming}</p>
        <p>
            Projects I have worked on:
        </p>
        <ul>
            {#each Content.projects as project}
                <li>
                    <a href={project.link}>{project.name}</a>
                </li>
            {/each}
        </ul>
        <h3>Publications</h3>
        <ul>
            {#each Content.publications as publication}
                <li>
                    <a href={`/documents/publications/${publication.link}`}>{publication.title}</a>
                </li>
            {/each}
        </ul>
        <h3>Curriculum Vitae</h3>
        <p>
            Please click <a href="/documents/cv.pdf">here.</a>
        </p>
        <h3>Blog</h3>
        <p>
            Coming soon.
        </p>
    </div>
</div>
