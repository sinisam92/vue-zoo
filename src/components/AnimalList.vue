<template >
    <div>
        <form @submit.prevent="addAnimal">
            <label>Spicies</label>
            <input v-model="newAnimal.spicies" placeholder="Spicies">
            <label>Name</label>
            <input v-model="newAnimal.name" placeholder="Name">
            <label>Date Of Birth</label>
            <input v-model="newAnimal.dateOfBirth" placeholder="DAte Of Birth">
            <button type="submit">Add Animal</button>
        </form>
        <h3>Sve zivotinje</h3>
        <table border="1"   >
            <thead>
                <td>Spicies</td>
                <td>Name</td>
                <td>Date Of Birth</td>
                
            </thead>
            <tbody>
                <tr v-for="(animal, index) in animals" :key="index">
                    <td>{{animal.spicies}}</td>
                    <td>{{animal.name}}</td>
                    <td v-if="animal.dateOfBirth !== ''">{{animal.dateOfBirth}}</td>
                    <td v-if="animal.dateOfBirth === ''">'Nepoznat'</td>
                    <td>
                    <button @click="removeAnimal(animal)" type="submit">Remove</button>
                    </td>
                    <td>
                    <button @click="moveToTop(animal)" type="submit">Move to top</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newAnimal: {
                spicies: '',
                name: '',
                dateOfBirth: ''
            },
            animals: [
                {spicies: 'Sisar', name: 'Spajk', dateOfBirth: '10 05 2006'},
                {spicies: 'Glodar', name: 'Misko', dateOfBirth: '11 06 2007'},
                {spicies: 'Vodozemac', name: 'Zabra', dateOfBirth: '12 07 2007'},
                {spicies: 'Dinosaurus', name: 'Perodaktil', dateOfBirth: '10 05 2006'},
                {spicies: 'Sisar', name: 'Sinisa', dateOfBirth: '16 08 2016'},
                {spicies: 'Komsija', name: 'Dejan', dateOfBirth: ''}
            ]
            
        }

    },
    methods: {
        removeAnimal(animal) {
            let index = this.animals.indexOf(animal);
            this.animals.splice(index, 1);
        },
        moveToTop(animal) {
            let index = this.animals.indexOf(animal);
            this.animals.splice(index, 1);
            this.animals.unshift(animal);
        },
        addAnimal() {
            this.animals.push(this.newAnimal);
            this.newAnimal = {};
        }
    }
}
</script>

