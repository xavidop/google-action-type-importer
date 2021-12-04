# Google Action Type Importer

This CLI allows you to transform you Alexa Custom Slots into Google Action types.

## Installation

You can download the latest realese from [here](https://github.com/xavidop/google-action-type-importer/releases)

## Hombrew

If you use the package manager Hombrew, you can intall this utility following these steps:

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

Easy right?