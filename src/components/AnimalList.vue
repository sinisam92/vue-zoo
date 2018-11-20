<template >
    <div class="container">
        
        <form @submit.prevent="addAnimal" class="form-group">
            <label>Spicies</label><br>
            <input v-model="newAnimal.spicies" placeholder="Spicies"><br>
            <label>Name</label><br>
            <input v-model="newAnimal.name" placeholder="Name"><br>
            <label>Date Of Birth</label><br>
            <input v-model="newAnimal.dateOfBirth" placeholder="DAte Of Birth"><br>

            <select v-model="newAnimal.sector"><br>
                <option disabled value="">Please select one</option><br>
                <option v-for="(sector, index) in sectors" :key="index" :value="sector">{{sector.name}}</option>
             
            </select>
            
            <button type="submit" class="btn btn-primary">Add Animal</button><br>
        </form>
        <h3>Sve zivotinje</h3>
        <table border="1">
            <thead>
                <td>Spicies</td>
                <td>Name</td>
                <td>Date Of Birth</td>
                <td>Sector</td>
                
            </thead>
            <tbody>
                <tr v-for="(animal, index) in animals" :key="index">
                    <td>{{animal.spicies}}</td>
                    <td>{{animal.name}}</td>
                    <td v-if="animal.dateOfBirth">{{animal.dateOfBirth}}</td>
                    <td v-if="!animal.dateOfBirth">'Nepoznat'</td>
                    <td>{{animal.sector.name}}</td>
                    <td>
                    <button @click="removeAnimal(animal)" type="submit">Remove</button>
                    </td>
                    <td>
                    <button @click="moveToTop(animal)" type="submit">Move to top</button>
                    </td>
                </tr>
            </tbody>
        </table>
        <table border="1">
            <thead>
                <td>Name</td>
                <td>Surface</td>
            </thead>
            <tbody>
                <tr v-for="(sector, index) in sectors" :key="index">
                    <td>{{sector.name}}</td>
                    <td>{{sector.surface}}</td>
                    <td>
                        <button @click="showAnimals(sector)" type="submit">Vidi Zivotinje</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
const sectors = [
    {name:'Water-animals', surface: 'Water'},
    {name:'Air-animals', surface: 'Air'},
    {name:'Dinosaurusi', surface: 'All-around'}
    
]
export default {
    data() {
        return {
            sectors: sectors,
            newAnimal: {},
            animals: [
                {spicies: 'Sisar', name: 'Spajk', dateOfBirth: '10 05 2006', sector:sectors[0]},
                {spicies: 'Glodar', name: 'Misko', dateOfBirth: '11 06 2007', sector:sectors[1]},
                {spicies: 'Vodozemac', name: 'Zabra', dateOfBirth: '12 07 2007', sector:sectors[0]},
                {spicies: 'Dinosaurus', name: 'Perodaktil', dateOfBirth: '10 05 2006', sector:sectors[2]},
                {spicies: 'Sisar', name: 'Sinisa', dateOfBirth: '16 08 2016', sector:sectors[1]},
                {spicies: 'Komsija', name: 'Dejan', dateOfBirth: '', sector:sectors[0]}
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
            console.log(this.newAnimal);
            
            this.animals.push(this.newAnimal);
            this.newAnimal = {dateOfBirth: ''};
        },
        showAnimals(sector) {
            let animals = [];
           this.animals.forEach((currentAnimal) => {
            if(currentAnimal.sector == sector){

                    animals.push(currentAnimal.name);  
               }    
                
           });
           alert(animals);  
          
        }
    }
}
</script>

