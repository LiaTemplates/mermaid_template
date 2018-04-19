<!--

author:   André Dietrich
email:    andre.dietrich@ovgu.de
version:  1.0.0
language: en_US
narrator: US English Female

script:   https://unpkg.com/mermaid@7.1.0/dist/mermaid.min.js

@mermaid
<script>
  mermaid.initialize({});

  mermaid.render("id@0",
                 `@1`,
                 function(svgCode) {
                     var elem = document.getElementById("id@0");
                     elem.innerHTML = svgCode;
                     elem.firstChild.style.height = elem.getAttribute('viewbox').split(' ')[3] + 'px';
                 });
</script>
<span class="mermaid" id="id@0"></span>
@end

@mermaid_eval
<script>
var elem = document.getElementById('id@0');

if(elem != null)
  elem.remove();

mermaid.initialize({});
var graphDefinition = `{{0}}`
var cb = function(svgGraph) {
    return true;
}
mermaid.render('id@0',graphDefinition,cb)
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

<link rel="stylesheet" href="https://unpkg.com/mermaid@7.1.0/dist/mermaid.css">

<script>
  mermaid.initialize({});

  mermaid.render("id",
                 `graph TD\nA-->B\nA-->C\nB-->D\nD-->A\n`,
                 function(svgCode) {
                     //console.log(svgCode);
                     var elem = document.getElementById("id");
                     elem.innerHTML = svgCode;
                     elem.firstChild.style.height = elem.getAttribute('viewbox').split(' ')[3] + 'px';
                 });
</script>
<span class="mermaid" id="id"></span>


## Inline

                              --{{0}}--
To simplify the usage of JavaScript libraries, LiaScript allowes to define
macros, which allow to inject code during the parsing process. The following
macro, generates exactly the same graph as the previous example.

<link rel="stylesheet" href="https://unpkg.com/mermaid@7.1.0/dist/mermaid.css">

@mermaid(1,`graph TD\nA-->B\nA-->C\nB-->D\nD-->A\n`)


## Code-Block

                              --{{0}}--
For more complex examples you can also use the block-code notation, that results
in a nicely rendered code on github, but on LiaScript it is converted to a graph.

<link rel="stylesheet" href="https://unpkg.com/mermaid@7.1.0/dist/mermaid.css">

```js
@mermaid(2)

graph TB
    c1-->a2
    subgraph one
    a1-->a2
    end
    subgraph two
    b1-->b2
    end
    subgraph three
    c1-->c2
    end
```

## Interactive

                              --{{0}}--
If you want to have an editable version of mermaid graphs, use the following
example. Simply double-click on the code to edit it and execute it by clicking
on the play-button.

```js
sequenceDiagram
    Alice->>+John: Hello John, how are you?
    Alice->>+John: John, can you hear me?
    John-->>-Alice: Hi Alice, I can hear you!
    John-->>-Alice: I feel great!
```
@mermaid_eval(3)
