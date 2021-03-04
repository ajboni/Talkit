## Hello! I'm currently working on a similar but more powerfull app which supports multiple dialogues with built in scripting, gdds, quest, etc.

## https://baj.itch.io/drafft

---

# Talkit

Web Based, Non-Linear Game Dialogue Editor.

#

Talkit is a fork of [etodd's](https://github.com/etodd) wonderful [The Poor Man's Dialogue Tree](https://etodd.io/2014/05/16/the-poor-mans-dialogue-tree/) which is currently part of [Lemma](https://github.com/etodd/Lemma) project.

## Description

Talkit is a Non-linear, node based, game dialog editor.
It runs on [jointJS](https://www.jointjs.com/). It exports to JSON with game ready content.
![alt text](https://i.imgur.com/7lu8NIy.png?1)

## Nodes

### Text

Display a message from the specified actor.
Actor: Specify the actor who will say the speech.
Speech: The text the actor will say.

### Choice

Intended to populate the players choices for responses.
Title: The title of the choice. This is useful for cases when the buttons the player would have to chose from
will differ from the actual speech he will say.
Speech: The text the actor will say.

### Set

Sets a variable to a value. Can link to one Text, Node, Set, or Branch.

### Branch

Takes one of several paths based on the value of a variable. Each port can link to one Text, Node, Set, or Branch.

### Node

Does nothing. Can link to one Text, Node, Set, or Branch, or to one or more Choices.

## Usage

Fire up the HTML, make your dialog and export.
You can add ?load="file.json" to the URL to load a graph saved on cache.
Example Output:

```javascript
[
  {
    type: "Text",
    id: "227b6f95-2759-4bda-8364-3bcbcb2cbf4d",
    actor: "Detective",
    name: "Now tell me Victor.\nWhere were you last night?",
    choices: [
      "b24806af-4923-4881-84c8-93426cbe3c19",
      "69261cd7-1cfe-4088-8c7c-99f19bc5fb25",
    ],
  },
  {
    type: "Choice",
    id: "69261cd7-1cfe-4088-8c7c-99f19bc5fb25",
    title: "Honest Answer",
    name: "I was at her house.\nBut I dind't saw anything strange.",
    next: "6e9f9c69-3efc-447b-ac3a-ade28635b106",
  },
  {
    type: "Choice",
    id: "b24806af-4923-4881-84c8-93426cbe3c19",
    title: "Lie",
    name: "",
    next: "fe9c4ac5-3f5a-4df1-91fe-e45b523017d7",
  },
  {
    type: "Set",
    id: "6e9f9c69-3efc-447b-ac3a-ade28635b106",
    variable: "Honest",
    value: "true",
    next: "fd3067f6-2afc-42e8-a697-2bb5739a8438",
  },
  {
    type: "Set",
    id: "fe9c4ac5-3f5a-4df1-91fe-e45b523017d7",
    variable: "Honest",
    value: "false",
    next: "fd3067f6-2afc-42e8-a697-2bb5739a8438",
  },
  {
    type: "Text",
    id: "fd3067f6-2afc-42e8-a697-2bb5739a8438",
    actor: "Detective",
    name: "That will be all for now.",
    next: null,
  },
];
```

## Not Implemented Yet - `TODO`:

- Add ?import="file.json" to import a graph from disk.
- Add the ability to make a node a starting node.
- Display the Id of the node on each node.
