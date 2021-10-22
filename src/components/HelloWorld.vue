<template>
  <v-container>
    <v-row class="text-center">
      <v-col>
        <v-text-field
          label="Event Name"
        >
        </v-text-field>
          <v-row>
            <v-col cols="6">
              <v-menu
                ref="menu"
                v-model="menu"
                :close-on-content-click="false"
                :return-value.sync="date"
                transition="scale-transition"
                offset-y
                min-width="auto"
              >
                <template v-slot:activator="{ on, attrs }">
                  <v-text-field
                    v-model="date"
                    label="Picker in menu"
                    prepend-icon="mdi-calendar"
                    readonly
                    v-bind="attrs"
                    v-on="on"
                  ></v-text-field>
                </template>
                <v-date-picker
                  v-model="date"
                  no-title
                  scrollable
                >
                  <v-spacer></v-spacer>
                  <v-btn
                    text
                    color="primary"
                    @click="menu = false"
                  >
                    Cancel
                  </v-btn>
                  <v-btn
                    text
                    color="primary"
                    @click="$refs.menu.save(date)"
                  >
                    OK
                  </v-btn>
                </v-date-picker>
              </v-menu>
            </v-col>
            <v-col cols="6">
              <v-menu
                ref="menu"
                v-model="menu"
                :close-on-content-click="false"
                :return-value.sync="date"
                transition="scale-transition"
                offset-y
                min-width="auto"
              >
                <template v-slot:activator="{ on, attrs }">
                  <v-text-field
                    v-model="date"
                    label="Picker in menu"
                    prepend-icon="mdi-calendar"
                    readonly
                    v-bind="attrs"
                    v-on="on"
                  ></v-text-field>
                </template>
                <v-date-picker
                  v-model="date"
                  no-title
                  scrollable
                >
                  <v-spacer></v-spacer>
                  <v-btn
                    text
                    color="primary"
                    @click="menu = false"
                  >
                    Cancel
                  </v-btn>
                  <v-btn
                    text
                    color="primary"
                    @click="$refs.menu.save(date)"
                  >
                    OK
                  </v-btn>
                </v-date-picker>
              </v-menu>
            </v-col>
          </v-row>

          <v-row>
            <v-col cols="12">
                  <v-radio-group
                    v-model="row"
                    row
                  >
                    <v-radio
                      label="Monday"
                      value="radio-1"
                    ></v-radio>
                    <v-radio
                      label="Tuesday"
                      value="radio-2"
                    ></v-radio>
                    <v-radio
                      label="Wednesday"
                      value="radio-3"
                    ></v-radio>
                    <v-radio
                      label="Thursday"
                      value="radio-4"
                    ></v-radio>
                    <v-radio
                      label="Friday"
                      value="radio-5"
                    ></v-radio>
                    <v-radio
                      label="Saturday"
                      value="radio-6"
                    ></v-radio>
                    <v-radio
                      label="Sunday"
                      value="radio-7"
                    ></v-radio>
                  </v-radio-group>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="12">
              <v-btn
                depressed
                color="primary"
              >
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
                :event-color="getEventColor"
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
  export default {
    name: 'HelloWorld',

    data: () => ({
      ecosystem: [
        {
          text: 'vuetify-loader',
          href: 'https://github.com/vuetifyjs/vuetify-loader',
        },
        {
          text: 'github',
          href: 'https://github.com/vuetifyjs/vuetify',
        },
        {
          text: 'awesome-vuetify',
          href: 'https://github.com/vuetifyjs/awesome-vuetify',
        },
      ],
      importantLinks: [
        {
          text: 'Documentation',
          href: 'https://vuetifyjs.com',
        },
        {
          text: 'Chat',
          href: 'https://community.vuetifyjs.com',
        },
        {
          text: 'Made with Vuetify',
          href: 'https://madewithvuejs.com/vuetify',
        },
        {
          text: 'Twitter',
          href: 'https://twitter.com/vuetifyjs',
        },
        {
          text: 'Articles',
          href: 'https://medium.com/vuetify',
        },
      ],
      whatsNext: [
        {
          text: 'Explore components',
          href: 'https://vuetifyjs.com/components/api-explorer',
        },
        {
          text: 'Select a layout',
          href: 'https://vuetifyjs.com/getting-started/pre-made-layouts',
        },
        {
          text: 'Frequently Asked Questions',
          href: 'https://vuetifyjs.com/getting-started/frequently-asked-questions',
        },
      ],
    }),
  }
</script>
