<template>
    <form action="" v-on:submit.prevent class="w-2/3 flex justify-between gap-2">
        <input type="text" name="add" id="add" class="ring-0 border border-slate-800 focus:outline-none focus:ring-1 focus:border-blue-400 rounded-md py-0.5 px-2 w-full" v-model="inputTodo">
        <button type="submit" class="px-2 bg-green-300 hover:bg-green-400 rounded-sm" @click="addTodo"><i class="fa-solid fa-plus text-white"></i></button>
    </form> 
    <div class="flex shadow-sm bg-slate-100 px-6 py-2 rounded-md w-2/3 mt-4 justify-between" v-for="(data,index) in dataTodo">
        <div class="flex gap-3">
            <input type="checkbox" :name="data.id" id="activity" v-model="data.checked">
            <p :class="{checkedTodo: data.checked }">{{ data.activity}}</p>
        </div>
        <div class="flex gap-3">
            <button type="submit" class="underline underline-offset-2 hover:text-blue-500" @click="updateData(index)">Edit</button>
            <button class="underline underline-offset-2 hover:text-blue-500" @click="deleteTodos(index)">Delete</button>
        </div>
    </div>
</template>

<script>

export default {
    data() {
        return {
            dataTodo: [
                {activity: 'Olahraga', checked:false},
            ],
            inputTodo:'',
            editTodo : null,
        }
    },
    methods: {
        addTodo() {
            if(this.inputTodo.length === 0) return

            if(this.editTodo != null) {
                alert('data berhasill di update')
                this.dataTodo[this.editTodo].activity = this.inputTodo
                this.editTodo = null
            } else {
                alert('data berhasill di tambahkan')
                let data = this.inputTodo
                this.dataTodo.push({
                    activity: data,
                    checked: false
                })
            }
            this.inputTodo = ''
        },
        deleteTodos(index) {
            alert(`data ${this.dataTodo[index].activity} berhasil dihapus`)
            this.dataTodo.splice(index, 1)
        },
        updateData(index) {
            const DataEdit = this.dataTodo[index].activity
            this.inputTodo = DataEdit
            this.editTodo = index
        },
    }

}
</script>

<style>
    .checkedTodo {
        text-decoration: line-through;
        text-decoration-color: red;
    }
</style>