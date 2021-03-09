<template>
  <div class="container">
    <Header @add-task="addTask" />
    <Tasks @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<style scoped>
* {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  margin-left: 10%;
  border: 3px solid #050827;
  border-radius: 5px;
  padding: 20px;
  width: 800px;
}

@media (max-width: 600px) {
  .container {
    margin: 0px;
  }
}
</style>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    deleteTask(id) {
      fetch(
        `http://localhost:1337/tasks/${id}`,
        {
          method: "DELETE",
        }
        // resetting tasks without the task with the specific id.
      )
        .then((this.tasks = this.tasks.filter((task) => task.id !== id)))
        .catch((e) => console.log(e));
    },
    addTask(text, day, reminder) {
      const body = {
        text: text,
        day: day,
        reminder: reminder,
      };

      fetch("http://localhost:1337/tasks", {
        "method": "POST",
        "headers": {
          "Accept":"application/json",
          "Content-Type":"application/json",
        },
        "body": JSON.stringify(body),
        // fetching data again
      }).then(fetch("http://localhost:1337/tasks")
        .then((res) => res.json())
        .then((data) => {
          this.tasks = data;
        }))
    },
  },
  created() {

    // fetch data from strapi API
    fetch("http://localhost:1337/tasks")
      .then((res) => res.json())
      .then((data) => {
        this.tasks = data;
      });
  },
};
</script>

<style></style>
