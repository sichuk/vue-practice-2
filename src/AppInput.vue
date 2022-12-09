<template>
 <form class="card card-w30"  @submit.prevent="submit">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="type">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
          </div>
        
        <div class="form-control">
        <label for="value">Значение</label>
        <textarea
            id="value"
            rows="3"
            v-model="value"
            :placeholder="avatarPlaceholder"
          ></textarea>
      </div>

      <button type="submit" class="btn primary" :disabled="this.value.length<3">Добавить</button>
    </form>

</template>

<script>
export default {
  emits:['block-add'],
  data() {
    return {
      type:'title',
      value:'',
      id: Date.now()
    }
  },

  methods: {
    submit () {
      this.$emit('block-add', {
        type: this.type,
        value: this.value,
        })
        this.type='title',
        this.value=''
        
    }
  },
  computed: {
    avatarPlaceholder() {
      return this.type === "avatar" ? "Вставьте ссылку на изображение" : "Введите текст"
    }
  }


 
}
</script>

<style>

</style>