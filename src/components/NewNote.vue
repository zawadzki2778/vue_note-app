<template>
  <!-- ДОБАВЛЕНИЕ НОВОЙ ЗАМЕТКИ-->
  <div class="new-note">
    <label>Title</label>
    <input type="text" v-model="note.title" />
    <label>Description</label>
    <textarea v-model="note.descr"></textarea>
    <button class="btn btnPrimary" @click="addNote">new note</button>
  </div>
</template>

<script>
export default {
  name: "NewNote",
  data() {
    return {};
  },
  props: {
    note: {
      type: Object,
      required: true
    },
  },
  methods: {
    addNote() {
      this.$emit("addNote", this.note);
    },
  },
};
</script>

<style lang="scss" scoped>
.new-note {
  text-align: center;
}
</style>