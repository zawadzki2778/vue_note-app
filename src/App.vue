<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="conteiner">
          <div
            class="note-header"
            style="margin: 36px 0; justify-content: center"
          >
            <h1>{{ title }}</h1>
          </div>
          <Message v-if="message" :message="message" />

          <NewNote :note="note" @addNote="addNote" />

          <Notes :notes="notes"/>
          <!--:notes это пропс, "notes" это массив с заметками-->
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
  },
};
</script>

<style>
</style>
