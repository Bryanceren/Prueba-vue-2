<template>
  <v-app>
    <v-main>
      <v-container>
        <h2>Vuetify Table</h2>
        <v-row>
          <v-col md="3">
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search"
              single-line
              show-select
              hide-details
            ></v-text-field>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-data-table
              :headers="headers"
              :items="items"
              item-key="name"
              :items-per-page="5"
              :search="search"
              class="elevation-1"
            ><template v-slot:[`item.actions`]="{ item }">
                <v-icon small @click="showItem(item)">mdi-eye</v-icon>
              </template>
              <template v-slot:[`body.append`]>
                <tr>
                  <td>
                    <v-text-field
                      v-model="seeing"
                      type="number"
                      label="Filtro por seeing"
                    ></v-text-field>
                  </td>
                  <td><v-select
                      v-model="enabled"
                      :items="items.seeing"
                      label="Slot"
                      clearable
                    ></v-select>   
                  </td>
                </tr>
              </template>
              
              
              

                         

            </v-data-table>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  props: ["items"],
  data () {
      return {
        search: '',
        seeing: '',
        items: this.items,
        
      }
    },
  computed: {
    headers() {
      return [
        {
          text: "seeing",
          value: "seeing",
          align: "start",
          sortable: false,
          filter: value => {
            if (!this.seeing) return true;

            return value == parseInt(this.seeing);
          },
        },
        {text: "transparency",value: "transparency"},
        { text: "lifted index", value: "lifted_index" },
        { text: "wind", value: "wind10m.direction" },
        { text: "Actions", value: "actions", sortable: false },
      ];
    },
  },
  methods: {
    showItem(item) {
      this.$router.push({
        path: "/about",
        query: {
          transparency: item.transparency,
          wind: item.wind,
          type: item.prec_type,
        },
      });
    },
    columnValueList(val) {
				return this.items.map((d) => d[val]);
			},
  },
};
</script>
