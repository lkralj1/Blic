<template>
  <div class="home">
    <ol>
      <li v-for="knjiga in knjige" :key="knjige.url">
        <router-link :to="{ name: 'About', params: { url: knjiga.url } }">{{
          knjiga.url
        }}</router-link>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      knjige: [],
    };
  },

  mounted: async function () {
    let get_request = await fetch(
      "https://www.anapioficeandfire.com/api/books"
    );
    let response = await get_request.json();
    this.knjige = response;
  },
};
</script>
