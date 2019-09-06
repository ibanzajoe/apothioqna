<template>
  <div class="qna-index">
    <div class="qna-header flex justify-center py-4">
      <div class="qna-logo-holder">
        <img style="max-width: 150px; margin: 0 auto;" src="logo/logo_whitebg.png" alt="logo" />
      </div>
    </div>

    <div class="qna-content flex items-start justify-start ">
      <template v-for="(question, index) in questions">
        <div class="qna-content-window flex items-center justify-center px-2">
          <qna-wrapper :key="index" >
            <div slot="question-slot">
              <h3 class="question-label">
                {{question.question}}
              </h3>
            </div>
            <div slot="choices-slot">
              <binary v-if="question.choiceType == 'binary'" :choices="question.choices" />
              <select-multi v-else-if="question.choiceType == 'selectMulti'" :choices="question.choices" />
              <free-input v-else-if="question.choiceType == 'free'" />
              <terms-check v-else-if="question.choiceType == 'terms'" />
              <select-one v-else :choices="question.choices" />
            </div>
          </qna-wrapper>
        </div>
      </template>
    </div>

    <div class="qna-footer">

    </div>


  </div>
</template>

<script>
  import binary from '~/components/qna/choices/binaryChoice'
  import selectOne from '~/components/qna/choices/selectOne'
  import selectMulti from '~/components/qna/choices/selectMulti'
  import qnaWrapper from '~/components/qna/choices/qnaWrapper'
  import freeInput from '~/components/qna/choices/freeInput'
  import termsCheck from '~/components/qna/choices/termsCheck'

  export default {
    name: "qna-index",
    components: {
      binary, selectOne, selectMulti, qnaWrapper, freeInput, termsCheck
    },
    data () {
      return {
        choices: [
          {
            type: 'binary',
            choices: ['yes', 'no']
          },
          {
            type: 'selectMulti',
            choices: [
              {label: 'Tincture', icon: './images/selectMulti/formTincture.png'},
              {label: 'Gummies', icon: './images/selectMulti/formGummies.png'},
              {label: 'Vaporizer', icon: './images/selectMulti/formVaporizer.png'},
              {label: 'Lotion', icon: './images/selectMulti/formLotion.png'},
              {label: 'Gel Caps', icon: './images/selectMulti/formPill.png'},
              {label: 'Pharma', icon: './images/selectMulti/formPharm.png'},
              {label: 'Suppository', icon: './images/selectMulti/formSuppository.png'}
            ]
          },
          {
            type: 'selectOne',
            choices: [
              {label: 'Rarely', iconLabel: '--'},
              {label: 'A few days', iconLabel: '2-3'},
              {label: 'Every day', iconLabel: '365'},
              {label: '2+ / day', iconLabel: '2x+'}
            ]
          }
        ],
        questions: [
          {
            q_id: 1,
            question: 'Have you taken CBD before?',
            choices: ['yes', 'no'],
            answer: 'yes',
            choiceType: 'binary',
            sponsor: true,
            sponsorToggle: {
              questions: [2, 3],
              answer: 'yes'
            },
          },
          {
            q_id: 2,
            question: 'On an average day, you eat protein:',
            choices: [
              {label: 'Tincture', icon: '/images/formTincture.png'},
              {label: 'Gummies', icon: '/images/formGummies.png'},
              {label: 'Vaporizer', icon: '/images/formVaporizer.png'},
              {label: 'Lotion or Balm', icon: '/images/formLotion.png'},
              {label: 'Gel Caps', icon: '/images/formPill.png'},
              {label: 'Pharmaceutical', icon: '/images/formPharm.png'},
              {label: 'Suppository', icon: '/images/formSuppository.png'}
            ],
            choiceType: 'selectMulti',
            multiChoice: true,
            answer: [],
            dependent: {
              q_id: 1,
              answer: 'yes'
            }
          },
          {
            q_id: 3,
            question: 'In an average week, how often do you take CBD?',
            choices: [
              {label: 'Rarely', iconLabel: '--'},
              {label: 'A few days', iconLabel: '2-3'},
              {label: 'Every day', iconLabel: '365'},
              {label: '2+ / day', iconLabel: '2x+'}
            ],
            answer: null,
            dependent: {
              q_id: 1,
              answer: 'yes'
            }
          },
          {
            q_id: 4,
            question: 'Are you?',
            choices: ['male', 'female'],
            choiceType: 'binary',
            answer: null
          },
          {
            q_id: 5,
            question: 'How old are you?',
            choices: ['free'],
            choiceType: 'free',
            placeholder: 'years',
            formType: 'number',
            answer: null
          },
          {
            q_id: 6,
            question: 'What is your approximate body weight?',
            choices: ['free'],
            choiceType: 'free',
            formType: 'number',
            answer: null
          },
          {
            q_id: 7,
            question: 'Do you have problems with anxiety?',
            choices: ['yes', 'no'],
            choiceType: 'binary',
            answer: null,
            sponsor: true,
            sponsorToggle: {
              questions: [8, 9],
              answer: 'yes'
            },
          },
          {
            q_id: 8,
            question: 'What is the intensity level of your anxiety?',
            choices: [
              {label: 'low'},
              {label: 'moderate'},
              {label: 'very high'}
            ],
            answer: null,
            dependent: {
              q_id: 7,
              answer: 'yes'
            }
          },
          {
            q_id: 9,
            question: 'How many days of the week do you experience anxiety?',
            choices: [
              {label: '1'},
              {label: '2'},
              {label: '3'},
              {label: '4'},
              {label: '5'},
              {label: '6'},
              {label: '7'}
            ],
            answer: null,
            dependent: {
              q_id: 7,
              answer: 'yes'
            }
          },
          {
            q_id: 10,
            question: 'Do you have problems with pain?',
            choices: ['yes', 'no'],
            choiceType: 'binary',
            answer: null,
            sponsor: true,
            sponsorToggle: {
              questions: [11, 12, 13, 14],
              answer: 'yes'
            }
          },
          {
            q_id: 11,
            question: 'What kind of pain are you experiencing?',
            choices: ['free'],
            choiceType: 'free',
            placeholder: 'sharp, dull, numbing...',
            formType: 'text',
            answer: null,
            dependent: {
              q_id: 10,
              answer: 'yes'
            }
          },
          {
            q_id: 12,
            question: 'Where are you experiencing pain?',
            choices: ['free'],
            choiceType: 'free',
            placeholder: 'lower back, neck, hands...',
            formType: 'text',
            answer: null,
            dependent: {
              q_id: 10,
              answer: 'yes'
            }
          },
          {
            q_id: 13,
            question: 'What is the intensity level of your pain?',
            choices: [
              {label: 'low'},
              {label: 'moderate'},
              {label: 'very high'}
            ],
            answer: null,
            dependent: {
              q_id: 10,
              answer: 'yes'
            }
          },
          {
            q_id: 14,
            question: 'How many days are you in pain?',
            choices: [
              {label: '1'},
              {label: '2'},
              {label: '3'},
              {label: '4'},
              {label: '5'},
              {label: '6'},
              {label: '7'}
            ],
            answer: null,
            dependent: {
              q_id: 10,
              answer: 'yes'
            }
          },
          {
            q_id: 15,
            question: 'Do you suffer from insomnia?',
            choices: ['yes', 'no'],
            choiceType: 'binary',
            answer: null,
            sponsor: true,
            sponsorToggle: {
              questions: [16, 17],
              answer: 'yes'
            }
          },
          {
            q_id: 16,
            question: 'What is the intensity level of your insomnia?',
            choices: [
              {label: 'low'},
              {label: 'moderate'},
              {label: 'very high'}
            ],
            answer: null,
            dependent: {
              q_id: 15,
              answer: 'yes'
            }
          },
          {
            q_id: 17,
            question: 'How many days of the week do you experience insomnia?',
            choices: [
              {label: '1'},
              {label: '2'},
              {label: '3'},
              {label: '4'},
              {label: '5'},
              {label: '6'},
              {label: '7'}
            ],
            answer: null,
            dependent: {
              q_id: 15,
              answer: 'yes'
            }
          },
          {
            q_id: 18,
            question: 'Are you experiencing other symptoms or chronic disease?',
            choices: ['yes', 'no'],
            choiceType: 'binary',
            answer: null,
            sponsor: true,
            sponsorToggle: {
              questions: [19, 20, 21],
              answer: 'yes'
            }
          },
          {
            q_id: 19,
            question: 'What other kinds of symptoms or chronic disease are you experiencing?',
            choices: ['free'],
            choiceType: 'free',
            formType: 'text',
            answer: null,
            dependent: {
              q_id: 18,
              answer: 'yes'
            }
          },
          {
            q_id: 20,
            question: 'What is the intensity level of these symptoms?',
            choices: [
              {label: 'low'},
              {label: 'moderate'},
              {label: 'very high'}
            ],
            answer: null,
            dependent: {
              q_id: 18,
              answer: 'yes',
            }
          },
          {
            q_id: 21,
            question: 'What is the intensity level of these symptoms?',
            choices: [
              {label: '1'},
              {label: '2'},
              {label: '3'},
              {label: '4'},
              {label: '5'},
              {label: '6'},
              {label: '7'}
            ],
            answer: null,
            dependent: {
              q_id: 18,
              answer: 'yes',
            }
          },
          {
            q_id: 22,
            question: 'Thank you for helping us understand your needs! You\'re almost there! let\'s comlete your profile.  Upon completion, we\'ll send you 200 mg of our whole plant CBD oil.',
            choices: ['none'],
            choiceType: 'none',
            answer: null
          },
          {
            q_id: 23,
            questionType: 'endForm',
            question: 'Please provide the information below',
            formFields: {
              firstName: '',
              lastName: '',
              fullName: '',
              email: '',
              address: '',
              suite: '',
              city: '',
              state: '',
              zip: '',
              phone: ''
            },
            answer: null
          },
          /*{
            q_id: 23,
            question: 'What is your first name?',
            choices: ['free'],
            answer: null
          },
          {
            q_id: 24,
            question: 'What is your last name?',
            choices: ['free'],
            answer: null
          },
          {
            q_id: 25,
            question: 'What is your email address?',
            choices: ['free'],
            answer: null
          },
          {
            q_id: 26,
            question: 'Where can we send your free CBD oil?',
            choices: ['none'],
            answer: null
          },
          {
            q_id: 27,
            question: 'What is your street address?',
            choices: ['free'],
            answer: null
          },
          {
            q_id: 28,
            question: 'City?',
            choices: ['free'],
            answer: null
          },
          {
            q_id: 29,
            question: 'State?',
            choices: ['free'],
            answer: null
          },
          {
            q_id: 30,
            question: 'Zip code?',
            choices: ['free'],
            answer: null
          },
          {
            q_id: 31,
            question: 'What is your phone number?',
            choices: ['free'],
            answer: null
          },*/
          {
            q_id: 24,
            question: 'Do you hold Apothio harmless against any and all claims relating to death, physical injury, or damage arising from or relating to the use of our whole plant hemp derived cannabinoid oil?',
            choices: ['terms'],
            choiceType: 'terms',
            placeholder: 'I agree to not hold Apothio responsible for any harm relating to the use of their products',
            answer: null
          },
          {
            q_id: 25,
            question: 'Do you agree to completing a 30 second follow up survey in two weeks?',
            choices: ['terms'],
            choiceType: 'terms',
            placeholder: 'I agree to complete a 30 second survey in two weeks',
            answer: null
          },
          {
            q_id: 26,
            question: '',
            questionType: 'end'
          }
        ]
      }
    }
  }
</script>

<style scoped>
  .qna-index {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto 1fr 150px;
    background-color: #f5f1ed;
    height: 100vh;
  }

  .qna-content {
    overflow-y: auto;
  }

  .qna-content-window {
    min-width: 100%;
    height: 100%;
  }

  .question-label {
    font-size: 21px;
    font-weight: 600;
    max-width: 684px;
    text-align: center;
  }
</style>
