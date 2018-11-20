<template >
    <div>
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
                    
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    data() {
        return {
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

    }
}
</script>

