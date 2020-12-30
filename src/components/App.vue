<template>
 <Page>
   <ActionBar title="NativeScript-Vue Pokedex"/>
   <StackLayout backgroundColor="#3c495e">
     <ListView class="list-group" for="episode in episodes" separatorColor="#e6e6e6" @itemTap="fetchQuote">
       <v-template>
         <FlexboxLayout flexDirection="row" class="list-group-item">
           <Label :text="episode.name" class="list-group-item-heading" style="width: 60%" />
         </FlexboxLayout>
       </v-template>
     </ListView>
   </StackLayout>
 </Page>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      episodes: [],
    };
  },
  methods: {
    fetchQuote() {
      axios({
        method: "GET",
        url: "https://rickandmortyapi.com/api/episode",
      }).then(
        (result) => {
          this.episodes = result.data.results;
        },
        (error) => {
          console.error(error);
        }
      );
    },
  },
  created() {
    this.fetchQuote();
  },
};
</script>

<style scoped>
#quote {
  font-size: 40px;
  text-align: right;
  margin-top: 30%;
  font-weight: bold;
  margin-right: 10px;
  color: white;
}

#author {
  text-align: right;
  font-size: 25px;
  margin-top: 10%;
  margin-right: 3px;
  color: white;
}

.page {
  background-image: url("~/assets/breaking-bad1.jpg");
  background-position: center;
  background-size: cover;
}
</style>