<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">

          <Message v-if="message" :message="message" />

          <NewNote :note="note" @addNote="addNote" />

          <div class="note-header">
            <h1 class="title">{{ title }}</h1>

            <Search />

            <div class="icons">
              <svg
                :class="{ active: grid }"
                @click="grid=true"
                xmlns="http://www.w3.org/2000/svg"
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <rect x="3" y="3" width="7" height="7"></rect>
                <rect x="14" y="3" width="7" height="7"></rect>
                <rect x="14" y="14" width="7" height="7"></rect>
                <rect x="3" y="14" width="7" height="7"></rect>
              </svg>
              <svg
                :class="{ active: !grid }"
                @click="grid = false"
                xmlns="http://www.w3.org/2000/svg"
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <line x1="8" y1="6" x2="21" y2="6"></line>
                <line x1="8" y1="12" x2="21" y2="12"></line>
                <line x1="8" y1="18" x2="21" y2="18"></line>
                <line x1="3" y1="6" x2="3" y2="6"></line>
                <line x1="3" y1="12" x2="3" y2="12"></line>
                <line x1="3" y1="18" x2="3" y2="18"></line>
              </svg>
            </div>
          </div>

          <Notes :notes="notes" @remove="removeNote" :grid="grid"/>
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
import Search from "@/components/Search.vue"
export default {
  name: "App",
  components: {
    Message,
    NewNote,
    Notes,
    Search
  },

  data() {
    return {
      title: "NOTE APP",
      message: null,
      grid: true, // <svg :class="{ active: grid }"
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
      this.notes.splice(index, 1); // index - то, что удаляем, 1 - кол-во
    },
  },
};
</script>

<style lang="scss">
h1.title {
  font-size: 30px;
}
</style>
