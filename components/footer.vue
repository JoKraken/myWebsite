<template>
    <footer class="footer gridContainer__element">
        <div class="footer__background"></div>
        <ul class="footer__list gridContainer">
            <li class="footer__person">
                <p>Johanna Kraken</p>
                <p>Franz-Sellhorst-Str. 20,<br> 48432 Rheine</p>
                <a href="tele:015161841189">+49 1516 1841189</a> <br>
                <a href="mailto:J.Kraken24@hotmail.com">J.Kraken24@hotmail.com</a>
            </li>
            <li class="footer__pages">
                <p>Pages</p>
                <hr />
                <ul>
                    <li><a href="/">Home</a></li>
                    <li><a href="/portfolio/">Portfolio</a></li>
                    <li><a href="/contact/">Contact</a></li>
                </ul>
            </li>
            <li class="footer__links">
                <p>Links</p>
                <hr />
                <ul>
                    <li><a href="https://github.com/JoKraken" target="_blank">Github</a></li>
                    <li><a href="https://www.linkedin.com/in/johannakraken/" target="_blank">LinkedIn</a></li>
                    <li><a href="https://www.xing.com/profile/Johanna_Kraken/cv" target="_blank">XING</a></li>
                </ul>
            </li>
        </ul>
    </footer>
</template>

<style lang="scss" scoped>
    body {
        margin: 0;
    }

    .footer {
        padding: 15px;
        display: flex;
        flex-flow: row;
        color: $white;
        justify-content: space-between;
    }

    .footer__background {
        background-color: $primary;
        position: absolute;
        bottom: 0;
        right: 0;
        left: 0;
        height: 21.5vh;
        z-index: -1;

        @include for-phone {
            height: 35vh;
        }
    }

    .footer__list {
        grid-template-columns: repeat(6, [col-start] 1fr);
        grid-gap: 2rem;
        padding: 0;

        @include for-phone {
            grid-template-columns: repeat(2, [col-start] 1fr);
        }
    }

    .footer__list > li {
        margin: 0 15px;

        &::marker {
            content: none;
        } 

        a {
            text-decoration: none;
            color: white;
        }

        a:hover {
            text-decoration: underline;
        }
    }

    .footer__person {
        grid-column: col-start 1 / span 2;
    }

    .footer__pages,
    .footer__links {
        p {
            margin-top: 0;
        }
    }
</style>