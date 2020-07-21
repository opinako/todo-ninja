<template>

    <div class="team">
        <h1 class="subheading grey--text">Team</h1>

        <v-container class="my-5">
            <v-row>
                <v-col cols="12" sm="6" md="4" lg="3" v-for="person in team" :key="person.name">
                    <v-card flat class="ma-3">
                        <v-responsive class="pt-4">
                            <div align="center">
                                <v-avatar size="100" class="grey lighten-2">
                                    <img :src="person.avatar" alt="キャラの写真">
                                </v-avatar>
                                <v-card-text>
                                    <div class="subheading">{{ person.name }}</div>
                                    <div class="grey--text">{{ person.role}}</div>
                                </v-card-text>
                            </div>
                            <v-card-action>
                                <v-btn color="grey lighten-4">
                                    <v-icon small left>message</v-icon>
                                    <span>Message</span>
                                </v-btn>
                            </v-card-action>
                        </v-responsive>
                    </v-card>
                </v-col>
            </v-row>
        </v-container>

    </div>
</template>

<script>
    export default {
        data() {
            return {
                team: [ {
                        name: 'The Net Ninja',
                        role: 'Web developer',
                        avatar: '/avatar-1.png'
                    },
                    {
                        name: 'Ryu',
                        role: 'Graphic designer',
                        avatar: '/avatar-2.png'
                    },
                    {
                        name: 'Chun Li',
                        role: 'Web developer',
                        avatar: '/avatar-3.png'
                    },
                    {
                        name: 'Gouken',
                        role: 'Social media maverick',
                        avatar: '/avatar-4.png'
                    },
                    {
                        name: 'Yoshi',
                        role: 'Sales guru',
                        avatar: '/avatar-5.png'
                    }
                ]
            }
        }
    }
</script>

<style>
    .center {
        display: flex;
        text-align: center;
    }

</style>