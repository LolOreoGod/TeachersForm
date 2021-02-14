<template>
  <!-- <div class="x-button">
   <a href="dashboard.html">X</a> -->
  <div id="form">
    <div class="x-button">
      <a href="StudentDashboard.html">X</a>
    </div>
    <div id="title">Title (from Database)</div>
    <br />
    <div id="description">Description (from database)</div>
    <div id="due_date">
      Due Date (is this needed)
      <br /><input disabled type="datetime-local" v-model="dueDate" />
    </div>
    <br />

    <!--option boxes-->
    <div
      id="optionSet"
      bind:key="{index}"
      v-for="(optionSet, index) in options"
      :key="optionSet"
    >
      <div
        id="questionSet"
        bind:key="questionIndex"
        v-for="questionSet in optionSet"
        :key="questionSet"
      >
        <!--question-->
        <div type="text" id="choice_question" class="topic-choice-text">
          Question (from database)
        </div>
        <!--Question Answer-->
        <input
          type="text"
          id="choice_question_answer"
          class="topic-choice-answer"
          placeholder="answer area"
        />
      </div>

      <!--trash button-->
      <div class="trash_can">
        <div class="trash_symbol" @click="deleteOptionSet(index)">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="currentColor"
            class="bi bi-trash"
            viewBox="0 0 16 16"
          >
            <path
              d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"
            />
            <path
              fill-rule="evenodd"
              d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4L4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"
            />
          </svg>
        </div>
      </div>
    </div>
    <button @click="addNewOptionSet">Add</button>
    <div class="submit-button">Submit</div>
  </div>
  <!--form-->
</template>

<script>
function getISOStringWithoutSecsAndMillisecs2(date) {
  const dStr = date.toISOString();
  return dStr.substring(0, dStr.indexOf(":", dStr.indexOf(":") + 1));
}
export default {
  name: "TeachersForm",
  el: "#form",
  data() {
    return {
      title: "",
      desc: "",
      dueDate: getISOStringWithoutSecsAndMillisecs2(new Date()),
      options: [
        {
          answer1: "",
          answer2: "",
          answer3: "",
        },
        {
          answer1: "",
          answer2: "",
          answer3: "",
        },
        {
          answer1: "",
          answer2: "",
          answer3: "",
        },
      ],
    };
  },
  methods: {
    addNewOptionSet(index) {
      this.options.push({
        answer1: "",
        answer2: "",
        answer3: "",
      });
    },
    deleteOptionSet(index) {
      if (this.options.length > 3) {
        this.options.splice(index, 1);
      }
    },
  }, // methods end
}; // app end
</script>


<style scoped>
/* box for form */
#form {
  height: auto;
  width: 70%;
  background-color: #e1caabff;
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1%;
  margin-bottom: 10%;
  border: 1px solid black;
}
/* box for title */
#title {
  width: 90%;
  height: 50px;
  background-color: #eeeeeeff;
  margin-left: auto;
  margin-right: auto;
  margin-top: 2%;
  border: 1px solid black;
}
/* Text box for title */
.title-text {
  width: 100%;
  border: none;
  box-sizing: border-box;
  border-radius: 4px;
  height: 100%;
  font-size: 100%;
}
/* box for description */
#description {
  width: 90%;
  height: 50px;
  background-color: #eeeeeeff;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1%;
  border: 1px solid black;
}
/* Text box for descrption */
.desc-text {
  width: 100%;
  border: none;
  box-sizing: border-box;
  border-radius: 4px;
  height: 100%;
  font-size: 100%;
}
/* box for x-button */
.x-button {
  width: 20px;
  height: 20px;
  background-color: #c95237ff;
  float: right;
  border: 1px solid black;
  text-decoration: none;
  display: block;
  color: white;
}
/* letter in the x-button */
.x-button a {
  float: none;
  color: white;
  text-decoration: none;
  display: block;
  text-align: center;
}
/* box for due date */
#due_date {
  width: auto;
  background-color: #779fa1ff;
  float: right;
  margin-right: 1%;
  margin-top: 1%;
  border: 1px solid black;
}

/* option */
#optionSet {
  width: 600px;
  height: auto;
  background-color: #eeeeeeff;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 1%;
  margin-top: 6%;
  border: 1px solid black;
  display: block;
}

/* label of choice box */
.topic-label {
  width: 200px;
  height: 30px;
  float: left;
  margin-left: 1%;
  margin-bottom: 10px;
  float: bottom;
  border: 1px solid black;
}
/*question and answer text inputs in choice question box*/
.topic-choice-text {
  width: 550px;
  height: 30px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 3%;
  border: 1px solid black;
}

.topic-choice-answer {
  width: 550px;
  height: 80px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 3%;
  border: 1px solid black;
}

.submit-button {
  height: 25px;
  width: 100px;
  background-color: #be4b31ff;
  border: 1px solid black;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 1%;
  color: white;
  display: block;
  text-align: center;
}
</style>
