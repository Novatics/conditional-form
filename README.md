# Conditional Form

This package intent is to help developers to create forms that the inputs
are showed accordingly with the response of the previous ones.

Calling the component:

### questions.js
```
export default = [
  questionNumber: 1,
  inputType: 'twoOptionsButtons',
  inputClassNames: 'optionsCssClass',
  questionText: 'Who is your favorite hero?',
  optionOneText: 'Spider-Man',
  optionTwoText: 'Batman',
  descriptionTextClassNames: 'descroptionCssClass',
  descriptionText: (
    <span>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit,
      sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
    </span>
  ),
  leftAwnserQuestions: {
    questionNumber: 2,
    type: 'text',
    inputClassNames: 'optionsCssClass',
    questionText: 'Why Spider-Man?',
    placeholder: 'type here'
  },
  rightAwnserQuestions: {
    questionNumber: 3,
    type: 'text',
    inputClassNames: 'optionsCssClass',
    questionText: 'Why Batman??',
    placeholder: 'type here'
  },
]
```

### hero-form.js
```
import React, { Component } from 'react'
import ConditionalForm from 'conditional-form'
import QUESTIONS from './question.js'

class HeroForm extends React.Component {
  constructor(props) {
    super(props);
  }

  onStepReveal = (previousStepInput, nextStepInput) => {
    console.log(`Previous step info ${previousStepInput}`)
    console.log(`Next step info ${nextStepInput}`)
  }

  handleSubmit = (data) => {
    event.preventDefault();
    console.log(`Inputs values ${data}`)
  }

  render() {
    return (
      <ConditionalForm
        questions={QUESTIONS}
        onSubmit={this.handleSubmit}
        onStepReveal={this.onStepReveal}
      />
    );
  }
}
```

---

Each section with a text and input is a "question". Each question is defined
by an object that contains all the main info for it.

Each question attributes that you'll need to pass:

### Two options buttons
```
{
  questionNumber:
  inputType:
  inputClassNames:
  questionText:
  optionOneText:
  optionTwoText:
  descriptionTextClassNames:
  descriptionText:
}
```  
