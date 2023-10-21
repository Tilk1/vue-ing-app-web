<script setup>
import { ref } from 'vue'
import { onBeforeMount } from 'vue';
import WebSiteService from "../services/WebSiteServiceClass.js"

const websites = ref([]);

function getSubtitle(website){
    return `${website.url} | Cada ${website.frecuencia} | ${website.ultima}`
}

const webSiteService = new WebSiteService();

function setWebSites() {
    webSiteService.getWebsites().then(result => {
        websites.value = result;
    }).catch(error => {
        console.error(error);
    });
}

onBeforeMount(() => {
    setWebSites();
})
</script>

<template>
    <v-container fluid>
        <h1>Sitios web registrados</h1>
        <v-sheet width="800" class="mx-auto">
            <v-list>
                <v-list-item
                    v-for="website in websites"
                    :key="website.id"
                    :title="website.nombre"

                >
                <template v-slot:prepend>
                    <v-avatar color="grey-lighten-1">
                        <v-icon color="white">mdi-web</v-icon>
                    </v-avatar>
                </template>
                
                <template v-slot:append>
                    <v-btn
                        color="grey-lighten-1"
                        icon="mdi-cog"
                        variant="text"
                    >
                    <RouterLink :to="{ name: 'detail', params: { id:website.Id }}"><v-icon>mdi-cog</v-icon></RouterLink>
                    </v-btn>
                </template>
                </v-list-item>
            </v-list>
        </v-sheet>
    </v-container>
</template>