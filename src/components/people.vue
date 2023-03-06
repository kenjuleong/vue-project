<script>
    import List from './peopleList.vue';
    import Button from './button.vue';

    export default {
        components: {
            List, Button
        },
        props: {
            list: {
                type: Array,
                required: true
            }
        },
        data() {
      return {
        name: null,
        health: null,
        attack: null
      }
    },
    computed: {
      averageAttack() {
        return this.list.map(r=>r.attack).reduce((partialSum, a) => partialSum + a, 0) / this.list.length;
      }
    },
    methods: {
      addPeople() {
        if(this.name && this.health && this.attack) {
          this.list.push({
          name: this.name, health: this.health, attack: this.attack
        })
        this.name = null;
        this.health = null;
        this.attack = null;
      }
    },
      deletePeople(name) {
        this.list.splice(this.list.indexOf(this.list.find(i => i.name == name)), 1)
      }
    }
    }
</script>

<template>
    <p>{{ name ? name : 'Unknown' }} has {{ attack ? attack : 0 }} attack & {{ health ? health : 0 }} health</p>
    Name: <input type="text" placeholder="Enter name" v-model="name"><br>
    Attack: <input type="number" placeholder="0" v-model="attack"><br>
    Health: <input type="number" placeholder="0" v-model="health">
    <Button @click="addPeople">Add</Button><br>
    <span v-if="list.length < 1">
        There are no people
    </span>
    <ul v-else>
      <li v-for="(i, index) in list">
        <List :i="i" :index="index" @delete-people="deletePeople"/>
    </li>
    </ul>
    <p>Average Attack: {{ averageAttack }}</p>
    <p>Average Health: {{ list.map(r=>r.health).reduce((partialSum, a) => partialSum + a, 0) / list.length }}</p>
</template>