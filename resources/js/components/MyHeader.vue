<template>
    <div class="wrapper">
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <a class="navbar-brand" href="#">Rahat!</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarColor02"
                aria-controls="navbarColor02" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarColor02">
                <ul class="navbar-nav mr-auto">
                    <li class="nav-item active">
                        <router-link to="/home" class="navbar-item">Home</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link to="/about" class="navbar-item">About</router-link>
                    </li>

                </ul>

            </div>
        </nav>
        <!-- <div class="bootfatilty">
            <nav class="navbar navbar-expand-lg navbar-light bg-light">
                <a class="navbar-item" href="">
                    Rahat!
                </a>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav mr-auto">
                        <li class="nav-item">
                            <router-link to="/home" class="navbar-item">Home</router-link>
                        </li>

                        <li class="nav-item">
                            <router-link to="/about" class="navbar-item">About</router-link>
                        </li>
                    </ul>

                </div>
            </nav>



        </div>
 -->







        <!--  <nav class="navbar" role="navigation" aria-label="main navigation">
            <div class="navbar-brand">
                <a class="navbar-item" href="">
                    Rahat!
                </a>
                <div class="navbar-menu is-active">

                </div>
                <router-link to="/home" class="navbar-item">Home</router-link>
                <router-link to="/about" class="navbar-item">About</router-link>

                <a role="button" class="navbar-burger" aria-label="menu" aria-expanded="false">
                    <span aria-hidden="true"></span>
                    <span aria-hidden="true"></span>
                    <span aria-hidden="true"></span>
                </a>
            </div>
        </nav> -->
    </div>

</template>
