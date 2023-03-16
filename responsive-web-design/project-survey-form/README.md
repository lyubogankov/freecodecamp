## Build a Survey Form

Objective: Build an app that is functionally similar to https://survey-form.freecodecamp.rocks

## User Stories:

01. :heavy_check_mark: You should have a page title in an `h1` element with an `id` of `title`

02. :heavy_check_mark: You should have a short explanation in a `p` element with an `id` of `description`

03. :heavy_check_mark: You should have a `form` element with an `id` of `survey-form`

04. :heavy_check_mark: Inside the `form` element, you are required to enter your name in an `input` field that has an `id` of `name` and a `type` of `text`

05. :heavy_check_mark: Inside the `form` element, you are required to enter your email in an input field that has an `id` of `email`

06. :heavy_check_mark: If you enter an email that is not formatted correctly, you will see an HTML5 validation error
    - This is handled by the `input` element's `type="email"` property!

07. :heavy_check_mark: Inside the form, you can enter a number in an `input` field that has an `id` of `number`

08. :heavy_check_mark: The number `input` should not accept non-numbers, either by preventing you from typing them or by showing an HTML5 validation error (depending on your browser).
09. :heavy_check_mark: If you enter numbers outside the range of the number input, which are defined by the `min` and `max` attributes, you will see an HTML5 validation error
    - The above two are both handled by the `input` element's `type="number"` property!

10. :heavy_check_mark: For the name, email, and number `input` fields, you can see corresponding `label` elements in the form, that describe the purpose of each field with the following ids: `id="name-label"`, `id="email-label"`, and `id="number-label"`

11. :heavy_check_mark: For the name, email, and number `input` fields, you can see placeholder text that gives a description or instructions for each field

12. :heavy_check_mark: Inside the `form` element, you should have a `select` dropdown element with an `id` of `dropdown` and at least two `option`s to choose from

13. :heavy_check_mark: Inside the `form` element, you can select an option from a group of at least two radio buttons that are grouped using the `name` attribute

14. :heavy_check_mark: Inside the `form` element, you can select several fields from a series of checkboxes, each of which must have a `value` attribute

15. :heavy_check_mark: Inside the `form` element, you are presented with a `textarea` for additional comments

16. :heavy_check_mark: Inside the `form` element, you are presented with a button with `id` of `submit` to submit all the inputs
    - I think I can use an `input` for this?  They might require a `button`, we shall see

Fulfill the user stories and pass all the tests below to complete this project. Give it your own personal style. Happy Coding!

Note: Be sure to add <link rel="stylesheet" href="styles.css"> in your HTML to link your stylesheet and apply your CSS
