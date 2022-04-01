<template>
  <div class="home">
    <ol>
      <li v-for="commit in commits" :key="commit.url">
        <!-- <router-link :to="'/commit_details/' + commit.sha">{{ commit.sha }}</router-link> -->
        <router-link :to="{ name: 'About', params: { url: commit.url } }">{{
          commit.url
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
      commits: [],
    };
  },

  mounted: async function () {
    let get_request = await fetch(
      "https://www.anapioficeandfire.com/api/books"
    );
    let response = await get_request.json();
    this.commits = response;
  },
};
</script>
