<template>
  <!-- <div class="x-button">
   <a href="dashboard.html">X</a> -->
  <div id="form">
    <div class="x-button">
      <a href="StudentDashboard.html">X</a>
    </div>
    <div id="title">
      Title (from Database)
    </div>
    <br/>
    <div id="description">
      Description (from database)
    </div>
    <div id="due_date">
      Due Date (is this needed)
      <br /><input disabled type="datetime-local" v-model="dueDate" />
    </div>
    <br />
  
    <!--topic choice box-->
    <div id="topicChoiceBox" class="questions">
      <p>POAS Questions (or whatever teacher decides)</p>

      <!--all choice sets (question + answer)-->
      <div
        id="questionSet"
        :key="questionIndex"
        style="height: 150px"
        v-for="(questionSet, questionIndex) in choiceQuestions"
      >
        <!--question-->
        <div
          type="text"
          id="choice_question"
          class="topic-choice-text">
          Question (from database)
        </div>

        <!--Question Answer-->
        <input
          type="text"
          id="choice_question_answer"
          v-if="questionSet.type == 'short'"
          class="topic-choice-answer"
          placeholder="answer area"
        />

      </div>
      <!--END: choice set (question+answer) stack-->
    </div>
    <!--END: topic choice box-->
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
      choiceQuestions: [
        {
          type: "short",
          question: "sdjfko;ajfdk;af",
        },
      ],
      /*questionBoxes: [
        {
          
          question: "",
          title: "",
          required: false,
          type: "short answer",
          // short Answer is default question
          shortAnswers: [
            {
              answer: "",
            },
          ],
          longAnswers: [
            {
              answer: "",
            },
          ],
          multipleChoiceOptions: [
            {
              moption: "",
            },
          ],
          checkboxOptions: [
            {
              coption: "",
            },
          ], 
        }, 
      ],*/
    };
  },
  methods: {
    addNewQuestion() {
      this.questionBoxes.push({
        question: "",
        type: "short answer",
        required: true,
        shortAnswers: [
          {
            answer: "",
          },
        ],
        longAnswers: [
          {
            answer: "",
          },
        ],
        multipleChoiceOptions: [
          {
            moption: "",
          },
        ],
        checkboxOptions: [
          {
            coption: "",
          },
        ],
      });
    },
    deleteQuestion(index) {
      this.questionBoxes.splice(index, 1);
    },
    addNewMultipleChoiceOption(index) {
      this.questionBoxes[index].multipleChoiceOptions.push({
        moption: "",
      });
    },
    deleteMultipleChoiceOption(index, mcindex) {
      this.questionBoxes[index].multipleChoiceOptions.splice(mcindex, 1);
    },
    addNewCheckboxOption(index) {
      this.questionBoxes[index].checkboxOptions.push({
        coption: "",
      });
    },
    deleteCheckboxOption(index, mcindex) {
      this.questionBoxes[index].checkboxOptions.splice(mcindex, 1);
    },
    addNewChoiceQuestionSet() {
      this.choiceQuestions.push({
        type: "short",
        question: "",
        answer: "",
      });
    },
    deleteChoiceQuestionSet(questionIndex) {
      if (this.choiceQuestions.length !== 1) {
        this.choiceQuestions.splice(questionIndex, 1);
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

/* topic choice box */
#topicChoiceBox {
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
