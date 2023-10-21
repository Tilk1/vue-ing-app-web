<script setup>
import { ref } from 'vue';
import { onBeforeMount } from 'vue';
import { useRoute } from 'vue-router';
import WebSiteService from '../services/WebSiteServiceClass'

const route = useRoute();

const website = ref({}) //  variable reactiva
const error = ref(false)
const success = ref(false)

function setWebsite(){
    WebSiteService.get(route.params.id).then(
        result => website.value = result
    )
}

onBeforeMount(() => setWebsite())

function deleteWebsite(){
    success.value = false
    error.value = false
    WebSiteService.delete(website.value.id).then(res => {
        success.value = true
        website.value = false
    }).catch(err => {
        error.value = true
    })
}