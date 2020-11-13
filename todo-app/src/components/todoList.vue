<template>
    <section>
        <ul>
            <li class="shadow" v-for="item in todoList" :key="item.id">
                <font-awesome-icon class="checkBtn" icon="check" />
                {{ item.todo }}
                <font-awesome-icon class="removeBtn" icon="trash-alt" @click="removeItem(item.id)" />
            </li>
        </ul>
    </section>
</template>
<script>
export default {
    props: ['todoList'],
    methods: {
        removeItem(id) {
            console.log('list id : ' + id)
            this.$emit('removeItem', id)
        }
    }
}
</script>
<style scoped>
ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
}

li {
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background-color: white;
    border-radius: 5px;
}

.checkBtn {
    margin-top: 17px;
    color: #62acde;
    margin-right: 5px;
}

.removeBtn {
    margin-top: 17px;
    margin-left: auto;
    color: #de4343;
}


</style>