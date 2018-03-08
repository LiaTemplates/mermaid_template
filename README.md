<!--

author:   André Dietrich
email:    andre.dietrich@ovgu.de
version:  1.0.0
language: de_DE
narrator: Deutsch Female

script:   https://unpkg.com/mermaid@7.1.0/dist/mermaid.min.js

@mermaid
<script>
  var elem = document.getElementById("id@0");

  mermaid.initialize({startOnLoad:true});

  var graphDefinition = `@1`;
  var cb = function(svgCode) {
      elem.innerHTML = svgCode;
      elem.firstChild.style.height = elem.getAttribute('viewbox').split(' ')[3] + 'px';
  }
  mermaid.render(elem.id,graphDefinition,cb);
</script>
<span class="mermaid" id="id@0"></span>
@end

@mermaid_eval
<script>
var elem = document.getElementById('id@0');

if(elem != null)
  elem.remove();

mermaid.initialize({});
var graphDefinition = `{X}`
var cb = function(svgGraph) {
    return true;
}
mermaid.render('id@0',graphDefinition,cb)
</script>
@end

-->

# mermaid_template

Template for including mermaidJS graphs into LiaScript

## Plain - HTML

<link rel="stylesheet" href="https://unpkg.com/mermaid@7.1.0/dist/mermaid.css">

<script>
  var elem = document.getElementById("id");

  mermaid.initialize({startOnLoad:true});

  var graphDefinition = `graph TD\nA-->B\nA-->C\nB-->D\nD-->A\n`;
  var cb = function(svgCode) {
      elem.innerHTML = svgCode;

  }
  mermaid.render(elem.id,graphDefinition,cb);
</script>
<span class="mermaid" id="id"></span>


## Inline

<link rel="stylesheet" href="https://unpkg.com/mermaid@7.1.0/dist/mermaid.css">

@mermaid(1,`graph TD\nA-->B\nA-->C\nB-->D\nD-->A\n`)


## Code-Block

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

sss

## Interactive


```js
sequenceDiagram
    Alice->>+John: Hello John, how are you?
    Alice->>+John: John, can you hear me?
    John-->>-Alice: Hi Alice, I can hear you!
    John-->>-Alice: I feel great!
```
@mermaid_eval(3)


