---
{"dg-publish":true,"permalink":"/01-reference/yaml/","title":"YAML Ain’t Markup Language","tags":["configuration","yaml"],"created":"2025-12-05T03:27:51.078+01:00"}
---


# YAML Ain’t Markup Language

YAML is a data serialisation language designed to be human-friendly and work well with modern programming languages for common everyday tasks. It is often used for configuration files that are parsed and read by a programming language or a framework. It's readable syntax format makes it easy for developers and system admins to understand and modify.

## Design goals

The design goals for YAML are, in decreasing priority:

- Should be easily readable by humans.
- YAML data should be portable between programming languages.
- Should match the native data structures of dynamic languages.
- Should have a consistent model to support generic tools.
- Should support one-pass processing.
- Should be expressive and extensible.
- Should be easy to implement and use.

## Basics syntax rules

- Case sensitive.
- Files should have .yaml as the extension.
- Does not allow usage of tabs, use spaces instead.
- As opposed to json, comments are supported with `#`
- Use indentation to denote structure
- List members are written with leading hyphen `-` each on it's own line but can also be enclosed in square brackets and separated with commas.

```yaml
# Block style list
List:
  - itemA
  - itemB

# Flow style list
List: [itemA, itemB]
```

- Associative arrays or dictionaries, also called maps or mapping values are represented using colon `:` in the format of key value pair. They are enclosed in curly braces `{key1: value1, key2: value2}`. A question mark can be used in front of a key if key have complex structure, like combination of `? key: value` both being a key to another value. They provide efficient mechanisms to retrieve values based on keys and organised data storage. The values can be of any type, including other nested dictionaries, lists, strings... anything.

```yaml
# Block style
employees:
  - name: Alice
    role: developer
    skills:
      - Python
      - Javascript
  - name: Bob
    role: designer
    skills:
      - Photoshop
      - Illustrator

# Flow style
employees:
  - { name: Alice, role: developer, skills: [Python, Javascript] }
  - { name: Bob, role: designer, skills: [Photoshop, Illustrator] }
```

- Strings can be unquoted but may be enclosed in double or single quotes.
- Multiple documents can be separated inside a single file using a `---` while document end is denoted with dots `...`. Using dots is optional since enclosing the document with hyphens `---` inherently ends it. Dots can be useful in cases where you need to explicitly denote the end in situations where document is followed by non-yaml content.

```yaml
---
# Document 1
title: "Document 1"
data:
  key1: value1
  key2: value2
...

---
# Document 2
title: "Document 2"
data:
  key3: value3
  key4: value4
...

# Non-YAML content can follow, or another YAML document can start with `---`
Some non-YAML content or metadata
```

- Use anchors `&` to define reusable nodes and aliases `*` to refer to previously defined node. Merge key `<<` to merge the content of an anchor into another node. Using anchors and aliases simplify the yaml files by avoiding redundancy and ensuring consistency. When dealing with large configuration files you can make them cleaner and easier to maintain.

```yaml
default_settings: &default
  resolution: 1080p
  frame_rate: 60
  aspect_ratio: 16:9

player1:
  <<: *default
  name: Player1
  controls:
    move_up: "W"
    move_down: "S"

player2:
  <<: *default
  name: Player2
  controls:
    move_up: "ArrowUp"
    move_down: "ArrowDown"

```

- To assign a tag to a node use ampersand `&`. To reference that node, use an asterisk `*`.

```yaml
name: Tom Nolan
bill-to:  &id01
  street: |
          123 Main Valley
          Room 16          
  city:   New York
  state:  NY

ship-to:  *id01
```

- In YAML, scalar values can be represented in various ways, including block notation, which allows for multi-line text. The `|` and `>` symbols are used to specify how line breaks and formatting should be treated.

- Literal block scalar, the `|` symbol is used when you want to preserve all the line breaks and formatting in the text exactly as it appears. It tells yaml to include the line breaks in the content. The text will be rendered with the exact formatting you see, including newlines and indentation. Useful for preformatted text, code blocks, or any content where exact formatting is crucial.

- Folded block scalar, the `>` symbol is used to fold newlines into spaces, which helps to produce a single-line output for text that is easier to read. It also allows for maintaining newlines when there are blank lines between paragraphs. Converts line breaks into spaces to produce more compact text. Maintains paragraph breaks with blank lines but removes other line breaks. Ideal for long texts that should appear as a single paragraph in the output.

```yaml
literal_block: |
  This block preserves line breaks.
  Each line is treated separately.
  
  Blank lines are kept as is.

folded_block: >
  This block folds newlines into spaces,
  so it will be displayed as a single
  line of text with spaces replacing
  line breaks.

  Paragraphs are separated by blank lines.
```

> In YAML, scalar values are simple, indivisible data values that can be represented in different ways. They include basic data types like strings, numbers, and booleans. Scalars are the most basic form of data you can work with in YAML, as opposed to more complex data structures like lists or maps. These include: Strings, Numbers, Boolean, Null, Date and Time,

```yaml
scalar_values:
  string_plain: This is a plain string.
  string_double_quoted: "This is a double-quoted string with a newline \n and a \"quote\"."
  string_single_quoted: 'This is a single-quoted string with a single quote '' inside it.'
  integer: 42
  float: 3.14
  boolean_true: true
  boolean_false: false
  null_value: null
  date: 2024-07-21
  datetime: 2024-07-21T14:30:00

```

## Reference

[yaml.org/documentation](https://yaml.org/) "Official" documentation and resources page. Check out  one of the version specifications at the top.
