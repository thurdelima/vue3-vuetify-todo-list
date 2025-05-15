<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer">
      <v-img
        class="pt-2"
        cover
        gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"
        height="80"
        src="https://picsum.photos/1920/1080?random"
      >
        <v-list>
          <v-list-item
            prepend-avatar="https://avataaars.io/?avatarStyle=Circle&topType=ShortHairShortRound&accessoriesType=Blank&hairColor=BrownDark&facialHairType=Blank&clotheType=BlazerShirt&eyeType=Default&eyebrowType=Default&mouthType=Default&skinColor=Light"
            subtitle="Todo list"
            title="Arthur Lima"
          >
          </v-list-item>
        </v-list>
      </v-img>

      <v-divider></v-divider>

      <v-list density="compact" :lines="false" nav>
        <RouterLink v-for="(item, i) in items" :key="i" :to="item.to">
          <v-list-item color="primary" :value="item">
            <template v-slot:prepend>
              <v-icon :icon="item.icon"></v-icon>
            </template>

            <v-list-item-title :textContent="item.text"></v-list-item-title>
          </v-list-item>
        </RouterLink>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      color="teal-darken-4"
      density="prominent"
      image="https://picsum.photos/1920/1080?random"
    >
      <template v-slot:image>
        <v-img
          gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"
        ></v-img>
      </template>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>Todo list</v-app-bar-title>
    </v-app-bar>

    <v-main>
      <!--  -->
      <!-- <v-main> -->
      <router-view />
      <!-- </v-main> -->
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref } from "vue";

  const drawer = ref(null);

  const items = [
    { text: "Home", icon: "mdi-folder", to: "/Home" },
    { text: "About", icon: "mdi-account-multiple", to: "/About" },
  ];
</script>

<style scoped>
a {
  text-decoration: none;
  color: #505050;
}
</style>
