<template>
  <q-page class="flex flex-center q-px-md">
    <q-card class="my-card" style="width: 500px">
      <q-card-section class="bg-primary">
        <div class="text-h6 text-white">To-Do List</div>
      </q-card-section>

      <q-card-section>
        <div class="row justify-center">
          <div class="col-12 q-pb-sm">
            <q-input v-model="todoTask" label="Input Task">
              <template v-slot:after>
                <q-btn round dense flat icon="send" @click="addItem" />
              </template>
            </q-input>
          </div>
        </div>
      </q-card-section>

      <q-card-section v-if="todoList.length > 0">
        <div class="row justify-center" v-for="(item, index) in todoList" :key="index">
          <div class="col-2 q-py-sm">{{ index + 1 }}</div>
          <div class="col-8 q-py-sm">{{ item.value }}</div>
          <div class="col-auto q-py-sm-md">
            <q-btn round dense flat icon="done" v-if="!item.done" @click="doneTodo(index)" />
            <q-btn round dense flat icon="delete" v-if="item.done" @click="removeItem(index)" />
          </div>
        </div>
      </q-card-section>

      <q-card-section v-else>
        <div class="row justify-center">
          <div class="col-12">
            <div class="text-center">
              <q-icon name="info" />
              <p>No items</p>
            </div>
          </div>
        </div>
      </q-card-section>

      <q-separator />

      <q-card-section>
        <div class="row justify-center">
          <div class="col-12">
            <div class="text-center">
              <p>Made with ❤️ in Pekalongan.</p>
              <q-btn
                size="10px"
                color="primary"
                class="q-btn--rounded"
                href="https://www.textnice.tech"
                target="_blank"
              >TextNice</q-btn>
            </div>
          </div>
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PageIndex',
  data() {
    return {
      todoTask: '',
      todoList: [
        
      ]
    }
  },
  methods: {
    addItem() {
      if (this.todoTask.trim() !== '') {
        this.todoList.push({ value: this.todoTask, done: false });
        this.todoTask = '';
      }
    },
    doneTodo(index) {
      this.todoList[index].done = true;
    },
    removeItem(index) {
      this.todoList.splice(index, 1);
      
    }
  }
})
</script>
