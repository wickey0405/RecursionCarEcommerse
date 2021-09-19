<template>
    <div>
        <select v-model="sortmethod" v-on:click="selectSortMethod" class="form-select" aria-label="Default select example">
            <option value="default">Sort by:</option>
            <option value="Low to High">Price: Low to High</option>
            <option value="High to Low">Price: High to Low</option>
            <option value="Newest Arrivals">Newest Arrivals</option>
        </select>
    </div>
</template>

<script>
export default{
    name: 'sortBox',
    data(){
        return {
            sortmethod: "default"
        }
    },
    methods:{
        selectSortMethod: function(){
            this.$emit('select-sort',this.sortmethod);
        }
    }
}

</script>