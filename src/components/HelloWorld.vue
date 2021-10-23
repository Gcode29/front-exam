<template>
  <v-container>
    <v-row class="text-center">
      <v-col>
        <v-text-field label="Event Name" v-model="form.name"> </v-text-field>
        <v-row>
          <v-col cols="12" lg="6">
            <v-text-field type="date" v-model="form.dateFrom" />
          </v-col>
          <v-col cols="12" lg="6">
            <v-text-field type="date" v-model="form.dateTo" />
          </v-col>
        </v-row>

        <v-row>
          <v-col cols="12">
            <v-checkbox label="Monday" value="Mon" v-model="form.days" />
            <v-checkbox label="Tuesday" value="Tue" v-model="form.days" />
            <v-checkbox label="Wednesday" value="Wed" v-model="form.days" />
            <v-checkbox label="Thursday" value="Thu" v-model="form.days" />
            <v-checkbox label="Friday" value="Fri" v-model="form.days" />
            <v-checkbox label="Saturday" value="Sat" v-model="form.days" />
            <v-checkbox label="Sunday" value="Sun" v-model="form.days" />
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <v-btn depressed color="primary" @click="save">
              Save
            </v-btn>
          </v-col>
        </v-row>
      </v-col>

      <v-row>
        <v-col class="mt-4">
          <div>
            <v-sheet height="600">
              <v-calendar
                ref="calendar"
                v-model="value"
                :weekdays="weekday"
                :type="type"
                :events="events"
                :event-overlap-mode="mode"
                :event-overlap-threshold="30"
                @change="getEvents"
              ></v-calendar>
            </v-sheet>
          </div>
        </v-col>
      </v-row>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";

export default {
  name: "HelloWorld",

  data: () => ({
    form: {
      name: null,
      dateFrom: null,
      dateTo: null,
      days: [],
    },
    type: "month",
    types: ["month", "week", "day", "4day"],
    mode: "stack",
    modes: ["stack", "column"],
    weekday: [0, 1, 2, 3, 4, 5, 6],
    weekdays: [
      { text: "Sun - Sat", value: [0, 1, 2, 3, 4, 5, 6] },
      { text: "Mon - Sun", value: [1, 2, 3, 4, 5, 6, 0] },
      { text: "Mon - Fri", value: [1, 2, 3, 4, 5] },
      { text: "Mon, Wed, Fri", value: [1, 3, 5] },
    ],
    value: "",
    events: [],
  }),

  methods: {
    save() {
      const apiUrl = process.env.VUE_APP_API_URL;

      axios.post(`${apiUrl}/api/events`, this.form).then((response) => {
        this.events = response.data;
      });
    },
  },

  async mounted() {
    const apiUrl = process.env.VUE_APP_API_URL;

    await axios.get(`${apiUrl}/api/events`).then((response) => {
      this.events = response.data;
    });
  },
};
</script>
