<template>
    <nav>
        <v-toolbar flat app color="grey lighten-4">
            <!-- <v-app-bar-nav-icon class="red--text" @click="drawer = !drawer" /> -->
            <v-icon color="red" @click="drawer = !drawer">menu</v-icon>

            <v-toolbar-text class="text-uppercase grey--text">

                <span class="font-weight-light">Todo</span>
                <span>Ninja</span>
            </v-toolbar-text>
            <v-spacer></v-spacer>


            <v-menu offset-y>
                <template v-slot:activator="{ on, attrs }">
                    <v-btn color="grey lighten-4 grey--text" v-bind="attrs" v-on="on">
                        <v-icon>expand_more</v-icon>
                        Menu
                    </v-btn>
                </template>
                <v-list>
                    <v-list-item v-for="link in links" :key="link.title" router :to="link.route">
                        <v-list-item-title>{{ link.title }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>

            <v-btn flat color="grey lighten-4 grey--text">
                <span>Sign Out</span>
                <v-icon right>exit_to_app</v-icon>
            </v-btn>
        </v-toolbar>

        <v-navigation-drawer v-model="drawer" app class="primary">

            <div align="center">
                <v-col class="mt-5">
                    <v-avatar size="100">
                        <img src="/avatar-1.png" alt="">
                    </v-avatar>
                    <p class="white--text subheading mt-1">
                        The Net Ninja
                    </p>
                </v-col>

                <v-col class="mt-4 mb-3">
                    <Popup></Popup>
                </v-col>
            </div>

            <v-list>
                <v-list-item-group>
                    <v-list-item v-for="link in links" :key="link.tilte" router :to="link.route">
                        <v-list-item-icon>
                            <v-icon class="white--text">{{ link.icon}}</v-icon>
                        </v-list-item-icon>
                        <v-list-item-content>
                            <v-list-item-title class="white--text">{{ link.title}}</v-list-item-title>
                        </v-list-item-content>
                    </v-list-item>
                </v-list-item-group>
            </v-list>

        </v-navigation-drawer>

    </nav>
</template>

<script>
    import Popup from './Popup'
    export default {
        data() {
            return {
                drawer: false,
                links: [ {
                        icon: 'dashboard',
                        title: 'Dashboard',
                        route: '/'
                    },
                    {
                        icon: 'folder',
                        title: 'My Projects',
                        route: '/projects'
                    },
                    {
                        icon: 'person',
                        title: 'Team',
                        route: '/team'
                    }
                ],
                item: 2
            }
        },
        components: {
            Popup
        }
    }
</script>

<style>

</style>