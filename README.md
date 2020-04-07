# Base Alexa Hello World Skill

### This is a simple "hello world" template for building Alexa skills

## What is this?

This template project is based on the official Hello World template at https://github.com/alexa/skill-sample-nodejs-hello-world. That template, however, has recently become more complicated than what many projects will need as a starting point.

This template project is a simplified form of that template, offering a simpler starting point for any Alexa skill you might want to create.

If you find this template useful, you might also want to check out [my book](https://pragprog.com/book/cwalexa/build-talking-apps) where I use this template as the starting point for a skill that is built throughout the book.

## How do I use it?

You may simply `git clone` this repository and start developing your own skill on top of it. Or you may use the ASK CLI to clone it for you.

If you are using ASK CLI v1 (the one that is commonly used at this time), you will need to use the `--url` parameter to reference a template list JSON file that references this repository. For example:

    $ ask new --url https://thetalkingapp.s3.amazonaws.com/templates.json

And select the "Hello World (simple)" template. You'll then be asked to give the project a name; use any name you wish. Then you'll be warned that the template is from an unofficial resource and be asked if you wish to continue. Answer "y" and the project will be created on your machine for you.

If you are using ASK CLI v2 (which at this time is still in beta), there is not yet an equivalent template. Once ASK CLI v2 is released out of beta, this project will be converted appropriately. In the meantime, you can use the `askx util upgrade-to-v2` command to convert this project to ASK CLI v2.

## What do I do next?

Once the project has been created, you can tweak the skill to do whatever you want. When you're ready, you can use the ASK CLI to deploy it:

    $ ask deploy

After a few moments, it will deployed and ready to try out. You can use your Alexa device to test it or use `ask dialog` to kick the tires:

    $ ask dialog -l en-US
      User  > open hello world
      Alexa > Welcome, you can say Hello or Help. Which would you like to try?
      User  > say hello
      Alexa > Hello World!
      User  > !quit

## What's different?

Specifically, this project differs from the official template in the following ways:

 * Removed the `instructions/` folder. Refer to the official template project for that information.
 * Removed all but en-US language/locale from `skill.json`, `lambda/custom/languageStrings.js`, and `models/`. (While it is a great idea to support multiple languages and locales in your skill, it is not likely that you will support all of them and it is often easier to start with a single language/locale and grow into others as the skill's functionality matures.)
 * Removed `AMAZON.NavigateHomeIntent` from `models/en-US.json`. This intent only makes sense when developing a skill that targets a screen-based device such as Echo Show. It's unnecessary for a simple Hello World skill that doesn't have visual components.
 * Removed `lambda/custom/util.js`. While this module is useful when resolving images and sounds from S3, this skill does not make use of it and any skill based on this template may never need it. If your skill needs it, then copy it from the official template project.
 * Moved `lambda/custom/local-debugger.js` to `utils/local-debugger.js` so that it won't be deployed to AWS Lambda with the skill code.
 * Removed the call to `.withCustomUserAgent()` in `lambda/custom/index.js` when building the skill. It's unclear what purpose this serves and you can certainly build and deploy a skill without it.
 * Rearranged intent declarations in `models/en-US.json` so that the "HelloWorldIntent" is first and all built-in intents follow. Also put "CancelIntent" and "StopIntent" adjacent to each other since their handler is the same.
 * Delete .git and .github folders from post-new hooks.
