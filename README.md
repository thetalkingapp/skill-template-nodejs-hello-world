# Base Alexa Hello World Skill

### This is a simple "hello world" template for building Alexa skills

## What is this?

This template project is based on the official Hello World template at https://github.com/alexa/skill-sample-nodejs-hello-world in the `ask-cli-x` branch (for ASK CLI v2.x). This template adds a few things that are generally useful in most skills so that you can start a skill project without having to add these manually.

If you find this template useful, you might also want to check out [my book](https://pragprog.com/book/cwalexa/build-talking-apps) where I use this template as the starting point for a skill that is built throughout the book.

And, please follow me on Twitter at [@habuma](https://twitter.com/habuma) (my personal, any topic is fair game handle) and [@thetalkingapp](https://twitter.com/thetalkingapp) (voice-app related tweets only).

## How do I use it?

You may simply `git clone` this repository and start developing your own skill on top of it. Or you may use the ASK CLI to clone it for you.

If you are using ASK CLI v1 (the one that is commonly used at this time), you will need to use the `--url` parameter to reference a template list JSON file that references this repository. For example:

    $ ask new --template-url https://github.com/thetalkingapp/skill-template-nodejs-hello-world.git

And select the "Hello World (simple)" template. You'll then be asked to give the project a name; use any name you wish. Then you'll be warned that the template is from an unofficial resource and be asked if you wish to continue. Answer "y" and the project will be created on your machine for you.

## What do I do next?

Once the project has been created, you can tweak the skill to do whatever you want. When you're ready, you can use the ASK CLI to deploy it:

    $ ask deploy

After a few moments, it will deployed and ready to try out. You can use your Alexa device to test it or use `ask dialog` to kick the tires:

    $ ask dialog --locale en-US
      User  > open hello world
      Alexa > Welcome, you can say Hello or Help. Which would you like to try?
      User  > say hello
      Alexa > Hello World!
      User  > .quit

## What's different?

Specifically, this project differs from the official template in the following ways:

 * Removed `AMAZON.NavigateHomeIntent` from `skill-package/interactionModels/custom/en-US.json`. This intent only makes sense when developing a skill that targets a screen-based device such as Echo Show. It's unnecessary for a simple Hello World skill that doesn't have visual components.
 * Added the `i18next` module and `LocalisationRequestInterceptor` in `lambda/index.js` to enable externalization of string messages. String messages are maintained in `lamdba/languageStrings.js`.
 * Added `AMAZON.FallbackIntent` in `skill-package/interactionModels/custom/en-US.json` and a corresponding request handler in `lambda/index.js`.
 * Include sample template JSON files for creating ISPs. This is to replace the files created by `ask add isp` in ASK CLI v1 which is no longer available in ASK CLI v2. These files have no bearing on the deployed skill and are only provided as a convenience. If your skill isn't going to have any in-skill products, then they can be deleted.
