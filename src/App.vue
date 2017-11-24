<template>
    <div id="app">
        <p>{{ doneTodos }}</p>
        <p>{{count}}</p>
        <p id="p1">
            <button @click="add">+</button>
            <button @click="reduce">-</button>
        </p>
        <p>666</p>
    </div>

</template>

<script>
        import { mapState } from 'vuex'
        import { mapGetters } from 'vuex'
        import { mapMutations } from 'vuex'
    export default {
        data(){
          return {
              msg:5
          }
        },
        computed: {
            localComputed() {
            },
            ...mapState({
                count(store) {
                    return store.count
                }
            }),
            ...mapGetters([
                "doneTodos"
            ])
        }
        ,
        methods: {
            ...mapMutations(["increment","decrement"]),
            ...mapMutations({
                add: 'increment' // 将 `this.add()` 映射为 `this.$store.commit('increment')`
                ,reduce:"decrement"
            })
        }
    }
</script>

<style type="text/scss" lang="scss">
    $color:yellow;
    #p1{
        color: red;
        &+p{
            color: $color
        }
    }
</style>

