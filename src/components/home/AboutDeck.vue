<template>
  <div>
    <h1><span class="info-title">About this deck</span></h1>
    <br>
    <p class="info-text"><b>Elixir Cost:</b> {{ deckElixirCost }}</p>
    <p class="info-text"><b>Deck for Arena:</b> {{ maxArena }}</p>
    <p class="info-text">It uses <b> {{ countCommonCards }} Common <span v-if="(this.countCommonCards == '1')">Card</span><span v-else>Cards</span></b></p>
    <p class="info-text">It uses <b>{{ countRareCards }} Rare <span v-if="(this.countRareCards == '1')">Card</span><span v-else>Cards</span></b></p>
    <p class="info-text">It uses <b>{{ countEpicCards }} Epic <span v-if="(this.countEpicCards == '1')">Card</span><span v-else>Cards</span></b></p>
    <p class="info-text">It uses <b>{{ countLegenCards }} Legendary <span v-if="(this.countLegenCards == '1')">Card</span><span v-else>Cards</span></b></p>
  </div>
</template>
<script>
export default {
  props: ['deck'],
  computed: {
    deckElixirCost() {
      let totalElixir = 0;
      console.log(this.deck);
      this.deck.forEach(function(item, index, arr){
        totalElixir += item.elixirCost;
      });
      return Math.round(totalElixir/8*10)/10;
    },
    maxArena() {
      let arena = 0;
      this.deck.forEach(function(item, index, arr){
        if (item.arena > arena) {
          arena = item.arena;
        }
      });
      return arena;
    },
    countCommonCards() {
      let common = 0;
      this.deck.forEach(function(item,index,arr){
        if (item.rarity == "Common"){
          common += 1;
        }
      });
      return common;
    },
    countRareCards() {
      let rare = 0;
      this.deck.forEach(function(item,index,arr){
        if (item.rarity == "Rare"){
          rare += 1;
        }
      });
      return rare;
    },
    countEpicCards() {
      let epic = 0;
      this.deck.forEach(function(item,index,arr){
        if (item.rarity == "Epic"){
          epic += 1;
        }
      });
      return epic;
    },
    countLegenCards() {
      let legend = 0;
      this.deck.forEach(function(item,index,arr){
        if (item.rarity == "Legendary"){
          legend += 1;
        }
      });
      return legend;
    }
  }
}
</script>
<style>
</style>
