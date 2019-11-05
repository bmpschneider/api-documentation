<template>
  <v-container>
    <div id="App">
      <v-app id="inspire">
        <v-form v-model="valid">
          <v-container>
            {{ api }}
            <v-row>
              <v-col cols="12" md="12" sm="6">
                <v-text-field v-model="api.nome" label="nome" required></v-text-field>
              </v-col>

              <v-col cols="12" md="12" sm="6">
                <v-text-field v-model="api.description" label="description" required></v-text-field>
              </v-col>

              <v-col cols="12" md="12" sm="6">
                <v-text-field v-model="api.path" label="path" required></v-text-field>
              </v-col>
              <v-col cols="12" md="12" sm="6">
                <v-select
                  v-model="api.method"
                  :items="methods"
                  label="method"
                  required
                  :menu-props="{ offsetY: true }"
                ></v-select>
              </v-col>
              <v-btn color="yellow" @click="handleConfirm">Confirmar</v-btn>
            </v-row>
          </v-container>
        </v-form>
      </v-app>
    </div>
  </v-container>
</template>

<script>
import { mapMutations } from 'vuex'
export default {
  data: () => ({
    api: {
      nome: '',
      description: '',
      path: '/',
      method: '',
    },
    methods: ['get', 'put', 'post', 'delete'],
  }),
  methods: {
    ...mapMutations('user', ['UPDATE_FORM']),
    handleConfirm() {
      this.$router.push('/about')
      this.UPDATE_FORM(this.api)
    },
  },
}
</script>
