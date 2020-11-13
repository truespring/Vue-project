<template>
    <div>
        {{ todo }}
        <input type="text" v-model="todo"><button>등록</button>
    </div>
</template>
<script>
export default {
    data() {
        return {
            todo: ''
        }
    }
}
</script>