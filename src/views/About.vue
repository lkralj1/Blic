<template>
  <div class="commit">
    <h1>Detalji knjige</h1>
    <ul>
      <li>Ime autora: {{ commit.commit.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "About",
  props: {
    url: String,
  },

  data() {
    return {
      commit: [],
    };
  },

  created: async function () {
    let get_request = await fetch(
      "https://www.anapioficeandfire.com/api/books" + this.url
    );
    let response = await get_request.json();
    this.commit = response;
    console.log(get_request);
  },
};
</script>
