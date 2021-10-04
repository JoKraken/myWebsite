<template>
    <nav class="navbar">
        <div class="navbar__header">
            <img src="../static/octopus.png">
            <div>Johanna Kraken</div>
        </div>
        <ul class="navbar__list">
            <li class="active"><a href="#">Home</a></li>
            <li><a href="#">Portfolio</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
    </nav>
</template>

<script>

</script>

<style>
    body {
        margin: 0;
    }

    .navbar {
        background-color: brown;
        padding: 15px;
        display: flex;
        flex-flow: row;
        color: white;
        justify-content: space-between


    }
    .navbar__header,
    .navbar__list {
        display: flex;
        flex-flow: row;

    }

    .navbar__header > img {
        width: 40px;
        margin-right: 25px;
    }

    .navbar__header > div {
        margin: auto;
    }

    .navbar__list > li {
        margin: 0 15px;
    }

    .navbar__list > li > a {
        text-decoration: none;
        color: white;
    }

    .navbar__list > li::marker {
        content: none;
    }

    .navbar__list > li > a:hover {
        text-decoration: underline;
    }
</style>