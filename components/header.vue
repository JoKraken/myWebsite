<template>
    <nav class="navbar gridContainer__element">
        <div class="navbar__background"></div>
        <div class="gridContainer gridContainer--secound">
            <!--Links class="navbar__header" :data="data"-->
            <a class="navbar__header" href="/">
                <img src="../static/icons/octopus.png">
                <span>Johanna Kraken</span>
            </a>
            <div class="navbar__list">
                <ul>
                    <li class="active"><a href="/">Home</a></li>
                    <li><a href="/portfolio/">Portfolio</a></li>
                    <li><a href="/contact/">Contact</a></li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
  export default {
    data() {
        let data = {
            name:"octopus",
            url:"Johanna Kraken",
            link:"/"
        }

        return {data:data};
    }
  }
</script>

<style lang="scss" scoped>
    body {
        margin: 0;
    }

    .navbar {
        padding: 15px;
        display: flex;
        flex-flow: row;
        color: $white;
        justify-content: space-between;
    }

    .navbar__background {
        background-color: $primary;
        position: absolute;
        top: 0;
        right: 0;
        left: 0;
        height: 11vh;
        z-index: -1;
    }

    .navbar__header,
    .navbar__list {
        display: flex;
        flex-flow: row;

    }

    .navbar__header {
        grid-column: col-start 1 / span 4;
        text-decoration: none;

        @include for-destop {
            grid-column: col-start 1 / span 2;
        }
    }

    .navbar__list {
        grid-column: col-start 9 / span 3;

        @include for-only-tablet {
            grid-column: col-start 5 / span 6;
            align-items: end;
        }

        @include for-phone {
            grid-column: col-start 5 / span 7;
        }

        & > ul {
            padding: 0;
            display: inline-flex;
        }
    }

    .navbar__header > img {
        width: 40px;
    }

    .navbar__header > span {
        margin: auto 0 auto 15px;
        text-decoration: none;
        color: white;
    }

    .navbar__list > ul > li {
        margin: 0 15px;
    }

    .navbar__list > ul > li > a {
        text-decoration: none;
        color: white;
    }

    .navbar__list > ul > li::marker {
        content: none;
    }

    .navbar__list > ul > li > a:hover {
        text-decoration: underline;
    }
</style>