<script setup>
import { ref } from 'vue';
import { defineProps } from 'vue';

const { produit,handlerAdd} = defineProps(["produit","handlerAdd"]);

const nomProduit = ref('');
const quantite = ref(0);
const photoUrl = ref('');

const ajouterProduit = () => {
  if (!nomProduit.value || !quantite.value || !photoUrl.value) {
    alert('Veuillez remplir tous les champs');
    return;
  }

  // Appeler la fonction handlerAdd avec les données saisies par l'utilisateur
  handlerAdd(nomProduit.value, quantite.value, photoUrl.value);

  // Réinitialiser les champs après l'ajout du produit
  nomProduit.value = '';
  quantite.value = 0;
  photoUrl.value = '';
};
</script>

<template>
  <v-col cols="12">
    <v-card>
      <v-card-title class="text-center">
        <v-container>
          <v-row class="row">
            <v-col cols="12">
              <h3 class="title">Remplir le Frigo</h3>
              <v-text-field v-model="nomProduit" label="Nom du produit" persistent></v-text-field>
              <v-text-field v-model.number="quantite" label="Quantité" persistent></v-text-field>
              <v-text-field v-model="photoUrl" label="URL de la photo" persistent></v-text-field>
              <br>
              <v-btn @click="ajouterProduit" class="v-btn--small btn-add">Ajouter</v-btn>
            </v-col>
          </v-row>
        </v-container>
      </v-card-title>
    </v-card>
  </v-col>
</template>

<style scoped>
.title {
  font-size: 30px;
  font-family: "Times New Roman", Times, serif;
  color: #1c9ee6; 
  text-align: center;
}

.btn-add {
  
  background-color: #007bff; 
  color: white; 
  transition: background-color 0.3s, color 0.3s; 
  text-align: center;
  padding-left: 50px; 
  padding-right: 50px;
}

.btn-add:hover {
  
  background-color: #0056b3; 
  color: #fff; 
}
</style>

