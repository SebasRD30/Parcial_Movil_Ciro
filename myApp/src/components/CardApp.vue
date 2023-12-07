<template>
    <ion-card>
        <ion-card-header>
            <ion-card-title>Paises de Europa</ion-card-title>
            <ion-card-subtitle>Sebastián Ruiz</ion-card-subtitle>
        </ion-card-header>
        <ion-card-content>
            <ion-list>
                <ion-item v-for="pais in PaisesData" :key="pais.id" class="item">
                    <ion-thumbnail slot="start">
                        <img alt="Silhouette of mountains" src="@/assets/img/banderas.png" />
                    </ion-thumbnail>
                    <ion-label>{{ pais.nombre }}</ion-label>
                    <ion-button @click="verDetalle(pais.id)">Ver Descripcion</ion-button>
                </ion-item>
            </ion-list>
        </ion-card-content>
    </ion-card>
</template>

<script lang="ts">
import { IonList, IonItem, IonButton, IonThumbnail, IonLabel, IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle } from '@ionic/vue';
import { defineComponent } from 'vue';
import Paises from '@/assets/json/Paises.json'
import { useRouter } from 'vue-router';
import { ref } from 'vue';

export default defineComponent({
    components: { IonList, IonItem, IonButton, IonThumbnail, IonLabel, IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle },

    setup() {
        const router = useRouter();

        const verDetalle = (idPais: string) => {
            router.push(`/tabs/tab2/${idPais}`);
        };

        const PaisesData = ref(Paises);

        return { PaisesData, verDetalle };
    },

});

</script>

<style scoped>
ion-item {
    --padding-start: 0;
}

img {
    border-radius: 50%;
    border: 2px solid #000;
}

.item {
    margin-top: 20px;
}
</style>