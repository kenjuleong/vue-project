<script>
    import Counter from './components/counter.vue';
    import People from './components/people.vue';
    import UseProp from './components/useProp.vue';
    import Layout from './components/baseLayout.vue';
    export default {
    components: {
       Counter, People, UseProp, Layout
    },
    data: () => ({
        character: {
        name: "Joe",
        age: 15
        },
        list: [
       {
        name: 'Annie',
        attack: 25,
        health: 200
       },{
        name: 'Mickey',
        attack: 40,
        health: 100
       },{
        name: 'Minnie',
        attack: 20,
        health: 250
       },{
        name: 'Donald',
        attack: 30,
        health: 180
       }
    ]
    }),
    methods: {
        handleChangeName() {
            this.character.name = this.character.name == "Joe" ? "Mickey" : "Joe"
        },
        changeRealAge(age) {
            this.character.age = age
        }
    }
  }
</script>

<template>
    <Layout>
        <template v-slot:title>Joe Lee</template>
        <template v-slot:description>haha this is joe lee and hello world</template>
    </Layout>
    <UseProp :name="character.name" :age="character.age" @change-name="handleChangeName" @change-realAge="changeRealAge"/>
<Counter :list="list"/>
   <People :list="list"/>
</template>


