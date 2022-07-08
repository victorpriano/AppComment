<template>
<div>
    <div class="container">
        <h1>App de comentários</h1>
        <hr />
        <FormTodo v-on:add-comment="addComment" />
        <br />
        <p v-if="comments.length <= 0">Sem comentários...</p>
        <div v-else class="list-group" v-for="(comment, index) in allComments" v-bind:key="index">
            <div class="list-group-item">
                <span>Autor: <strong>{{comment.name}}</strong></span>
                <p>Descrição: {{comment.description}}</p>
                <div>
                    <a href="#" v-on:click.prevent="removeComment(index)" class="btn btn-outline-danger btn-sm" title="Excluir">Excluir</a>
                </div>
            </div>
            <br />
        </div>
    </div>
</div>
</template>

<script>
import FormTodo from './FormTodo.vue'

export default {
    components: {
        FormTodo
    },
    data() {
        return {
            comments: []
        }
    },
    methods: {
        addComment(comment){
            this.comments.push(comment)
        },
        removeComment(index){
            this.comments.splice(index, 1)
        }
    },
    computed: {
        allComments(){
            return this.comments.map(comment => ({
                ...comment,
                name: comment.name.trim() === '' ? 'Anônimo' : comment.name
            }))
        }
    }
}
</script>
