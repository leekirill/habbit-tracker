<script>
Date.prototype.daysInMonth = function () {
  return 32 - new Date(this.getFullYear(), this.getMonth(), 32).getDate()
}

export default {
  data: () => ({
    days: [],
  }),
  computed: {
    getData() {
      return new Date().daysInMonth()
    },
  },
  mounted() {
    for (let i = 0; i < this.getData; i++) {
      this.days.push({ id: i, checked: false })
    }
  },
}
</script>

<template>
  <div class="count">
    <h3>0</h3>
    <span>/{{ this.days.length }}</span>
  </div>
  <div>
    <ul class="list">
      <li class="list__item" v-for="(day, id) of days" :key="id">
        <label class="custom-checkbox">
          <input class="hidden-checkbox" type="checkbox" />
          <span>{{ id + 1 }}</span>
          <div class="checkbox"></div>
        </label>
      </li>
    </ul>
  </div>
</template>

<style scoped>
h3 {
  font-size: 40px;
  padding: 0;
  margin: 0 0 40px 0;
}
.list {
  display: flex;
  flex-wrap: wrap;
  padding: 0;
  margin: 0;
  width: 350px;
}
.list__item {
  position: relative;
  list-style: none;
}

.custom-checkbox {
  display: flex;
  align-items: center;
}
.custom-checkbox input {
  -webkit-appearance: none;
  position: absolute;
}
.custom-checkbox span {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 20px;
  z-index: 1;
}
.checkbox {
  position: relative;
  width: 3em;
  height: 3em;
  border: 1px solid rgb(255, 255, 255);
}

.custom-checkbox input:checked ~ .checkbox .checkmark {
  display: block;
}
.custom-checkbox input:checked ~ .checkbox {
  background: blue;
}
</style>
