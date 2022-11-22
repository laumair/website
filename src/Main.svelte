<script>
    import Content from "./content.json";
</script>

<div class="container">
    <div class="inner">
        <p class="intro">{Content.intro}</p>
        <h3>Programming</h3>
        <p>{Content.programming}</p>

        <h3>Projects</h3>
        {#each Content.projects as project}
            <p>
                <a href={project.link}>
                    <img
                        class="project-image"
                        width="25%"
                        src={`/images/${project.image}`}
                        alt={Content.name}
                    />
                    <b>{project.name}</b>
                </a>

                {project.description}
            </p>
            <div class="project-margin" />
        {/each}

        <h3>Research & Publications</h3>
        <p>{Content.research.text}</p>
        <ul>
            {#each Content.publications as publication}
                <li>
                    <a href={`/documents/publications/${publication.link}`}
                        >{publication.title}</a
                    >
                </li>
            {/each}
        </ul>

        <h3>Curriculum Vitae</h3>
        <p>
            Please click <a href="/documents/cv.pdf">here.</a>
        </p>

        <h3>Random Stuff</h3>
        <ul>
            {#each Content.quotes as quote}
                <li>
                    <p class="quote">
                        <i>"{quote.text}"</i>
                        <span>— {quote.by}</span>
                    </p>
                </li>
            {/each}
        </ul>
        <!-- <h3>Blog</h3>
        <p>Coming soon.</p> -->
    </div>
</div>

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

    .project-margin {
        clear: both;
    }

    .project-image {
        float: left;
        margin: 0px 10px 0px;
        max-width: 50%;
    }

    .quote {
        font-size: 14px;
        font-weight: 400;
        color: var(--quote-fg);
    }
</style>
