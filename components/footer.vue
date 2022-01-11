<template>
    <footer class="footer">
        <ul class="footer_list">
            <li>
                <p>Johanna Kraken</p>
                <p>Franz-Sellhorst-Str. 20,<br> 48432 Rheine</p>
                <p>Email: J.Kraken24@hotmail.com</p>
            </li>
            <li>
                <p>Pages:</p>
                <p><a href="#">Home</a></p>
                <p><a href="#">Portfolio</a></p>
                <p><a href="#">Contact</a></p>
            </li>
            <li>
                <p>Links:</p>
                <p><a href="#">Github</a></p>
                <p><a href="#">LinkedIn</a></p>
                <p><a href="#">XING</a></p>
            </li>
        </ul>
    </footer>
</template>

<style>
    body {
        margin: 0;
    }

    .footer {
        background-color: brown;
        padding: 15px;
        display: flex;
        flex-flow: row;
        color: white;
        justify-content: space-between


    }
    
    .footer__list {
        display: flex;
        flex-flow: row;

    }
    
    .footer__list > li {
        margin: 0 15px;
    }

    .footer__list > li > a {
        text-decoration: none;
        color: white;
    }

    .footer__list > li::marker {
        content: none;
    }

    .footer__list > li > a:hover {
        text-decoration: underline;
    }
</style>