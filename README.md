# Security Engineer Challenge

> This repository contains the challenge for the security engineers.

Note: Please don't fork this repository, or create a pull request against it. Otherwise other applicants may take inspiration from it. Once the coding challenge is completed, you can submit it via this [Google form](https://docs.google.com/forms/d/e/1FAIpQLSeVpv4gvm9naELQZjSl8huR4mA_x4N7-qrC3fWf34I8aTeEjg/viewform).

## Engine Exercise

The engine exercise should be contained in one repository, with the following structure:

```bash
├── <source files>
├── test-src/
├── tools/
├── Dockerfile
└── README.md # documentation for this repo
```

The `Dockerfile` should follow best practices (unprivileged user, small images size, etc).
The `tools` folder shall contain a `build.sh` script that builds the image, and a `run.sh` script that can execute the image against the `test-src` folder.
The `test-src` folder shall contain the source code of [NodeGoat](https://github.com/OWASP/NodeGoat).
The `source files` can be written in any language, chose whatever you think makes the most sense.

## Objectives

The objective of this challenge is to containerize [NodeJsScan](https://github.com/ajinabraham/NodeJsScan) and transform the output of the tool to the following structure:

```json
{
  "engine": {
    "name": "guardrails/engine-javascript-nodejsscan",
    "version": "1.0.0"
  },
  "process": {
    "name": "nodejsscan ",
    "version": "3.4"
  },
  "language": "javascript",
  "status": "success",
  "executionTime": 212, //in milliseconds
  "issues": 10, // number of identified issues
  "output": [
    // array containing all identified issues
    {
      "type": "sast", // This is static
      "ruleId": "Server Side Injection(SSI) - eval", // this is the title of the issue
      "location": {
        "path": "app/routes/contributions.js", // path to the file where the issue was identified
        "positions": {
          "begin": {
            "line": 26 // line number where the issue was identified
          }
        }
      },
      "metadata": {
        "description": "User controlled data in eval() can result in Server Side Injection (SSI) or Remote Code Execution (RCE)."
      }
    } // [...]
  ]
}
```

**Things that are expected:**

Overall make sure that you use meaningful commit messages and write clean code.
Wherever you’d have to add something that you feel requires product subscriptions or significant extra time, just mention it in the README.md file.

**Things you don’t have to worry about:**

- CI configuration / Deployment
- Secret Management
