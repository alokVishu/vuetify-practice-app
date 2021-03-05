<template>
  <div class="about">
    <h4 class="blue--text my-4">About Me</h4>
    <p>{{ aboutMe }}</p>

    <!-- expansion panels -->
    <v-expansion-panels flat multiple v-model="panel">

      <!-- services -->
      <v-expansion-panel class="px-0">
        <v-expansion-panel-header color="blue--text" class="font-weight-bold px-0">
          Services
        </v-expansion-panel-header>
        <v-expansion-panel-content class="px-0">
          <v-row class="d-flex">
            <v-col
              v-for="service in servicesData"
              :key="service.img"
              cols="auto"
              class="pl-0"
            >
              <v-card elevation="2" class="pa-4">
                <v-img
                  max-height="80"
                  max-width="80"
                  class="mx-auto my-4"
                  :src="service.img"
                ></v-img>
                <h5>{{ service.title }}</h5>
                <small>{{ service.desc }}</small>
              </v-card>
            </v-col>
          </v-row>
        </v-expansion-panel-content>
      </v-expansion-panel>

      <!-- Skills -->
      <v-expansion-panel>
        <v-expansion-panel-header color="blue--text" class="font-weight-bold px-0">
          Skills
        </v-expansion-panel-header>
        <v-expansion-panel-content>
          <v-row
            align="center"
            v-for="progress in progressData"
            :key="progress.title"
          >
            <v-col cols="12" xl="2" class="pl-0"> {{ progress.title }} </v-col>
            <v-col cols="12" xl="10" class="pl-0">
              <v-progress-linear
                :value="progress.value"
                stream
                buffer-value="0"
                :color="progress.color"
              ></v-progress-linear>
            </v-col>
          </v-row>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      panel: [0, 1],
      aboutMe: `Lorem ipsum dolor, sit amet consectetur adipisicing elit. Exercitationem
      et illum similique modi veniam eum quas pariatur, vel magnam harum
      inventore aperiam labore distinctio ipsa, magni id autem incidunt.
      Voluptatem perferendis, eum asperiores minus nam maiores delectus expedita
      fugit, architecto ad qui nihil modi nisi deleniti, dolorum sunt. Ullam
      quae a, temporibus saepe cumque sit hic tempore id consequuntur
      necessitatibus quas, sunt in accusantium labore fuga similique? Beatae
      molestiae obcaecati facere modi esse dolores maxime numquam ut qui
      deserunt exercitationem possimus dicta consectetur labore ipsum ratione
      dolor ducimus officiis, rerum fuga? Rem tempore corrupti reiciendis
      maxime. Molestias ab similique vitae`,
      progressData: [
        { color: 'blue', value: 90, title: 'HTML' },
        { color: 'red', value: 95, title: 'CSS' },
        { color: 'green', value: 60, title: 'VueJS' },
        { color: 'amber', value: 80, title: 'Vuetify' },
      ],
      /* eslint-disable global-require */
      servicesData: [
        {
          img: require('@/assets/images/online-shopping.svg'),
          title: 'Web Development',
          desc: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit',
        },
        {
          img: require('@/assets/images/checklist.svg'),
          title: 'Branding Identity',
          desc: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit',
        },
        {
          img: require('@/assets/images/paint.svg'),
          title: 'Designing',
          desc: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit',
        },
        {
          img: require('@/assets/images/watch.png'),
          title: 'Designing',
          desc: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit',
        },
      ],
    };
  },
});
</script>
