# Base Alexa Hello World Skill

### This is a simple "hello world" template for building Alexa skills

This template project is based on the official Hello World template at https://github.com/alexa/skill-sample-nodejs-hello-world. That template, however, has recently become more complicated than what many projects will need as a starting point. This template is a simplified form of that template, offering as simple of a project as possible that can be used as the foundation for any Alexa skill you might create.

Specifically, this project differs from the official template in the following ways:

 * Removed the `instructions/` folder. Refer to the official template project for that information.
 * Removed all but en-US language/locale from `skill.json`, `lambda/custom/languageStrings.js`, and `models/`. (While it is a great idea to support multiple languages and locales in your skill, it is not likely that you will support all of them and it is often easier to start with a single language/locale and grow into others as the skill's functionality matures.)
 * Removed `AMAZON.NavigateHomeIntent` from `models/en-US.json`. This intent only makes sense when developing a skill that targets a screen-based device such as Echo Show. It's unnecessary for a simple Hello World skill that doesn't have visual components.
 * Removed `lambda/custom/util.js`. While this module is useful when resolving images and sounds from S3, this skill does not make use of it and any skill based on this template may never need it. If your skill needs it, then copy it from the official template project.
 * Moved `lambda/custom/local-debugger.js` to `utils/local-debugger.js` so that it won't be deployed to AWS Lambda with the skill code.
 * Removed the call to `.withCustomUserAgent()` in `lambda/custom/index.js` when building the skill. It's unclear what purpose this serves and you can certainly build and deploy a skill without it.
 * Rearranged intent declarations in `models/en-US.json` so that the "HelloWorldIntent" is first and all built-in intents follow. Also put "CancelIntent" and "StopIntent" adjacent to each other since their handler is the same.

 