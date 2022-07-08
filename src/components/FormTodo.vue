<template>
    <div class="col-auto">
        <form class="form-group">
            <div class="col">
                <div class="col-3 mb-3">
                    <input type="text" placeholder="Autor" class="form-control" v-model="name" />
                </div>
                <div class="col-6 mb-3">
                    <textarea type="text" placeholder="Descrição" class="form-control" v-model="description"></textarea>
                </div>
            </div>
            <div class="col-auto">
                <button type="submit" v-on:click.prevent="addComment" class="btn btn-primary">Comentar</button>
            </div>
        </form>
        </div>
</template>

<script>

export default {
    data(){
        return{
            name: '',
            description: ''
        }
    },
    methods:{
        addComment(){
            if(this.name.trim() === '' && this.description === ''){
                return;
            }

            this.$emit('add-comment', {
                name: this.name,
                description: this.description 
            })
            
            this.name = ''
            this.description = ''
        },

    }
}
</script>
