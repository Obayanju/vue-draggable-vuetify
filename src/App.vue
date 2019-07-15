<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Vuetify</span>
        <span class="font-weight-light">MATERIAL DESIGN</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn flat href="https://github.com/vuetifyjs/vuetify/releases/latest" target="_blank">
        <span class="mr-2">Latest Release</span>
      </v-btn>
    </v-toolbar>

    <v-content>
      <v-card>
        <v-list>
          <draggable
            :list="items"
            :disabled="!enabled"
            ghost-class="ghost"
            :move="checkMove"
            @start="dragging = true"
            @end="dragging = false"
          >
            <v-list-tile v-for="item in items" :key="item.title" avatark>
              <v-list-tile-content>
                <v-list-tile-title v-text="item.title"></v-list-tile-title>
              </v-list-tile-content>

              <v-list-tile-avatar>
                <img :src="item.avatar" />
              </v-list-tile-avatar>
            </v-list-tile>
          </draggable>
        </v-list>
      </v-card>

      <div>
        <v-btn color="info" @click="add">Add</v-btn>
        <v-btn color="info" @click="replace">Replace</v-btn>
      </div>
    </v-content>
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
    add: function() {
      const imgLink = "https://cdn.vuetifyjs.com/images/lists/5.jpg";
      this.items.push({
        title: `Damilare Obayanju ${this.damis}`,
        avatar: imgLink
      });
      this.damis++;
    },
    replace: function() {
      const imgLink = "https://cdn.vuetifyjs.com/images/lists/3.jpg";
      this.items = [
        {
          title: "King Kong",
          avatar: imgLink
        }
      ];
    },
    checkMove: function(e) {
      window.console.log("Future index: " + e.draggedContext.futureIndex);
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
