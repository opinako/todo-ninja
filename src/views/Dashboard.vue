<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>

    <v-container class="my-5">

      <v-row class="mb-3">

        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn small flat @click="sortBy('title')" v-bind="attrs" v-on="on" text>
              <v-icon left small>folder</v-icon>
              <span class="caption text-lowercase">By project name</span>
            </v-btn>
          </template>
          <span>Sort projects by project name</span>
        </v-tooltip>

        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn small outlined  v-bind="attrs" v-on="on">
              <v-icon small left>folder</v-icon>
             <span class="text-lowercase caption"> by projects name</span>
            </v-btn>
          </template>
          <span>sort projects by project name</span>
        </v-tooltip>


        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn small flat @click="sortBy('person')" v-bind="attrs" v-on="on">
              <v-icon left small>person</v-icon>
              <span class="caption text-lowercase">By project person</span>
            </v-btn>
          </template>
          <span>Sort projects by person</span>
        </v-tooltip>

      </v-row>

      <v-card flat v-for="project in projects" :key="project.title">
        <v-row :class="`pa-3 project ${project.status}`">
          <v-col cols="12" md="6">
            <div class="caption grey--text">Projects Title</div>
            <div>{{ project.title}}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="caption grey--text">Person</div>
            <div>{{ project.person}}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="caption grey--text">Due by</div>
            <div>{{ project.due }}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="right">
              <v-chip small :color="`${project.status}` " class="caption my-2">
                {{ project.status }}
              </v-chip>
            </div>

          </v-col>
        </v-row>
        <v-divider></v-divider>
      </v-card>

    </v-container>


  </div>
</template>

<script>
  // @ is an alias to /src

  export default {
    data() {
      return {
        projects: [ {
            title: 'Design a new website',
            person: 'The Net Ninja',
            due: '1st Jan 2019',
            status: 'ongoing',
            content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'
          },
          {
            title: 'Code up the homepage',
            person: 'Chun Li',
            due: '10th Jan 2019',
            status: 'complete',
            content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'
          },
          {
            title: 'Design video thumbnails',
            person: 'Ryu',
            due: '20th Dec 2018',
            status: 'complete',
            content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'
          },
          {
            title: 'Create a community forum',
            person: 'Gouken',
            due: '20th Oct 2018',
            status: 'overdue',
            content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'
          },
        ],
        makiko: 'red'
        //   complete:'aqua',
        //   ongoing:'#ffaa2c',
        //   overdue:'#f83e70'
      }
    },
    methods: {
      sortBy( prop ) {
        this.projects.sort( ( a, b ) => a[ prop ] < b[ prop ] ? -1 : 1 )
      }
    }
  }
</script>

<style scoped>
  .project.complete {
    border-left: 4px solid #3cd1c2;
  }

  .project.ongoing {
    border-left: 4px solid orange;
  }

  .project.overdue {
    border-left: 4px solid tomato;
  }

  .v-chip.complete {
    border: 4px solid #3cd1c2;

  }

  .v-chip.ongoing {
    border: 4px solid orange;
    background: orange;
  }

  .v-chip.overdue {
    border: 4px solid tomato;
  }
</style>