<template>
  <v-form ref="form" v-model="valid">
    <v-container>
      <v-row>
        <v-col cols="12" md="6">
          <!-- first name -->
          <v-text-field
            v-model="firstName"
            label="First name"
            :rules="nameRules"
            outlined
            required
          ></v-text-field>

          <!-- last name -->
          <v-text-field
            v-model="lastName"
            :rules="lastNameRules"
            label="Last name"
            outlined
            required
          ></v-text-field>

          <!-- email -->
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            outlined
            required
          ></v-text-field>
        </v-col>

        <!-- text area -->
        <v-col cols="12" md="6">
          <v-textarea
            v-model="textarea"
            :rules="textareaRules"
            outlined
            name="input-7-4"
            label="Write your message here.."
            required
          ></v-textarea>

          <!-- button -->
          <v-btn color="success" @click="submitForm">
            <v-icon class="mr-2">mdi-send-outline</v-icon>
            SEND MESSAGE
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      valid: true,
      firstName: '',
      nameRules: [(v: string) => !!v || '*First Name is required'],
      lastName: '',
      lastNameRules: [(v: string) => !!v || '*Last Name is required'],
      email: '',
      emailRules: [
        (v: string) => !!v || '*E-mail is required',
        (v: string) => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      textarea: '',
      textareaRules: [(v: string|number) => !!v || '*Text Area is required'],
    };
  },
  methods: {
    submitForm() {
      (this.$refs.form as Vue & { validate: () => boolean }).validate();
    },
  },
});
</script>
