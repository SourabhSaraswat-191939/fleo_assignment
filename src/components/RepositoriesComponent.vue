<template>
  <div>
    <v-card class="events-heading"> Github Repositories </v-card>
    <v-div >
      <center>
        <v-select
          :items="sortStar"
          label="Sort By Star"
          @change="sortByStar"
          style="width:20%; float:left;margin-left:25%;"
          solo
        ></v-select>
        <v-select
          :items="sortName"
          label="Sort By Name"
          @change="sortByName"
          style="width:20%;"
          solo
        ></v-select>
      </center>
    </v-div>
    <center>
      <v-card class="mx-20 main_card mb-10">
        <v-card
          v-for="(repo, i) in repoData"
          :key="i"
          class="inner_card"
          max-width="300"
          min-width="250"
          :href="repo.html_url"
          :hover="true"
        >
          <v-img
            class="white--text align-end"
            height="200px"
            src="../assets/github_icon.jpg"
          >
          
          </v-img>

          <v-card-text class="text--primary">
            <div>
              <b>{{ repo.name }}</b>
            </div>
            <div><b>Language </b> : {{ repo.language }}</div>
            <div>{{ repo.description }}</div>
          </v-card-text>

          <v-card-actions>
            <v-icon color="orange">mdi-star</v-icon>
            {{ repo.stargazers_count }} <v-icon>mdi-git</v-icon>
            {{ repo.fork ? repo.fork : 0 }} Forks
            <div style="flex: 2">
              <b>by</b> <span id="owner">{{ repo.owner.login }}</span>
            </div>
          </v-card-actions>
        </v-card>
        
      </v-card>

<v-div class="mb-10">
  <v-text-field
      label="Enter Page Size For Next Request"
      hide-details="auto"
       style="width:20%; float:left;margin-left:25%;"
      v-model="pageSize"
    ></v-text-field>
    <v-btn :disabled="counter<1" @click="newData(counter-1)">Prev</v-btn>
    {{counter}}
    <v-btn @click="newData(counter+1)">Next</v-btn>
</v-div>
    </center>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      counter:1,
      pageSize:10,
      repoData: null,
      sortStar: ["Ascending", "Descending"],
      sortName: ["Alphabetically", "Reverse Alphabetically"],
    };
  },
  components: {},
  beforeMount() {
    this.newData(1);
  },
  methods: {
    newData(count){
      this.counter=count;
      axios
      .get(
        "https://api.github.com/search/repositories?q=language:Javascript&sort=stars&order=desc&page=1" +this.counter+
          "&per_page="+this.pageSize
      )
      .then((data) => {
        this.repoData = data["data"]["items"];
      })
      .catch((err) => console.log(err));
    },
    sortByStar(e) {
      this.repoData.sort(function (a, b) {
        if (e == "Ascending") {
          return a.stargazers_count - b.stargazers_count;
        } else {
          return b.stargazers_count - a.stargazers_count;
        }
      });
      console.log(this.repoData);
    },
    sortByName(e) {
      this.repoData.sort(function (a, b) {
        return a.name.localeCompare(b.name);
      });
      if (e == "Reverse Alphabetically") {
        this.repoData = this.repoData.reverse();
      }
    },
  },
};
</script>


<style scoped>
#owner {
  color: rgb(254, 156, 173);
  font-family: fantasy;
  font-weight: 800;
}

.events-heading {
  margin: 20px;
  text-align: center;
  font-size: 4em;
  font-weight: 700;
}

.main_card {
  display: flex;
  align-content: center;
  justify-content: center;
  flex-direction: row;
  flex-wrap: wrap;
  background-image: linear-gradient(to right, #c6ffdd, #fbd786, #f7797d);
}
.inner_card {
  margin: 5%;
}
</style>