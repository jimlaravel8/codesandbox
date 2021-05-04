<template>
  <v-app>
    <v-main>
      <v-layout wrap justified>
        <v-card :loading="loading" class="mx-auto my-12" width="100%">
          <!-- <template slot="progress">
            <v-progress-linear
              color="deep-purple"
              height="10"
              indeterminate
            ></v-progress-linear>
          </template>

          <v-img
            height="250"
            src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
          ></v-img> -->

          <v-card-title> 
            <img src="https://phplaravel-317638-1894522.cloudwaysapps.com/storage/logo/Fts4HFQWoCmyWjP7f5cLG0Acir3DNykuAUhgr3RR.png" alt="" style="width: 200px">
            <v-spacer></v-spacer>
            <div>
              <small>SPEEDBALL COURIER SERVICES LTD</small> <br>
              <small>CUSTOMS CLEARANCE FEES FORM</small>
            </div>
          </v-card-title>

          <v-card-text>
            <table class="table">
              <thead>
                <tr>
                  <th scope="col">#</th>
                  <th scope="col">Date</th>
                  <th scope="col">Client</th>
                  <th scope="col">Weight</th>
                  <th scope="col">Price/KG</th>
                  <th scope="col">Total fees</th>
                  <th scope="col">Clearing company</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(item, index) in columns" :key="index">
                  <th scope="row">{{ index + 1 }}</th>
                  <td>
                    <input type="date" class="form-control" v-model="item.date" />
                  </td>
                  <td>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="Client"
                      v-model="item.client"
                    />
                  </td>

                  <td>
                    <input
                      type="number"
                      class="form-control"
                      placeholder="Weight"
                      v-model="item.weight"
                    />
                  </td>
                  <td>
                    <input
                      type="number"
                      class="form-control"
                      placeholder="price"
                      v-model="item.price"
                    />
                  </td>
                  <td>
                    <input
                      type="number"
                      class="form-control"
                      placeholder="fees"
                      v-model="item.fees"
                    />
                  </td>
                  <td>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="company"
                      v-model="item.company"
                    />
                  </td>
                </tr>
              </tbody>
              <tfoot>
                <tr>
                  <th colspan="5"></th>
                  <th>Total</th>
                  <th>{{total}}</th>
                </tr>
              </tfoot>
            </table>
            <v-btn text color="primary" @click="add_new">
              <v-icon>mdi-add</v-icon>
              Add more
            </v-btn>
            <v-divider></v-divider>
            <div class="form-inline">
              <label for="">I </label>
              <input
                type="text"
                placeholder="Enter your name"
                v-model="form.clearing_person"
              />
              , requests an amount 
              <input
                type="text"
                placeholder="amount"
                v-model="form.clearing_person"
              />
              <label for="">as clearance fee for the above mentioned client. This fee will be fully/partially recovered from the remittance(s) of date(s) </label>
              <input
                type="date"
                v-model="form.date"
              /> and <input
                type="date"
                v-model="form.date"
              />

            </div>
            Requester Signature ...................... <br>
            Approved by ......................
            Sign ...................... <br>
            Authorized by ......................
            Sign ...................... 

          </v-card-text>
        </v-card>
      </v-layout>
    </v-main>
  </v-app>
</template>
<script>
export default {
  data: () => ({
    loading: false,
    selection: 1,
    form: {},

    columns: [
      {
        date: "",
        client: "",
        weight: 0,
        price: 9,
        fees: 0,
        company: "",
      },
    ],
  }),

  methods: {
    add_new() {
      this.columns.push({
        date: "",
        client: "",
        weight: "",
        price: 0,
        fees: 0,
        company: 0,
      });
    },
  },
  computed: {
    total() {
      var total = 0

      this.columns.forEach(element => {
        total += parseFloat(element.fees)
      });

      return total
    }
  }
};
</script>
<style scoped>
/* Style the form - display items horizontally */
.form-inline {
  display: flex;
  flex-flow: row wrap;
  align-items: center;
}

/* Add some margins for each label */
.form-inline label {
  margin: 5px 10px 5px 0;
}

/* Style the input fields */
.form-inline input {
  vertical-align: middle;
  margin: 5px 10px 5px 0;
  padding: 5px;
  background-color: #fff;
  border: 1px solid #ddd;
}

/* Style the submit button */
.form-inline button {
  padding: 10px 20px;
  background-color: dodgerblue;
  border: 1px solid #ddd;
  color: white;
}

.form-inline button:hover {
  background-color: royalblue;
}

/* Add responsiveness - display the form controls vertically instead of horizontally on screens that are less than 800px wide */
@media (max-width: 800px) {
  .form-inline input {
    margin: 10px 0;
  }

  .form-inline {
    flex-direction: column;
    align-items: stretch;
  }
}
</style>
