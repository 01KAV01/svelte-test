<svelte:head>
<title>Блог</title>
</svelte:head>
<div class='container'>
    <h1>Мой блог</h1>
    <div class='blogposts'>
        {#each routes as page}
            <div class='post'>
                <h2>{page.title}</h2>
                <p>{page.body}</p>
                <p class='readmore'>
                    <a class='link' href={`/blog/posts/${page.id}`}>
                         Читать далее
                    </a>
                </p>
            </div>
        {/each}
    </div>
</div>

<script>
    import {routes} from './routes'
</script>

    <style>

:root {
    --primary-color: #3498db;
    --secondary-color: #2ecc71;
    --text-color: #333;
    --background-color: #f5f5f5;
    --border-color: #e7e7e7;
}

.blogposts {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
}

.post {
    border: 1px solid var(--border-color);
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    background-color: var(--background-color);
    border-radius: 5px;
    transition: box-shadow 0.3s ease;
}

.post:hover {
    box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
}

.link {
    color: var(--primary-color);
    text-decoration: none;
    transition: color 0.3s ease;
}

.link:hover {
    color: var(--secondary-color);
}

h1, h2 {
    color: var(--primary-color);
}

p {
    margin-bottom: 10px;
}
 
    </style>