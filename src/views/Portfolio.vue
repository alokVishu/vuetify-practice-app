<template>
  <v-container>
    <v-row>
      <v-col xl="9" col="12" class="mx-auto">
        <v-row>
          <!-- small card -->
          <v-col cols="12" sm="6" md="4" lg="3" class="mx-auto">
            <v-card>
              <div class="pa-2">
                <h3>John Doe</h3>
                <span class="subtitle-1 text--secondary">Web developer</span>
              </div>

              <!-- profile image -->
              <v-img src="https://picsum.photos/id/11/500/300"></v-img>

              <!-- timeline -->
              <div>
                <v-timeline dense>
                  <v-timeline-item
                    v-for="timeline in timelineData"
                    :key="timeline.question"
                    icon="mdi-check"
                    color="blue"
                    small
                  >
                    <small>
                      <span class="font-weight-bold mr-1">
                        {{ timeline.question }} :
                      </span>
                      {{ timeline.ans }}
                    </small>
                  </v-timeline-item>
                </v-timeline>
              </div>

              <v-card-actions class="justify-center mt-2">
                <v-btn color="blue" outlined class="mb-2">
                  <v-icon dark>mdi-note-outline</v-icon>
                  Resume / CV
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>

          <!-- details card -->
          <v-col cols="12" md="8" lg="9">
            <v-card class="d-flex align-center flex-wrap flex-sm-nowrap">
              <v-tabs v-model="tab">
                <v-tab>About Me</v-tab>
                <v-tab>Portfolio</v-tab>
                <v-tab>Hire Me</v-tab>
              </v-tabs>
              <div class="d-flex mr-4">
                <v-btn small icon color="error" class="mr-2">
                  <v-icon>mdi-youtube</v-icon>
                </v-btn>
                <v-btn small icon color="blue" class="mr-2">
                  <v-icon>mdi-twitter</v-icon>
                </v-btn>
                <v-btn small icon color="purple" class="mr-2">
                  <v-icon>mdi-github</v-icon>
                </v-btn>
                <v-btn small icon class="mr-2">
                  <v-icon>mdi-instagram</v-icon>
                </v-btn>
              </div>
            </v-card>
            <v-card class="mt-5 py-4 px-10">
              <v-tabs-items v-model="tab">
                <v-tab-item>
                  <about></about>
                </v-tab-item>
                <v-tab-item>
                  <portfolio-slider></portfolio-slider>
                </v-tab-item>
                <v-tab-item>
                  <hire-me></hire-me>
                </v-tab-item>
              </v-tabs-items>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import Vue from 'vue';
import About from './About.vue';
import PortfolioSlider from './PortfolioSlider.vue';
import HireMe from './HireMe.vue';

export default Vue.extend({
  components: {
    About,
    HireMe,
    PortfolioSlider,
  },
  data() {
    return {
      tab: null,
      timelineData: [
        { question: 'Age', ans: 27 },
        { question: 'Availability', ans: 'Full-time' },
        { question: 'Work Experience', ans: '2 years' },
        { question: 'Country  ', ans: 'The Netherlands' },
      ],
    };
  },
});
</script>

<style lang="scss">
</style>
