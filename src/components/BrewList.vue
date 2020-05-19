<template>
    <div class="card brew-list">
        <ul class="list-group list-group-flush">
            <li class="list-group-item"
                :key='index'
                v-for="(brew, index) in brews"

            >{{brew.name}}, {{brew.state}}
            </li>

        </ul>
    </div>
</template>

<script>
    export default {
        name: "BrewList",
        props: {
            brews: Array
        }
    }
</script>

<style lang="scss" scoped>
    .brew-list {
        overflow-y: scroll;
        height: 93vh;

        li {
            &:hover {
                background-color: darkgrey;
            }
        }
    }
</style>