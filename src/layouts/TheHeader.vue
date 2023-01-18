<template>
    <header>
        <nav class="navbar navbar-expand-lg bg-body-tertiary navbar-dark bg-primary">
            <div class="container-fluid">
                <a class="navbar-brand" href="#">Vue3 Learning</a>
                <button
                    class="navbar-toggler"
                    type="button"
                    data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent"
                    aria-controls="navbarSupportedContent"
                    aria-expanded="false"
                    aria-label="Toggle navigation"
                >
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto">
                        <li class="nav-item">
                            <RouterLink class="nav-link" to="/">Home</RouterLink>
                        </li>
                        <li class="nav-item">
                            <RouterLink class="nav-link" to="/about">About</RouterLink>
                        </li>
                    </ul>
                    <form class="d-flex" role="search" @submit.stop.prevent="searchSubmit()">
                        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" />
                        <button class="btn btn-primary btn-outline-light" type="submit">Search</button>
                    </form>
                </div>
            </div>
        </nav>
    </header>
</template>

<script setup>
function searchSubmit() {
    console.log('Search submitted');
    return;
}
</script>

<style scoped></style>
