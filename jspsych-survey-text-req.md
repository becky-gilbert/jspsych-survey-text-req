# jspsych-survey-text-req plugin

This document was copied directly from the [jsPsych survey-text plugin](http://docs.jspsych.org/plugins/jspsych-survey-text/) and then adapted by Becky Gilbert for the survey-text-req plugin.

The survey-text-req plugin displays a set of questions with free response text fields. The subject types in answers. 

This plugin differs from the jsPsych survey-text plugin in that it allows 

## Parameters

This table lists the parameters associated with this plugin. Parameters with a default value of *undefined* must be specified. Other parameters can be left unspecified if the default value is acceptable.

Parameter | Type | Default Value | Description
----------|------|---------------|------------
questions | array | *undefined* | An array of strings. The strings are the prompts for the subject to respond to. Each string gets its own response field.
preamble | string | empty string | HTML formatted string to display at the top of the page above all the questions.
rows | array | 1 | The number of rows for the response text box. Array length must match `questions` array, with a numeric value for each entry indicating the number of rows for that question's box.
columns | array | 40 | The number of columns for the response text box. Array length must match `questions` array, with a numeric value for each entry indicating the number of columns for that question's box.
button_label | string | 'Next' | The text that appears on the button to finish the trial.
required | array | false | An array of booleans.
placeholders | array | `[""]` | An array of strings. The strings will be used to populate the text response fields with default/placeholder text (disappears when the person starts typing). This is often used to give the participant an example of the type/format of response that you're looking for.

## Data Generated

In addition to the default data collected by all plugins, this plugin collects the following data for each trial.

Name | Type | Value
-----|------|------
responses | JSON string | A string in JSON format containing the response for each question. The encoded object will have a separate variable for the response to each question, with the first question in the trial being recorded in `Q0`, the second in `Q1`, and so on. Each response is a string containing whatever the subject typed into the associated text box.
rt | numeric | The response time in milliseconds for the subject to make a response.

## Examples

The following two examples are taken from jsPsych survey-text plugin documentation.

### Basic example

```javascript
// defining groups of questions that will go together.
var survey_trial = {
  type: 'survey-text-req',
  questions: ["How old are you?", "Where were you born?"],
};
```

### Custom number of rows and columns

```javascript
var survey_trial = {
  type: 'survey-text-req',
  questions: ["How old are you?", "Where were you born?"],
  rows: [5,3],
  columns: [40,50]
};
```

### Questions where a response is required

```javascript
var survey_trial = {
  type: 'survey-text-req',
  questions: ["How old are you?", "Where were you born?"],
  required: [true, false]
};
```

### Questions with placeholder text

```javascript
var survey_trial = {
  type: 'survey-text-req',
  questions: ["How old are you?", "Where were you born?"],
  placeholders: ["e.g. 30", "e.g. USA"] // to indicate that you want age in years and country of birth
};
```