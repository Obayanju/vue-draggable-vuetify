<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Vuetify</span>
        <span class="font-weight-light">MATERIAL DESIGN</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        flat
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
      >
        <span class="mr-2">Latest Release</span>
      </v-btn>
    </v-toolbar>

    <v-content>
      <v-container>
        <v-layout>
          <v-flex xs6>
            <v-card>
              <v-list>
                <draggable
                  :list="jobs1"
                  group="occupation"
                  :disabled="!enabled"
                  ghost-class="ghost"
                  :move="checkMove"
                  @start="dragging = true"
                  @end="dragging = false"
                >
                  <v-card
                    v-for="job in jobs1"
                    :key="job.title"
                    xs12
                    :color="job.color"
                    dark
                    max-width="400"
                    class="mb-2"
                  >
                    <v-list-tile class="job-card">
                      <v-list-tile-avatar>
                      </v-list-tile-avatar>

                      <v-list-tile-content>
                        <v-list-tile-title>{{ job.title }}</v-list-tile-title>
                        <v-list-tile-sub-title>
                          {{ job.subtitle }}
                        </v-list-tile-sub-title>
                      </v-list-tile-content>

                      <v-card-actions>
                        <v-list-tile class="grow">
                          <v-layout align-center justify-end>
                            <v-btn icon fab>
                              <v-icon class="mr-1">mdi-delete</v-icon>
                            </v-btn>
                          </v-layout>
                        </v-list-tile>
                      </v-card-actions>
                    </v-list-tile>

                    <v-card-text class="text-xs-right"
                      >added {{ job.date_added }} ago</v-card-text
                    >
                  </v-card>
                </draggable>
              </v-list>
            </v-card>
          </v-flex>

          <v-flex xs6>
            <v-card>
              <v-list>
                <draggable
                  :list="jobs2"
                  group="occupation"
                  :disabled="!enabled"
                  ghost-class="ghost"
                  :move="checkMove"
                  @start="dragging = true"
                  @end="dragging = false"
                >
                  <v-card
                    v-for="job in jobs2"
                    :key="job.title"
                    xs12
                    :color="job.color"
                    dark
                    max-width="400"
                    class="mb-2"
                  >
                    <v-list-tile class="job-card">
                      <v-list-tile-avatar></v-list-tile-avatar>

                      <v-list-tile-content>
                        <v-list-tile-title>{{ job.title }}</v-list-tile-title>
                        <v-list-tile-sub-title>
                          {{ job.subtitle }}
                        </v-list-tile-sub-title>
                      </v-list-tile-content>

                      <v-card-actions>
                        <v-list-tile class="grow">
                          <v-layout align-center justify-end>
                            <v-btn icon fab>
                              <v-icon class="mr-1">mdi-delete</v-icon>
                            </v-btn>
                          </v-layout>
                        </v-list-tile>
                      </v-card-actions>
                    </v-list-tile>

                    <v-card-text class="text-xs-right"
                      >added {{ job.date_added }} ago</v-card-text
                    >
                  </v-card>
                </draggable>
              </v-list>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>

    <div>
      <v-btn color="info" @click="add">Add</v-btn>
      <v-btn color="info" @click="replace">Replace</v-btn>
    </div>
  </v-app>
</template>

<script>
// import HelloWorld from "./components/HelloWorld";
import draggable from "vuedraggable";

export default {
  name: "App",
  components: {
    draggable
  },
  data() {
    return {
      enabled: true,
      dragging: false,
      damis: 1,
      jobs1: [
        {
          color: "green",
          title: "Google",
          subtitle: "Product Manager",
          date_added: "2 Years",
          image: "./assets/logo.svg"
        },
        {
          color: "blue",
          title: "Twitter",
          subtitle: "Product Manager",
          date_added: "2 Years",
          image: "./assets/logo.svg"
        },
        {
          color: "yellow",
          title: "WeWork",
          subtitle: "Product Manager",
          date_added: "2 Years",
          image: "./assets/logo.svg"
        },
        {
          color: "purple",
          title: "Weave",
          subtitle: "Product Manager",
          date_added: "2 Years",
          image: "./assets/logo.svg"
        }
      ],
      jobs2: [
        {
          color: "indigo",
          title: "We Work",
          subtitle: "SWE Intern",
          date_added: "1 Year",
          image: "./assets/logo.svg"
        },
        {
          color: "purple",
          title: "Hashcorp",
          subtitle: "Backend Engineer",
          date_added: "2 Years",
          image: "./assets/logo.svg"
        },
        {
          color: "black",
          title: "Postmates",
          subtitle: "Product Manager",
          date_added: "2 Years",
          image: "./assets/logo.svg"
        }
      ],
      items: [
        {
          icon: true,
          title: "Jason Oner",
          avatar: "https://cdn.vuetifyjs.com/images/lists/1.jpg"
        },
        {
          title: "Travis Howard",
          avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg"
        },
        {
          title: "Ali Connors",
          avatar: "https://cdn.vuetifyjs.com/images/lists/3.jpg"
        },
        {
          title: "Cindy Baker",
          avatar: "https://cdn.vuetifyjs.com/images/lists/4.jpg"
        }
      ]
    };
  },

  methods: {
    add() {
      const imgLink = "https://cdn.vuetifyjs.com/images/lists/5.jpg";
      this.items.push({
        title: `Damilare Obayanju ${this.damis}`,
        avatar: imgLink
      });
      this.damis++;
    },
    replace() {
      const imgLink = "https://cdn.vuetifyjs.com/images/lists/3.jpg";
      this.items = [
        {
          title: "King Kong",
          avatar: imgLink
        }
      ];
    },
    checkMove(e) {
      window.console.log(`Future index: ${e.draggedContext.futureIndex}`);
    }
  }
};
</script>

<style scoped>
.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}
</style>
