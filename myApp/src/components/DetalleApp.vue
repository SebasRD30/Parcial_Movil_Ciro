<template>
  <ion-card color="primary" v-if="pais">
    <ion-card-header>
      <ion-card-title>{{ pais.nombre }}</ion-card-title>
    </ion-card-header>

    <ion-card-content>{{ pais.descripcion }}</ion-card-content>
  </ion-card>
</template>
  
<script lang="ts">
import { IonCard, IonCardContent, IonCardHeader, IonCardTitle } from '@ionic/vue';
import { defineComponent } from 'vue';
import { useRoute } from 'vue-router';
import Paises from '@/assets/json/Paises.json'
import { ref } from 'vue';
import { onMounted } from 'vue';

export default defineComponent({
  components: { IonCard, IonCardContent, IonCardHeader, IonCardTitle },

  setup() {
    const route = useRoute();
    const paisId = route.params.id;
    const pais = ref();

    const buscarPaisPorId = () => {
      // Puedes ajustar esta lógica según la estructura de tu array de países
      pais.value = Paises.find(p => p.id === paisId);
    };

    // Llama a la función cuando el componente se ha montado
    onMounted(() => {
      buscarPaisPorId();
    });

    return { pais };
  },
});
</script>