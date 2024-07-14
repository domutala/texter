<script lang="ts" setup>
import cText from "~/components/text.vue";
import { Swiper as TSwiper } from "swiper";

const _swiper = ref<TSwiper>();
const texts = [
  {
    title: "Le Télétravail : Flexibilité et Durabilité",
    author: "Mamadou Diop",
    date: "2024-07-14T08:00:00",
    content:
      "Découvrez comment le télétravail améliore l'équilibre vie professionnelle/personnelle tout en réduisant notre empreinte carbone. 🌍💼",
  },
  {
    title: "Boostez Votre Productivité avec Ces Conseils Pratiques",
    author: "Aminata Sow",
    date: "2024-07-14T09:30:00",
    content:
      "Établissez des **priorités**, utilisez des outils de gestion de tâches, et adoptez la méthode [Pomodoro](https://fr.wikipedia.org/wiki/Technique_Pomodoro) pour optimiser votre efficacité au quotidien. 📈👩‍💻",
  },
  {
    title: "Savourez la Cuisine Végétarienne : Santé et Gourmandise",
    author: "Fatou Ndiaye",
    date: "2024-07-14T10:45:00",
    content:
      "Explorez des recettes innovantes pour intégrer plus de légumes, légumineuses, et grains entiers dans votre alimentation pour une santé optimale. 🥗🍽️",
  },
  {
    title: "Échappées Secrètes sur la Côte d'Azur : Plages de Rêve",
    author: "Cheikh Fall",
    date: "2024-07-14T12:00:00",
    content:
      "Découvrez des plages cachées comme [l'Escalet à Ramatuelle](https://www.ramatuelle-tourisme.com/fr/decouvrir/les-plages) et la crique de Mala à Cap d'Ail pour une escapade tranquille. 🌊☀️",
  },
  {
    title: "Méditation Quotidienne : Réduisez le Stress, Augmentez la Clarté",
    author: "Awa Diallo",
    date: "2024-07-14T14:15:00",
    content:
      "Apprenez comment quelques minutes de méditation par jour peuvent transformer votre bien-être mental et émotionnel. 🧘‍♀️🌿",
  },
  {
    title: "Créez Votre Jardin Écologique : Pour un Environnement Sain",
    author: "Ousmane Camara",
    date: "2024-07-14T15:45:00",
    content:
      "Explorez des conseils pour créer un jardin écologique qui attire les pollinisateurs et contribue à la biodiversité locale. 🌱🦋",
  },
  {
    title: "Voyagez Écoresponsablement : Découvrez et Protégez",
    author: "Mariama Ba",
    date: "2024-07-14T17:00:00",
    content:
      "Apprenez comment voyager tout en réduisant votre impact environnemental et en soutenant les communautés locales. 🌍🌴",
  },
  {
    title: "Sommeil Réparateur : Clé pour une Santé Optimale",
    author: "Mamadou Sarr",
    date: "2024-07-14T18:30:00",
    content:
      "Découvrez l'importance du sommeil pour la régénération physique et mentale, avec des conseils pour améliorer votre routine de sommeil. 😴🌙",
  },
];
</script>

<template>
  <div style="height: 100px"></div>
  <Swiper
    :modules="[SwiperKeyboard, SwiperNavigation]"
    :spaceBetween="30"
    :centeredSlides="true"
    :keyboard="{ enabled: true }"
    :cssMode="true"
    slides-per-view="auto"
    style="width: 100%; height: calc(100% - 100px)"
    @init="(slide) => (_swiper = slide)"
    @slide-change="() => $router.push(`/?text=${_swiper?.activeIndex}`)"
  >
    <SwiperSlide v-for="(text, t) in texts" :key="t" style="width: 400px">
      <div style="height: 100%; display: flex">
        <div style="height: calc(100% - 50px); width: 100%; margin: auto">
          <c-text :text="text" :active="_swiper?.activeIndex === t" />
        </div>
      </div>
    </SwiperSlide>
  </Swiper>
</template>
