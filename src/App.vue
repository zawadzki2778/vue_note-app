<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="conteiner">
          <div class="note-header">
            <h1>{{ title }}</h1>
          </div>
          <div class="note" v-for="(note, index) in notes" :key="index">
            <div>{{ note.title }} will be about: {{ note.descr }}</div>
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
};
</script>

<style>
</style>
