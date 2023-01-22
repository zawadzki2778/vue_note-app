<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{ title }}</h1>

          <Message v-if="message" :message="message" />

          <NewNote :note="note" @addNote="addNote" />

          <Notes :notes="notes" @remove="removeNote" />
          <!--:notes это пропс, "notes" это массив с заметками
               @remove это названия эмита, removeNote это название метода который создаём здесь (App)-->
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import Message from "@/components/Message.vue";
import NewNote from "@/components/NewNote.vue";
import Notes from "@/components/Notes.vue";
export default {
  name: "App",
  components: {
    Message,
    NewNote,
    Notes,
  },

  data() {
    return {
      title: "NOTE APP",
      message: null,
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
      note: {
        title: "",
        descr: "",
        date: "",
      },
    };
  },

  methods: {
    addNote() {
      let { title, descr } = this.note;
      if (title === "") {
        this.message = "FILL IT INPUT !!!";
        return false;
      } else {
        this.notes.push({
          title,
          descr,
          date: new Date(Date.now()).toLocaleString(),
        });
        this.message = null;
        this.note.title = "";
        this.note.descr = "";
      }
    },
    removeNote(index) {
      this.notes.splice(index, 1); // inex - то, что удаляем, 1 - кол-во 
    },
  },
};
</script>

<style>
</style>
