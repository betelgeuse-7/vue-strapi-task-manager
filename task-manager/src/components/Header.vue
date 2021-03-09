<template>
    <header>
        <h1>Task Tracker</h1>
        <label>Text: <input type="text" id="task-text"></label>
        <label>Day: <input type="text" id="task-day"></label>
        <label>Reminder?<input type="checkbox" id="task-reminder"></label>
        <button id="add-btn" @click="addTask" >Add Task</button>
    </header>
</template>

<style scoped>
    h1 {
    font-size: 40px;
    font-weight: 450;
    border-bottom: 4px solid #000;
    width: 350px;
  }
  label, input {
      display: block;
  }
  label {
      font-weight: 500;
      margin-bottom: 5px;
  }
  input[type="text"], input[type="number"] {
      width: 30%;
      height: 22px;
        border: 1px solid #3c53d4;
        border-radius: 5px;
        outline: none;
        padding: 0px 5px 0px 5px;
        font-size: 16px;
  }
  #task-reminder {
      width: 20px;
      height: 20px;
  }

  #add-btn {
      border: none;
      outline: none;
      color: #fff;
      width: 90px;
      height: 35px;
      background-color: #31d131;
      cursor: pointer;
      font-size: 17px;
  }

</style>

<script>

    export default {
        name: "Header",
        props: {
        },

        methods: {
            addTask() {
                const text = document.getElementById("task-text").value;
                const day = document.getElementById("task-day").value;
                const reminder = document.getElementById("task-reminder").checked;

                if (text !== '' && day !== ''){
                    this.$emit("add-task", text, day, reminder)
                }
            }   
        }

    }
</script>

<style scoped>

</style>

