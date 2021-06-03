<template>
  <v-container>
    <VuetifyDatatable :items="items" />
  </v-container>
</template>

<script>
import BootstrapDatatable from "../components/BootstrapDatatable";
import VuetifyDatatable from "../components/VuetifyDatatable";
export default {
  name: "Home",
  
  components: {
    BootstrapDatatable,
    VuetifyDatatable,
  },
  data: () => {
    return {
      items: [],
      nextUrl: "",
      currentUrl: "",
    };
  },
  methods: {
    fetchData() {
      let req = new Request(this.currentUrl);
      fetch(req)
        .then((resp) => {
          if (resp.status === 200) return resp.json();
        })
        .then((data) => {
          this.nextUrl = data.next;
          data.dataseries.forEach((item) => {
            this.items.push(item);
          });
        })
        .catch((error) => {
          console.log(error);
        });
    },
    next() {
      this.currentUrl = this.nextUrl;
      this.fetchData();
    },

  },
  created() {
      this.currentUrl = 'https://www.7timer.info/bin/astro.php?lon=113.2&lat=23.1&ac=0&unit=metric&output=json&tzshift=0';
      this.fetchData();
    },
};
</script>
