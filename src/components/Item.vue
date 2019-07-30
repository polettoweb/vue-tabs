<template>
    <div>
        <h3>{{item.title}}</h3>
        <p v-show="active">{{item.content}}</p>
        <a @click="toggle(item.id)">{{ active ? 'Reade less' : 'Read more'}}</a>
    </div>
</template>

<script>
export default {
    name: "item",
    props: {
        item: Object
    },
    data() {
        return {
            active: false
        }
    },
    methods: {
        toggle(id) {
            this.$emit("clicked", id)
        }
    }
}
</script>

<style>

</style>
