<!--

author:   André Dietrich
email:    LiaScript@web.de
version:  0.1.0
language: en
narrator: US English Female

script:   https://unpkg.com/mermaid@9.1.1/dist/mermaid.min.js


@mermaid
<script run-once="true" modify="false">
mermaid.initialize({});

var svg = mermaid.render('io9wuwzxt',`@0`.replace(/\\n/g, "\n"),
function(g) {
    return true;
})

"HTML: " + svg
</script>
@end


@mermaid_eval
<script>
mermaid.initialize({});
var graphDefinition = `@input`
var cb = function(svgGraph) {
    return true;
}

var svg = mermaid.render('io9wuwzxt',graphDefinition,cb)
console.html(svg)
"LIA: stop"
</script>
@end

-->

# mermaid_template

                               --{{0}}--
This is a simple template for including [mermaidJS](https://github.com/knsv/mermaid)
graphs into LiaScript.

* See the mermaid docs [here...](https://mermaidjs.github.io/)
* See the Github version of this document [here...](https://github.com/liaScript/mermaid_template)
* See the LiaScript version of this document [here...](https://liascript.github.io/?https://raw.githubusercontent.com/liaScript/mermaid_template/master/README.md)

__Overview:__

1. Use plain HTML
2. Use the inline Macro to generate graphs
3. Use the Block-Macro notation
4. Dynamically generate graphs

## Plain - HTML

                              --{{0}}--
If you are on github, you should see some odd looking code here, in contrast to
LiaScript which tries to execute also JavaScript code.

<script style="display: block" run-once="true" modify="false">
mermaid.initialize({});

var svg = mermaid.render(
'io9wuwzxt',
`journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me`,
function(g) {
    return true;
})

"HTML: " + svg
</script>


## Inline

                              --{{0}}--
To simplify the usage of JavaScript libraries, LiaScript allows to define
macros, which allow to inject code during the parsing process. The following
macro, generates exactly the same graph as the previous example.

@mermaid(`flowchart LR\nid1(This is the text in the box)`)


## Code-Block

                              --{{0}}--
For more complex examples you can also use the block-code notation, that results
in a nicely rendered code on github, but on LiaScript it is converted to a graph.

```text @mermaid
graph TD
  A-->B
  A-->C
  B-->D
  D-->A
```

## Interactive

                              --{{0}}--
If you want to have an editable version of mermaid graphs, use the following
example. Simply double-click on the code to edit it and execute it by clicking
on the play-button.

```text
sequenceDiagram
    Alice->>+John: Hello John, how are you?
    Alice->>+John: John, can you hear me?
    John-->>-Alice: Hi Alice, I can hear you!
    John-->>-Alice: I feel great!
```
@mermaid_eval
