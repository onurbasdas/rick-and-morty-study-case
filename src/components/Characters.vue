<template>
  <Page>
    <ActionBar title="NativeScript-Vue Pokedex" />
    <StackLayout backgroundColor="#3c495e">
      <ListView
        class="list-group"
        separatorColor="#e6e6e6"
        @itemTap="fetchQuote"
        for="episode in episodes"
      >
        <FlexboxLayout flexDirection="row" class="list-group-item">
          <Image class="thumb" />
          <Label
            :text="episode.name"
            class="list-group-item-heading"
            style="width: 60%"
            @tap="goToDetailPage"
          />
        </FlexboxLayout>
      </ListView>
    </StackLayout>
  </Page>
</template>

<script>
export default {
  props: ["id"],
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
};
</script>