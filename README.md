Esse é um modelo de cartões Anki que utilizo em minhas revisões sobre códigos. Dessa forma, eu consigo aprender tanto sintaxe quanto frameworks de qualquer linguagem de programação.

## Como usar

Baixe o arquivo `coding` e importe lá no Anki. Feito isso, é só usar o modelo de cartões chamado `Coding`.

### Modelo da frente

```javascript
<script>
// v1.1.8 - https://github.com/SimonLammer/anki-persistence/blob/584396fea9dea0921011671a47a0fdda19265e62/script.js
if(void 0===window.Persistence){var e="github.com/SimonLammer/anki-persistence/",t="_default";if(window.Persistence_sessionStorage=function(){var i=!1;try{"object"==typeof window.sessionStorage&&(i=!0,this.clear=function(){for(var t=0;t<sessionStorage.length;t++){var i=sessionStorage.key(t);0==i.indexOf(e)&&(sessionStorage.removeItem(i),t--)}},this.setItem=function(i,n){void 0==n&&(n=i,i=t),sessionStorage.setItem(e+i,JSON.stringify(n))},this.getItem=function(i){return void 0==i&&(i=t),JSON.parse(sessionStorage.getItem(e+i))},this.removeItem=function(i){void 0==i&&(i=t),sessionStorage.removeItem(e+i)},this.getAllKeys=function(){for(var t=[],i=Object.keys(sessionStorage),n=0;n<i.length;n++){var s=i[n];0==s.indexOf(e)&&t.push(s.substring(e.length,s.length))}return t.sort()})}catch(n){}this.isAvailable=function(){return i}},window.Persistence_windowKey=function(i){var n=window[i],s=!1;"object"==typeof n&&(s=!0,this.clear=function(){n[e]={}},this.setItem=function(i,s){void 0==s&&(s=i,i=t),n[e][i]=s},this.getItem=function(i){return void 0==i&&(i=t),void 0==n[e][i]?null:n[e][i]},this.removeItem=function(i){void 0==i&&(i=t),delete n[e][i]},this.getAllKeys=function(){return Object.keys(n[e])},void 0==n[e]&&this.clear()),this.isAvailable=function(){return s}},window.Persistence=new Persistence_sessionStorage,Persistence.isAvailable()||(window.Persistence=new Persistence_windowKey("py")),!Persistence.isAvailable()){var i=window.location.toString().indexOf("title"),n=window.location.toString().indexOf("main",i);i>0&&n>0&&n-i<10&&(window.Persistence=new Persistence_windowKey("qt"))}}
</script>

{{Frente}}

<div id="frente">
<textarea id="codeField" oninput="setValueAndPersist()"></textarea>

<pre id="pre" class="prettyprint"></pre>

<button onclick="indent()">Tab</button>
<button onclick="indent2()">Tab 2x</button>
</div>

<script>
var codeField = document.getElementById('codeField');
var pre = document.getElementById('pre');

function setValueAndPersist() {
pre.innerText = codeField.value;
Persistence.setItem(pre.innerHTML);}

function indent() {
codeField.value += ' '
}

function indent2() {
codeField.value += ' '
}

</script>

<script src="https://cdn.jsdelivr.net/gh/google/code-prettify@master/loader/run_prettify.js"></script>
```

### Modelo de trás

```javascript
<script> // v1.1.8 - https://github.com/SimonLammer/anki-persistence/blob/584396fea9dea0921011671a47a0fdda19265e62/script.js if(void 0===window.Persistence){var e="github.com/SimonLammer/anki-persistence/",t="_default";if(window.Persistence_sessionStorage=function(){var i=!1;try{"object"==typeof window.sessionStorage&&(i=!0,this.clear=function(){for(var t=0;t<sessionStorage.length;t++){var i=sessionStorage.key(t);0==i.indexOf(e)&&(sessionStorage.removeItem(i),t--)}},this.setItem=function(i,n){void 0==n&&(n=i,i=t),sessionStorage.setItem(e+i,JSON.stringify(n))},this.getItem=function(i){return void 0==i&&(i=t),JSON.parse(sessionStorage.getItem(e+i))},this.removeItem=function(i){void 0==i&&(i=t),sessionStorage.removeItem(e+i)},this.getAllKeys=function(){for(var t=[],i=Object.keys(sessionStorage),n=0;n<i.length;n++){var s=i[n];0==s.indexOf(e)&&t.push(s.substring(e.length,s.length))}return t.sort()})}catch(n){}this.isAvailable=function(){return i}},window.Persistence_windowKey=function(i){var n=window[i],s=!1;"object"==typeof n&&(s=!0,this.clear=function(){n[e]={}},this.setItem=function(i,s){void 0==s&&(s=i,i=t),n[e][i]=s},this.getItem=function(i){return void 0==i&&(i=t),void 0==n[e][i]?null:n[e][i]},this.removeItem=function(i){void 0==i&&(i=t),delete n[e][i]},this.getAllKeys=function(){return Object.keys(n[e])},void 0==n[e]&&this.clear()),this.isAvailable=function(){return s}},window.Persistence=new Persistence_sessionStorage,Persistence.isAvailable()||(window.Persistence=new Persistence_windowKey("py")),!Persistence.isAvailable()){var i=window.location.toString().indexOf("title"),n=window.location.toString().indexOf("main",i);i>0&&n>0&&n-i<10&&(window.Persistence=new Persistence_windowKey("qt"))}} </script>

{{FrontSide}}

<hr id="answer">

<p>You typed:</p>
<pre class="prettyprint"><div id="InputedCode"></div></pre>

<p>Expected: </p>
<pre class="prettyprint">{{ExpectedCode}}</pre>

{{Verso}}


<script>
var inputedCode = Persistence.getItem();

var inputedCodeDiv = document.getElementById('InputedCode')

inputedCodeDiv.innerHTML = inputedCode
</script>
```

### CSS
```css
.card {
 font-family: arial;
 font-size: 20px;
 text-align: center;
 color: black;
 background-color: white;
}

textarea {
 margin-top: 1rem;
}

pre {
 font-size: 12px;
 text-align: left;
}

/* Pretty printing styles. Used with prettify.js. */
/* Vim sunburst theme by David Leibovic */

pre .str, code .str { color: #65B042; } /* string - green */
pre .kwd, code .kwd { color: #E28964; } /* keyword - dark pink */
pre .com, code .com { color: #AEAEAE; font-style: italic; } /* comment - gray */
pre .typ, code .typ { color: #89bdff; } /* type - light blue */
pre .lit, code .lit { color: #3387CC; } /* literal - blue */
pre .pun, code .pun { color: #fff; } /* punctuation - white */
pre .pln, code .pln { color: #fff; } /* plaintext - white */
pre .tag, code .tag { color: #89bdff; } /* html/xml tag - light blue */
pre .atn, code .atn { color: #bdb76b; } /* html/xml attribute name - khaki */
pre .atv, code .atv { color: #65B042; } /* html/xml attribute value - green */
pre .dec, code .dec { color: #3387CC; } /* decimal - blue */

pre.prettyprint, code.prettyprint {
 background-color: #000;
 border-radius: 8px;
}

pre.prettyprint {
 width: 95%;
 margin: 1em auto;
 padding: 1em;
 white-space: pre-wrap;
}


/* Specify class=linenums on a pre to get line numbering */
ol.linenums { margin-top: 0; margin-bottom: 0; color: #AEAEAE; } /* IE indents via margin-left */
li.L0,li.L1,li.L2,li.L3,li.L5,li.L6,li.L7,li.L8 { list-style-type: none }
/* Alternate shading for lines */
li.L1,li.L3,li.L5,li.L7,li.L9 { }

@media print {
  pre .str, code .str { color: #060; }
  pre .kwd, code .kwd { color: #006; font-weight: bold; }
  pre .com, code .com { color: #600; font-style: italic; }
  pre .typ, code .typ { color: #404; font-weight: bold; }
  pre .lit, code .lit { color: #044; }
  pre .pun, code .pun { color: #440; }
  pre .pln, code .pln { color: #000; }
  pre .tag, code .tag { color: #006; font-weight: bold; }
  pre .atn, code .atn { color: #404; }
  pre .atv, code .atv { color: #060; }
}
```
