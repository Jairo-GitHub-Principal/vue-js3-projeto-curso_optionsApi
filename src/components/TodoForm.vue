<template>
    <form 
    @submit.stop.prevent="addTodo" id=" o codigo ao lado chama a função  addTodo que chama o ajax pra add uma todo, essa função esta  declarada em methods:{} "
    class="flex items-center px-4 bg-gray-900 h-15 
rounded-sm border-l-2 border-green-400 mb-3">
                
                <input
                v-model="title"
                    placeholder="Adicione um novo item ..."
                    type="text"
                    class="bg-gray-900 placeholder-gray-500 text-gray-500 font-light focus:outline-none block w-full appearance-none leading-normal py-3 pr-3 p-1"
                >
                

                <button
                    class="text-green-400 text-xs font-semibold 
focus:outline-none"
                    type="submit"

                >
                    ADICIONAR
                </button>
            </form>
            <!--/ Todoform -->
</template>

<script>
    export default {
        data(){
            return {
                title:''
            }
        },
        methods: {
            addTodo() {

                if(!this.title){ // impede que o formulario faça um envio vazio, no caso de não diigiitar nenhum titulo para o novo item
                    return;
                }
                this.$store.dispatch('addTodo',{
                    title:this.title,
                    completed: false
                }).finally(()=>{ 
                     this.title='' // reseta o imput limpando-o para prepara-lo para inserção de novos dados
                })
                console.log('here',this.title)
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>