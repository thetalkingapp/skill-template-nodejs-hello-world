# Skill project utilities

This folder contains a Node.js utility named `local-debugger.js` that will let you run your skill's lambda code locally, but interact with it through any Alexa device or virtual device associated with your Amazon account.

You'll first need to run `ngrok` to create a tunnel to your local machine:

    $ ngrok http 3001

Then deploy your skill using `ask new`, primarily for the interaction model and skill manifest. Once deployed, change the Service Endpoint Type in the Alexa developer console to the following:

 * Service Endpoint Type: HTTPS
 * URL: the HTTPS URL provided by `ngrok`
 * SSL Certificate Type: "My development endpoint is a sub-domain of a domain..."

You may also be able to set the service endpoint before deploying by editing `skill.json` to have the following in its "apis" property:

    "apis": {
        "custom": {
            "endpoint": {
                "uri": "https://d3eed21a.ngrok.io",
                "sslCertificateType": "Wildcard"
            },
            "interfaces": []
        }
    },

Finally, run the lambda code locally:

    $ node ./local-debugger.js --portNumber 3001 --skillEntryFile ../lambda/custom/index.js

Optionally, you may also setup VSCode to use this script for debugging so that you can set breakpoints and step through the code as you interact with the skill. In VSCode's "Debug->Add Configuration...", create a new configuration that looks like this:

    {
        "version": "0.2.0",
        "configurations": [
            {
                "type": "node",
                "request": "launch",
                "name": "Launch Program",
                "program": "${workspaceFolder}/utils/local-debugger.js",
                "args": [
                    "--portNumber", "3001",
                    "--skillEntryFile", "${workspaceFolder}/lambda/custom/index.js",
                    "--lambdaHandler", "handler"
                ],
            }
        ]
    }

Then start debugging from the "Debug->Start Debugging" menu item.
