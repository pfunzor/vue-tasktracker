<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input
        list="texts"
        type="text"
        v-model="text"
        id="text"
        name="text"
        placeholder="Add Task"
      />
      <datalist id="texts">
        <option value="Buy Groceries"> </option>
        <option value="Watch Netflix"> </option>
        <option value="Excersize"> </option>
        <option value="Read a book"> </option>
        <option value="Go to the mall"> </option>
      </datalist>
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      day: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.text) {
        alert("invalid task");
        return;
      }

      const newTask = {
        id: Math.floor(Math.random() * 10000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };

      this.text = "";
      this.day = "";
      this.reminder = "";
      console.log(newTask);
      this.$emit("add-task", newTask);
    },
    emits: ["add-task"],
  },
};
</script>
<style scoped>
input {
  -webkit-border-radius: 20px;
  -moz-border-radius: 20px;
  border-radius: 25px;
}
input[type="text"] {
  border: 2px solid #97d1d6;
  background-color: rgb(246, 250, 253);
}
input[type="text"]:focus {
  outline: none;
}
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
