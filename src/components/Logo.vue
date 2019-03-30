<template>
    <v-container bg fill-height text-xs-center>
        <v-layout align-center justify-center wrap column>
            <v-flex xs1>

                <p class="display-3 logo">{{title}}</p>

                <p class="subheading">{{smallMsg}}</p>

                <v-tooltip bottom v-for="link in orderedLinks" :key="link.order">
                    <template v-slot:activator="{ on }">
                        <v-btn fab flat v-on="on" :href="link.href" target="_blank">
                            <font-awesome-icon class="display-1" :icon="link.icon"/>
                        </v-btn>
                    </template>
                    <span>{{link.tooltip}}</span>
                </v-tooltip>

            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
    export default {
        name: "Logo",
        data () {
            return {
                title: 'Mina Moghaddam',
                smallMsg: 'This is empty for now but the wheels are in motion',
                links: [
                    {
                        order: 5,
                        icon: ['fas', 'envelope'],
                        tooltip: 'mina.moghaddam90@gmail.com',
                        href: 'mailto:mina.moghaddam90@gmail.com'
                    },
                    {
                        order: 1,
                        icon: ['fab', 'github'],
                        tooltip: '/MinaMoghaddam',
                        href: 'http://github.com/MinaMoghaddam'
                    },
                    {
                        order: 4,
                        icon: ['fab', 'instagram'],
                        tooltip: '@mina.moghaddam90',
                        href: 'http://instagram.com/mina.moghaddam90'
                    }
                ]
            }
        },
        computed: {
            orderedLinks () {
                return this.links.slice().sort((a,b) => {
                    return a.order > b.order ? 1 : -1
                })
            }
        }
    }
</script>

<style scoped>
    .logo {
        font-family: 'Satisfy', cursive !important;
    }
</style>