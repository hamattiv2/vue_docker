<template>
  <v-navigation-drawer
    v-model="$store.state.drawer"
    absolute
    temporary
    expand-on-hover
    
  >
    <v-list class="pa-1">
      <v-list-tile avatar>
        <v-list-tile-avatar>
          <img v-if="photoUrl" :src="photoUrl"/>
        </v-list-tile-avatar>

        <v-list-tile-content>
          <v-list-tile-title>{{ userName }}</v-list-tile-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>

    <v-list class="pt-0" dense>
      <v-divider></v-divider>

      <v-list-tile v-for="item in items" :key="item.title" :to="item.link">
        <v-list-tile-action>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-tile-action>

        <v-list-tile-content>
          <v-list-tile-title>{{ item.title }}</v-list-tile-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
import { mapGetters } from "vuex"

export default {
  data() {
    return {
      items: [
        {
          title: "連絡先一覧",
          icon: "playlist_add",
          link: { name: "addresses" },
        },
        {
          title: "連絡先追加",
          icon: "playlist_add",
          link: { name: "addresses_edit" },
        },
      ],
    };
  },
  computed: {
    ...mapGetters(["userName", "photoUrl"])
  }
};
</script>