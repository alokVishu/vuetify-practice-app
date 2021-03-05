<template>
  <v-card>
    <v-card-title>Portfolio</v-card-title>

    <!-- window -->
    <v-window v-model="onboarding" reverse>
      <v-window-item v-for="(data,index) in portfolioData" :key="`card-${index}`">
        <v-card>
          <v-img max-height="400" :src="data.img"></v-img>
          <div class="card-content">
            <v-card-text>
              <p>{{data.desc}}</p>
              <a :href="data.url" class="font-weight-bold">{{data.url}}</a>
            </v-card-text>
          </div>
        </v-card>
      </v-window-item>
    </v-window>

    <!-- card actions -->
    <v-card-actions class="justify-space-between">
      <v-btn text @click="prev">
        <v-icon>mdi-chevron-left</v-icon>
      </v-btn>
      <v-item-group v-model="onboarding" class="text-center" mandatory>
        <v-item
          v-for="(n,index) in portfolioData"
          :key="`btn-${index}`"
          v-slot="{ active, toggle }"
        >
          <v-btn :input-value="active" icon @click="toggle">
            <v-icon>mdi-record</v-icon>
          </v-btn>
        </v-item>
      </v-item-group>
      <v-btn text @click="next">
        <v-icon>mdi-chevron-right</v-icon>
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      /* eslint-disable global-require */
      portfolioData: [
        {
          img: require('@/assets/images/1.jpg'),
          desc:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Non assumenda corporis, accusamus est adipisci labore. Deserunt voluptates aperiam, earum culpa voluptatum minus consequatur quo animi dicta recusandae! Ea, est enim?',
          url: 'www.google.com',
        },
        {
          img: require('@/assets/images/2.jpg'),
          desc:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Non assumenda corporis, accusamus est adipisci labore. Deserunt voluptates aperiam, earum culpa voluptatum minus consequatur quo animi dicta recusandae! Ea, est enim?',
          url: 'www.google.com',
        },
        {
          img: require('@/assets/images/3.jpg'),
          desc:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Non assumenda corporis, accusamus est adipisci labore. Deserunt voluptates aperiam, earum culpa voluptatum minus consequatur quo animi dicta recusandae! Ea, est enim?',
          url: 'www.google.com',
        },
      ],
      onboarding: 0,
    };
  },
  methods: {
    next(): void {
      this.onboarding = this.onboarding + 1 === this.portfolioData.length
        ? 0
        : this.onboarding + 1;
    },
    prev() {
      this.onboarding = this.onboarding - 1 < 0
        ? this.portfolioData.length - 1
        : this.onboarding - 1;
    },
  },
});
</script>

<style lang="scss" scoped>
  .card-content{
    opacity:0;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: grey;
    border-radius: 2px;
    transition: all 0.2s;
    text-align: center;
    align-items: center;
    display: flex;
    &:hover{
      opacity: 1;
      background-color: rgba(58, 77, 85, 0.8);
      transition: all 0.2s;
      font-weight: 700;
      color: white;
    }
  }
</style>
