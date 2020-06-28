<template>
    <v-card class="mb-4" id="question-container" :dark="isdark">
        <v-card-title>
            {{question.q}}
        </v-card-title>
        <v-checkbox
            class="ml-4"
            v-for="(answer, index) in answers"
            :key="index"
            :error="errors[index]"
            :success="successes[index]"
            :false-value="true"
            v-model="user_answers"
            :label="answer.text"
            :value="answer.id"
        >
        </v-checkbox>
        <v-sheet
            class="d-flex pb-2 mr-2"
        >
            <v-btn
                class="ml-auto mr-2"
                @click="validate"
                color="success"
            >
                Validate
            </v-btn>
            <v-btn
                @click="$emit('next'); reset()"
                color="primary"
            >Next</v-btn>
        </v-sheet>
    </v-card>
</template>
<style scoped>
#question-container {
  position: relative;
}
</style>

<script>
export default {
    name: "Question",
    props: ['question','isdark'],
    data () {
        return {
            user_answers: [],
            errors: [],
            successes: [],
        }
    },
    computed: {
        answers () {
            return this.question.answers
        },
        right_answers () {
            return this.question.rightids.split('')
        }
    },
    methods: {
        validate () {
            for (let i = 0; i < this.answers.length; i++) {
                this.errors[i] = false
                this.successes[i] = false
            }
            for (let [index, answer] of this.answers.entries()) {
                if (this.right_answers.includes(""+answer.id)) {
                    if (this.user_answers.includes(+answer.id)) this.successes[index] = true
                    else this.errors[index] = true
                } else {
                    if (this.user_answers.includes(+answer.id)) this.errors[index] = true
                }
            }
            this.$forceUpdate();
        },
        reset () {
            this.errors = []
            this.successes = []
            this.user_answers = []
            for (let i = 0;i < this.answers.length; i++) {
                this.errors[i] = false
                this.successes[i] = false
            }
            this.$forceUpdate()
        },
    },
    mounted () {
            for (let i = 0;i < this.answers.length; i++) {
                this.errors[i] = false
                this.successes[i] = false
            }
        }
}
</script>