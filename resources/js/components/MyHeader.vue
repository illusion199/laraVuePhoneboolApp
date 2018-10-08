<template>
    <div class="wrapper">
        <nav class="navbar navbar-expand-lg navbar-light bg-light">

            <a class="navbar-brand" href="#">
                <img src="/img/logo.jpg" alt="Logo" style="width:40px; height:40px;border-radius:10px">
            </a>
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






    </div>

</template>
