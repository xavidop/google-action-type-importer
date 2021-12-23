# Google Action Type Importer

This CLI allows you to transform your Alexa Custom Slots into Google Action Types.


- [Google Action Type Importer](#google-action-type-importer)
  - [Preface](#preface)
    - [Natural Language Understanding](#natural-language-understanding)
    - [Custom Types and their importance](#custom-types-and-their-importance)
  - [Installation](#installation)
    - [Hombrew](#hombrew)
  - [Usage](#usage)
    - [Import a Custom Slot of One Alexa Skill to a Gooogle Action type](#import-a-custom-slot-of-one-alexa-skill-to-a-gooogle-action-type)
    - [Example](#example)
  - [Resources](#resources)
  - [Conclusion](#conclusion)

<!-- /TOC -->

## Preface

### Natural Language Understanding

NLU or Natural Language Understanding is one field of AI that allows us to understand the users' input in the form of voice or text.

For that, you have to specify the interaction model. In terms of Google Assistant, will be the Voice Interaction Model or VUI. With the VUI you, as a Voice app developer, will specify how you are going to interact with the assistant. 

In Google Assistant you will create intents (Globals or specific to a Scene) that will contain Utterances. Those utterances will determine the same user action/intention. Also, those utterances can contain variables also called slots or entities. Each slot can have its Type. 

Having well-defined your VUI the NLU can identify what the user is requesting at any time:

![img](/img/nlu.png)
Photo from Chatbots Magazine.

### Custom Types and their importance

Google Assistant has its own custom types like `actions.type.Date`, `actions.type.DateTime`, `actions.type.Time` or `actions.type.Number`. It is important that if you are developing your Google Actions and you are working with your words, those that are specific/related to your business. you should create your custom Types. These types will be used by Google Assistant to train their AI and it will understand you while you are interacting with it. The usability of Google Action directly depends on how well the sample utterances and custom types values represent real-world language use.

This is why I created this tool, to properly transform your Custom Slots created on Alexa into Google Assistant Types.

## Installation

You can download the latest realese from [here](https://github.com/xavidop/google-action-type-importer/releases)
<!-- TOC -->

### Hombrew

If you use the package manager Homebrew, you can install this utility following these steps:

1. Add my Hombre tab:
```bash
brew tap xavidop/tap git@github.com:xavidop/homebrew-tap.git
brew update
```
1. Install the CLI:
```bash
brew install google-action-type-importer
```

## Usage

This is the Overview of the Tool:

```bash
➜  google-action-type-importer git:(master) ✗ google-action-type-importer 
Welcome to google-action-type-importer!

This utility provides you with an easy way to create custom types 
for your Google Actions projects importing those values from files. 

You can find the documentation at https://github.com/xavidop/google-action-type-importer/master/README.md.

Please file all bug reports on Github at https://github.com/xavidop/google-action-type-importer/issues.

Usage:
  google-action-type-importer [flags]
  google-action-type-importer [command]

Available Commands:
  completion  generate the autocompletion script for the specified shell
  help        Help about any command
  import      Imports a type
  version     Get google-action-type-importer version

Flags:
  -h, --help      help for google-action-type-importer
  -v, --verbose   verbose error output (with stack trace)

Use "google-action-type-importer [command] --help" for more information about a command.
```

### Import a Custom Slot of One Alexa Skill to a Gooogle Action type

To import an Alexa Slot, you have to have your slot in a CSV with the format that accepts [Alexa](https://developer.amazon.com/en-US/docs/alexa/custom-skills/create-and-edit-custom-slot-types.html):
```csv
Slot value,identifier,synonym,synonym,...
```

Having that file, you can execute the `import` subcommand:

```bash
➜  google-action-type-importer git:(master) ✗ google-action-type-importer import --help
Imports a type

Usage:
  google-action-type-importer import [flags]

Flags:
  -f, --file string        CSV to read (default "file.csv")
  -e, --header             Specifies if the CSV contains headers or not
  -h, --help               help for import
  -t, --type-name string   Type to create (default "type")

Global Flags:
  -v, --verbose   verbose error output (with stack trace)
```

### Example

```bash
google-action-type-importer import -f examples/pokemon.csv --header -t pokemon
```

The command above will create the file `pokemon.yaml`. You can find the examples in the `examples` folder.

Alexa Custom Slot:

![img](/img/alexa.png)

Google Assistant Custom Type:

![img](/img/google.png)

Easy right?

Enjoy!

## Resources
* [Official Google Assistant Node.js SDK](https://github.com/actions-on-google/assistant-conversation-nodejs) - Official Google Assistant Node.js SDK
* [Official Google Assistant Documentation](https://developers.google.com/assistant/conversational/overview) - Official Google Assistant Documentation
* [Official Google Actions Custom Types Documentation](https://developer.amazon.com/en-US/docs/alexa/custom-skills/alexa-entities-reference.html) - Official Google Actions Custom Types Documentation
  
## Conclusion 

As you can see you can port your Alexa Slots easily to your google Actions. Looking forward to seeing what you are going to develop!

I hope this tool is useful to you.

That's all folks!

Happy coding!
