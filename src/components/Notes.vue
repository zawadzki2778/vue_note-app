<template>
  <div class="notes">
    <div
      class="note"
      :class="{ full: !grid }"
      v-for="(note, index) in notes"
      :key="index"
    >
      <div class="note-header" :class="{ full: !grid }">
        <p>{{ note.title }}</p>
        <p style="cursor: pointer" @click="removeNote(index)">x</p>
      </div>
      <div class="note-body">
        <p>{{ note.descr }}</p>
        <span>{{ note.date }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Notes",
  props: {
    notes: {
      type: Array,
      required: true,
    },
    grid: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    removeNote(index) {
      console.log(index);
      this.$emit("remove", index);
    },
  },
};
</script>

<style lang="scss" >
.notes {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 40px 0;
}

.note {
  cursor: pointer;
  width: 49%;
  padding: 20px;
  margin-bottom: 20px;
  background-color: #fff;
  transition: all 0.25s cubic-bezier(0.02, 0.01, 0.47, 1);
  box-shadow: 0 30px 30px rgba(0, 0, 0, 0.02);

  &:hover {
    box-shadow: 0 30px 30px rgba(0, 0, 0, 0.04);
    transform: translate(0, -6px); // Для подпрыгивания вверх
    transition-delay: 0s !important; // Для быстрого опускания вниз
  }

  &.full {
    width: 100%; //добавляем класс full при клике на svg
    text-align: center;
  }
}

.note-header {
  display: flex;
  justify-content: space-between;
  p {
    font-size: 22px;
    color: rgb(30, 30, 181);
  }
  svg {
    margin-right: 12px;
    color: #999999;
    cursor: pointer;
    &.active {
      color: rgb(30, 30, 181);
    }
    &:last-child {
      margin: 0;
    }
  }
  &.full {
    justify-content: center;
    p {
      margin-right: 16px;
      &:last-child {
        margin-right: 0;
      }
    }
  }
}

.note-body {
  p {
    margin: 20px 0;
  }
  span {
    font-size: 14px;
    color: #999999;
  }
}
</style>