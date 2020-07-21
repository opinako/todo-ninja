<template>
    <v-dialog v-model="dialog" max-width="600">
        <template v-slot:activator="{ on, attrs }">
            <v-btn color="success" flat v-bind="attrs" v-on="on">
                Add new project
            </v-btn>
        </template>

        <v-card>
            <v-card-title>
                <h2>
                    Add a New Project
                </h2>
            </v-card-title>

            <v-card-text>
                <v-form class="px-3" ref="form">
                    <v-text-field label="Title" v-model="title" prepend-icon="folder" :rules="inputRules"></v-text-field>
                    <v-textarea label="Infomation" v-model="content" prepend-icon="edit" :rules="inputRules"></v-textarea>

                    <v-row>
                        <v-col cols="12" lg="6">
                            <v-menu v-model="menu2" :close-on-content-click="false" max-width="290" >
                                <template v-slot:activator="{ on, attrs }">
                                    <v-text-field :value="computedDateFormattedDatefns" label="Due date" v-bind="attrs" v-on="on" @click:clear="date = null" prepend-icon="date_range" :rules="inputRules"></v-text-field>
                                </template>
                                <v-date-picker v-model="date" @change="menu2 = false"></v-date-picker>
                            </v-menu>
                        </v-col>
                    </v-row>
                    <v-btn flat class="success mx-0 my-3" @click="submit">Add project</v-btn>
                </v-form>
            </v-card-text>

        </v-card>
    </v-dialog>
</template>

<script>
    import {
        format,
        parseISO
    } from 'date-fns'
    export default {
        data() {
            return {
                title: '',
                content: '',
                date: parseISO( new Date().toISOString().substr( 0, 10 ) ),
                menu2: false,
                inputRules: [
                    v => !!v || 'This field is requred',
                    v => v.length >= 3 || 'Minimum length is 3 characters'
                ]
            }
        },
        methods: {
            submit() {
                if ( this.$ref.form.validate() ) {
                    console.log( this.title, this.content )

                }
            }
        },
        computed: {
            computedDateFormattedDatefns() {
                return this.date ? format( this.date, 'EEEE,do MMMM yyyy' ) : ''
            },
        }
    }
</script>

<style>

</style>