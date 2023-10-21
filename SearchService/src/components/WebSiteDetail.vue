<script setup>
import { ref } from 'vue';
import { onBeforeMount } from 'vue';
import { useRoute } from 'vue-router';
import webSiteService from "../services/webSiteService.js"

const route = useRoute();

const website = ref({}) //  variable reactiva
const error = ref(false)
const success = ref(false)

function setWebsite() {
    webSiteService.get(route.params.id).then(
        result => website.value = result
    )
}

onBeforeMount(() => setWebsite())

function deleteWebsite() {
    success.value = false
    error.value = false
    webSiteService.delete(website.value.id).then(res => {
        success.value = true
        website.value = false
    }).catch(err => {
        error.value = true
    })
}

</script>

<template>
    <v-form>
        <v-container>
            <v-row>
                <v-col cols="12">
                    <v-card>
                        <v-card-title class="headline">{{ website.nombre }}</v-card-title>
                        <v-card-text>
                            <v-form>
                                <v-container>
                                    <v-row>
                                        <v-col cols="12" sm="6">
                                            <v-text-field label="URL" v-model="website.URL"></v-text-field>
                                        </v-col>

                                        <v-col cols="12" sm="6">
                                            <v-text-field label="Profundidad de hojas"
                                                v-model="website.profundidad_hojas"></v-text-field>
                                        </v-col>

                                        <v-col cols="12" sm="6">
                                            <v-text-field label="Frecuencia" v-model="website.frecuencia"></v-text-field>
                                        </v-col>

                                        <v-col cols="12" sm="6">
                                            <v-text-field label="Dominios válidos"
                                                v-model="website.max_retrys"></v-text-field>
                                        </v-col>

                                        <v-col cols="12" sm="6">
                                            <v-text-field label="Máximo de intentos fallidos"
                                                v-model="website.max_retrys"></v-text-field>
                                        </v-col>

                                        <v-col cols="12" sm="6">
                                            <v-text-field label="Tiempo de espera máximo"
                                                v-model="website.timeout"></v-text-field>
                                        </v-col>
                                    </v-row>
                                </v-container>
                            </v-form>
                        </v-card-text>
                        <v-card-actions>
                            <v-btn color="error" @click="deleteWebsite">Eliminar</v-btn>
                            <v-btn color="primary" to="/edit">Editar</v-btn>
                        </v-card-actions>
                    </v-card>
                </v-col>
            </v-row>
        </v-container>
    </v-form>
</template>

  
<script>
export default {
    data() {
        return {
            website: {
                URL: '',
                profundidad_hojas: '',
                frecuencia: '',
                max_retrys: '',
                timeout: '',
            },
        };
    },
};
</script>

  