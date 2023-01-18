<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="conteiner">
          <div class="note-header">
            <h1>{{ title }}</h1>
            <div class="message" v-if="message">
              <p>{{ message }}</p>
            </div>

            <!-- ДОБАВЛЕНИЕ НОВОЙ ЗАМЕТКИ-->
            <div class="new-note">
              <input type="text" v-model="note.title" />
              <textarea v-model="note.descr"></textarea>
              <button @click="addNote">new note</button>
            </div>
          </div>
          <div class="note" v-for="(note, index) in notes" :key="index">
            <div>{{ note.title }} {{ note.descr }}</div>
            <div>{{ note.date }}</div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "NOTE APP",
      message: null,
      note: {
        title: "",
        descr: "",
        date: new Date(Date.now()).toLocaleString(),
      },
      notes: [
        {
          title: "First Note",
          descr: "Description for first note",
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: "Second Note",
          descr: "Description for second note",
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: "Third Note",
          descr: "Description for third note",
          date: new Date(Date.now()).toLocaleString(),
        },
      ],
    };
  },
  methods: {
    addNote() {
      if (this.note.title === "") {
        this.message = "it`s required field !";
        return false;
      }
      this.notes.push(this.note);
      this.message = null; // чтобы не выводилaсь ошибка при правильной отправке
      this.note.title = ""; // сброс данных после отправки
      this.note.descr = ""; //  ---------- // ------------
    },
  },
};
</script>

<style>
</style>
