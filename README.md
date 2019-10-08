# Conditional Form

This package intent is to help developers to create forms that the inputs
are showed accordingly with the response of the previous ones.

---

Calling the component:

### questions.js

```javascript
export default {
  number: 1,
  type: "twoOptionsButtons",
  ClassNames: "optionsCssClass",
  text: "Who is your favorite hero?",
  specificFields: {
    optionOneText: "Spider-Man",
    optionTwoText: "Batman",
    descriptionTextClassNames: "descroptionCssClass",
    descriptionText: (
      <span>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua.
      </span>
    ),
    questions: [
      {
        number: 2,
        type: "text",
        classNames: "optionsCssClass",
        text: "Why Spider-Man?",
        specificFields: {
          placeholder: "type here"
        }
      },
      {
        number: 3,
        type: "text",
        classNames: "optionsCssClass",
        text: "Why Batman??",
        specificFields: {
          placeholder: "type here"
        }
      }
    ]
  }
};
```

### hero-form.js

```javascript
import React, { Component } from "react";
import ConditionalForm from "conditional-form";
import QUESTIONS from "./question.js";

class HeroForm extends React.Component {
  constructor(props) {
    super(props);
  }

  onStepReveal = (previousStepInput, nextStepInput) => {
    console.log(`Previous step info ${previousStepInput}`);
    console.log(`Next step info ${nextStepInput}`);
  };

  handleSubmit = data => {
    event.preventDefault();
    console.log(`Inputs values ${data}`);
  };

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

**Currently we're only supporting two types of questions:**

- Two options buttons
- Simple text input

Each question attributes that you'll need to pass:

### Two options buttons

```
{
  number: <Number>,
  type: 'twoOptionsButtons',
  classNames: <String>,
  text: <String>,
  specificFields: {
    optionOneText: <String>,
    optionTwoText: <String>,
    descriptionTextClassNames: <String>,
    descriptionText: <String>,
    questions: <Array of Questions objects>
  }
}
```

### Simple text input

```
{
  number: <Number>,
  type: 'text',
  classNames: <String>,
  text: <String>,
  specificFields: {
    placeholder: <String>
  }
}
```

PS: The numbers assigned to `number` must be sequential
