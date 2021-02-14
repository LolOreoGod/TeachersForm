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
      <button
            id="deleting_mc_button"
            class="deleting_mc_button"
            @click="deleteOptionSet(index, optionsetindex)"
          >
            -
      </button>
    </div>
    <button 
        id="adding_mc_button"
        class="adding_mc_button"
        @click="addNewOptionSet">+
    </button>
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
    addNewOptionSet() {
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
  width: 90%;
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
  width: 90%;
  height: 30px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 3%;
  border: 1px solid black;
}

.topic-choice-answer {
  width: 90%;
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

.deleting_mc_button {
  float: center;
  margin-top: 1%;
  margin-bottom: 1%;
  width: 50px;
  font-size: 15px
}

/* adding multiple choice/checkbox button */
.adding_mc_button {
  background-color: white;
  margin-bottom: 1%;
  border: none;
  color: grey;
  border: 1px solid black;
  width: 100px;
  height: 30px;
  font-size: 20px;
  text-decoration: bold;
  border-radius: 10%;
}

.adding_mc_button:hover {
  background-color: #779fa1ff;
  color: white;
}
</style>
