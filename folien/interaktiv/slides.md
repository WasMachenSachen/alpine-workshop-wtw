---
theme: default
highlighter: shiki 
background: "https://images.unsplash.com/photo-1530273973427-22351773250c?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1950&q=80"
class: "text-center"

# some information about the slides, markdown enabled
info: |
  ## Slidev
  Presentation slides for developers.
  Learn more at [Sli.dev](https://sli.dev)
---

<div class="py-6 bg-blue-200 bg-opacity-50 -mt-15">
<h1 class="py-5">Getting started with <span class="text-[#9313ce]">Alpine.js</span></h1> 

<p class="text-white">Workshop für das Modul Weaving the Web</p>

<p class="absolute bottom-0">15.06.21 // Tim Loges</p>
</div>

---
layout: two-cols
---

# Hallo zusammen 

<br/>
<br/>
<br/>
<br/>
<br/>

### Tim Loges

<br/>

### Bachelor Medieninformatik an der TH Köln
### Aktuell im Master Medieninformatik

::right::


<div class="flex items-center justify-center w-full h-full">
<div class="bg-blue-500 rounded-full h-35 w-35"></div>
</div>

---
class: "bg-[#5952e1] h-full text-white"
---

<h1 class="pb-20 font-bold text-center">Was ist Alpine.js?</h1>


- Frontend JS-Framework für (~~einfache~~) Logik
- Logik lebt im Markup (Geschmacksache)
- Reaktive, ohne die "Kosten" der großen Brüder wie Vue & React

<!-- 
Alpine ~9 kb
Vue ~ 23 kb
React ~ 3kb + React Dom ~40 kb
 -->

---
class: ''
---

<h1 class="pb-10 font-bold">Wann greife ich zu Alpine.js</h1>

<div class="!all:list-none">

- Erweitern von bereits bestehenden Seiten
- Ein- und Ausblenden von DOM-Elementen
- Styling basierend auf JS-Logic (Class binding)
- Two-Way binding
- Bonus: Transitions

</div>

<!-- 
x-transition:enter=""
x-transition:enter-start=""
x-transition:enter-end=""
x-transition:leave=""
x-transition:leave-start=""
x-transition:leave-end=""
-->

---
class: text-right
---

<h1 class="pb-10 font-bold">Und wann nicht</h1>

<div class="!all:list-none pr-5">

- Große Projekte mit viel Logik (Auslagern unnötig kompliziert)
- SPA (kein Konzept für Routing)
- Kein virtual Dom (Performance)
- ~~Dokumentation nur README~~

</div>

---
class: "text-center"
layout: two-cols
---

<div class="absolute inset-x-0 text-xl ">oder</div>
<div class="absolute inset-x-0 text-2xl bottom-40">Alpine.js initialisert sich selbst*</div>
<div class="absolute bottom-0 right-0 p-2 text-sm text-gray-500">*ab V3 muss Alpine.js initialisert werden</div>

# <span class="text-[#9313ce]">CDN</span>

<div class="w-1/2 h-10 my-10 border-r-2"></div>

## Script Tag



::right::

# <span class="text-[#9313ce]">Bundler</span> 

<div class="w-1/2 h-10 my-10 border-r-2"></div>

## import 'alpinejs'



---
layout: center
---

<div class="grid grid-cols-2 gap-10">
  <div class="flex items-center text-center">
    <span class="text-5xl font-semibold text-[#9313ce]">14<br>Directives</span>
  </div>
  <div class="h-full my-auto list-none border-l border-gray-400 border-opacity-25 !all:leading-8 !all:list-none">

  - x-data 
  - x-init 
  - x-show 
  - x-text 
  - x-html 
  - x-bind 
  - x-on
  - x-ref 
  - x-model 
  - x-if 
  - x-for 
  - x-transition  
  - x-spread 
  - x-cloak
  
  </div>
</div>

---
layout: center
---

<div class="grid grid-cols-2 gap-10">
  <div class="flex items-center text-center">
    <span class="text-5xl font-semibold text-[#9313ce]">6<br>Magic<br> Properties</span>
  </div>
  <div class="h-full my-auto list-none border-l border-gray-400 border-opacity-25 !all:leading-8 !all:list-none">

  - $el
  - $refs
  - $event
  - $dispatch
  - $nextTick
  - $watch
  
  </div>
</div>

---
class: ''
---

# Directive `x-data` 

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">

- Neuer "scope"
- Daten nur innerhalb der Kinder verfügbar
- Objekt!

</div>
<div v-click>

### Benutzung

```html 
<div x-data="{ name: 'wert' }">...</div>
```


</div>
</div>


<div v-click class="absolute pl-2 border-l-2 border-gray-400 bottom-10">

Alle anderen Directives brauchen mindestens ein `x-data`. Möchte man ein Directive nutzen, hat aber keine Daten, kann `x-data` auch mit einem leeren Object bzw. sogar komplett ohne gesetzt werden.

</div>

<!--
Slides sollen gleichzeitig auch Cheat-Sheets sein
-->

---
class: ''
---

# Directive `x-init` 

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8 ">

- wird nach Initialisierung ausgeführt
- Ausdruck (expression) oder Funktion möglich

</div>
<div v-click>

### Benutzung

```html 
<div x-data="{ ... }" x-init="[expression]"></div>
```
```html 
<div 
  x-data="{ name: 'wert' }" 
  x-init="name = andererWert">
</div>
```
```html
<div 
  x-data="{ name: 'wert' }" 
  x-init="setTimeout(function(){ alert(name); }, 3000);">
</div>
```
</div>
</div>

<div v-click class="absolute pl-2 border-l-2 border-gray-400 bottom-10">

Ab V3 kann `x-init` innerhalb von `x-data` deklariert werden und wird automatisch ausgeführt.

</div>


---
class: ""
---

# Directive `x-show` 

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">

- Blendet Elemente ein und aus 
- Setzt display: none entsprechend der expression
- Bonus: Transitions



 
</div>
<div v-click>

### Benutzung

```html 
<div x-show="[expression]"></div>
```

```html 
<div x-data="{ open: false }">
  <button x-on:click="open = true">Zeige dich</button>
  <p x-show="open">
    Ich bin anfangst nicht sichtbar
  </p>
</div>
```

</div>
</div>

<div v-click class="absolute pl-2 border-l-2 border-gray-400 bottom-10">

Je nach Browser & Hardware kann es vorkommen das Alpine.js länger zum initialisieren braucht als der Browser zum Rendern. Daher ist es sinnvoll Elemente initial auszublenden um flackern zu verhindern. 

`style="display: none"`

</div> 

---
class: ""
---

# Directive `x-show` Transitions

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">

- Einfache Animationen
- Kann [individualisiert](https://github.com/alpinejs/alpine#x-show) werden 

</div>
<div v-click>

### Benutzung

```html {0} 
<div x-show.transition="[expression]"></div>
```

```html {3}
<div x-data="{ open: false }">
  <button x-on:click="open = true">Zeige dich</button>
  <p x-show.transition="open">
    Ich bin anfangst nicht sichtbar
  </p>
</div>
```

```html
<div
  x-show.transition.scale.opacity.delay.50ms
>
```

</div>
</div>

<div v-click class="absolute pl-2 border-l-2 border-gray-400 bottom-10">

Ab V3 ist `x-show.transition` nur noch über Directive `x-transition` nutzbar!

</div> 
---
class: ""
---

# Directive `x-text`

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">

- bindet `innerText` von DOM Elementen 

</div>
<div v-click>

### Benutzung

```html 
<span x-text="[expression]"></span>
```

```html 
<div x-data="{ msg: 'Hallo' }">
  <span x-text="msg + ' zusammen'">
    <!-- Hallo zusammen -->
  </span>
</div>
```

</div>
</div>

# Directive `x-html`

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">

- entfernt in V.3
- bindet `innerHTML` von DOM Elementen 

</div>
<div v-click>

### Benutzung

```html 
<span x-html="[expression]"></span>
```

</div>
</div>

---
class: 'bg-[#5952e1] h-full text-white text-center'
layout: center
---

# Übung Nr. 1

Site-Banner mit wechselndem Text

<!--
Gibt es Fragen bis hier?
-->

---
class: ''
---

# Übung Nr. 1

Site-Banner mit wechselndem Text

<BrowserMockup><iframe src="/beispiel-aufgabe-1.html" frameborder="0" class="w-full"></iframe></BrowserMockup>

---
class: ''
---

# Übung Nr. 1

Site-Banner mit wechselndem Text

- `x-data` neuer scope
- `x-init` wird ausgeführt nach der Initialisierung
- `x-show` ein- und ausblenden von Elementen
- `x-text` bindet `innerText`

<br/>
<br/>
<div v-click>

1. `aufgabe-1.html` in `aufgaben/aufgabe-1` öffnen
2. p-tag ein- bzw. ausblenden 
3. Bonus: Transitions
   
</div>

<div class="flex justify-center">

<h2 class="text-[#9313ce] mt-20">Dauer 20 Minuten</h2>

</div>

<!--
Devtools zeigen
html aufbau zeigen
Recap:
Gab es Probleme?
Möchte jemand seine Umsetzung zeigen?
-->

---
class: ''
---

# Directive `x-bind:TYPE`

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">
  
- Setzt HTML Attribute
      
- Für `value` Attribute als auch für `boolean` Attribute

</div>

<div v-click>

### Benutzung

```html 
<div x-bind:[attribute]="[expression]"></div>
```

```html 
<div x-data="{ isDisabled : true }">
  
  <button x-bind:disabled="isDisabled">Versuch es</button>
</div>
// isDisabled = true
<button disabled="disabled">Versuch es</button>

// isDisabled = false
<button>Versuch es</button>
```

</div>
</div>

<div v-click class="absolute pl-2 border-l-2 border-gray-400 bottom-10">

Shorthand: `:TYPE`

</div> 

<!--
value attribute zb. placeholder bei input
bool attribute z.B disabled bei buttons
funktioniert für alle Attribute der HTML Spezifkation
-->

---
class: ''
---

# Directive `x-bind:class`

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">

- Anderer Aufbau als `x-bind:TYPE` !
- Übergabeparameter muss Objekt sein
- Objekt Aufbau: <br/>
  name: die Klasse die hinzugefügt wird <br/>
  wert: boolean der angibt ob die Klasse
        hinzugefügt wird

</div>
<div>

### Benutzung

```html {all|0}
<div x-bind:class="{ 'className': variable }"></div>
```

```html {0|2|5|all}
<!-- Mehrere Klassen -->
<div x-bind:class="{ 'className className2': variable }"></div>

<!-- Verschiedene Klassen bei unterschiedlichen expressions  -->
<div x-bind:class="{ 'text-red': warning, 'text-green': !warning }"></div>

```

</div>
</div>

<div v-click class="absolute pl-2 border-l-2 border-gray-400 bottom-10">

Shorthand: `:class`

</div> 

---
class: ''
---

# Directive `x-on:EVENT`

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">

- Event-Listener 
- Kann mit jedem verfügbaren Event genutzt werden 

</div>
<div v-click>

### Benutzung

```html 
<button x-on:[event]="[expression]"></button>
```

```html 
<button x-on:click="isOpen = true"></button>
```

</div>
</div>

<div v-click class="absolute pl-2 border-l-2 border-gray-400 bottom-10">

Shorthand: `@event`

</div> 

---
class: ''
---

# Directive `x-on:EVENT` Helfer (Ausschnitt)

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="!all:leading-8">

- `.away`: triggert Event nur wenn es ausserhalb ausgeführt wird
  
<div class="!all:mb-8">

- `.prevent`: verhindert native Funktionalität
- `.once`: Event wird nur einmal ausgeführt
- `.debounce`: Event wird nur alle Xms ausgeführt
- `.window`: Event wird an Window-Object statt an DOM-Element registriert

</div>
</div>
<div v-click class="leading-6">


```html 
<div x-on:click.away="isOpen = false"></div>
```

<br/>

```html 
<button type="submit" x-on:click.prevent="dontSubmitForm()"></button>
```

<br/>

```html 
<div x-on:hover.once="fetchData()"></div>
```
<br/>

```html 
<input x-on:input.debounce.750ms="fetchSomething()">
```
<br/>

```html 
<div x-on:resize.window="resized = true"></div>
```

</div>
</div>

---
class: ''
---

# Directive `x-ref`

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">

- stellt DOM-Elemente für die Nutzung mit `$refs` zur verfügung

</div>
<div>

### Benutzung

```html 
<div x-ref="[name]"></div>
<button 
  x-on:click="$refs.[name].innerText = 'Moin'"
></button>
```

```html {0|2|3|all}
<div x-data>
  <input x-ref="input" />
  <button x-on:click="$refs.input.value = '' ">
    Input leeren
  </button>
</div>
```

</div>
</div>

---
class: 'bg-[#5952e1] h-full text-white text-center'
layout: center
---

# Übung Nr. 2

Passwort Validator

---
class: ''
---

# Übung Nr. 2

Passwort Validator

<BrowserMockup><iframe src="/beispiel-aufgabe-2.html" frameborder="0" class="w-full h-full"></iframe></BrowserMockup>

---
class: ''
---

# Übung Nr. 2

Passwort Validator

- `x-bind` bindet Attribute oder Klassen
- `x-on` Event-Listener
- `x-ref` referenziert und stellt DOM-Element zur Verfügung 
- `$refs` zugriff auf `x-ref` 

<br/>
<br/>
<div v-click>

1. `aufgabe-2.html` in `aufgaben/aufgabe-2` öffnen
2. Passwort Hinweise je nach Zustand Grün oder Rot einfärben
3. Verhindern das Button "Account erstellen" gedrückt werden kann, sollten nicht alle Regeln eingehalten sein
4. BONUS: Passwort zeigen/verstecken

</div>
<div class="flex justify-center">

<h2 class="text-[#9313ce] mt-7">Dauer 20 Minuten + 10 Minuten Pause</h2>

</div>

<!--
html zeigen!
-->

---
class: ''
---

# Directive `x-model`

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">

- Two-way binding für:
  
  - `<input type="text">`
  - `<textarea>`
  - `<input type="checkbox">`
  - `<input type="radio">`
  - `<select>`

</div>
<div>

### Benutzung

```html 
<div x-data="{ nachricht: '' }">
    <input type="text" x-model="nachricht">

    <span x-text="nachricht">
</div>
```

```html {0|2-4|all}
<div x-data="{ nachricht: '' }">
    <input type="text" x-model="nachricht">

    <button x-on:click="nachricht = ''">Reset</button>
</div>
```

</div>
</div>

<!--
x-model sets and gets!
siehe beispiel 2
-->

---
class: ''
---

# Magic Prop `$dispatch`

<div class="grid grid-cols-2 mt-15 gap-x-4">
<div class="leading-8">

- Event Kommunikation
- Event wird nach "oben" weitergegeben

- `.window` Modifier
  - Für Kommunikation zwischen Komponenten

</div>
<div>

### Benutzung

```html
<div x-on:custom-event="console.log($event.detail.foo)">
    <button x-on:click="$dispatch('custom-event', { foo: 'bar' })">
</div>

```

```html {0|3|all}
<div
    x-data="{ title: 'Hello' }"
    x-on:set-title.window="title = $event.detail"
>
    <h1 x-text="title"></h1>
</div>

<div x-data>
    <button x-on:click="$dispatch('set-title', 'Hello World!')">...</button>
</div>
```

</div>
</div>

<!--
Wrapper für browser events.
element.dispatchEvent(new CustomEvent(...))
-->

---
layout: center
---

<div class="grid grid-cols-2 gap-10">
<div class="flex items-center text-center">
<span class="text-5xl font-semibold text-[#9313ce]">Alpine.js<br>V 3</span>
</div>
<div class="h-full my-auto list-none border-l border-gray-400 border-opacity-25 !all:leading-12 !all:list-none">

- Neue Dokumentation 
- Globales State Management 
- Bessere wiederverwendbarkeit

</div>
</div>

---
class: ''
layout: center
---

# Wie kann ich mit <span class="text-[#9313ce]">Alpine.js</span> weitermachen?

- [Dokumentation](https://alpinejs.dev/)
- [Code with Hugo](https://codewithhugo.com/tags/alpinejs/)
- [Alpine.js Examples](https://alpinejs.codewithhugo.com)
- [Awesome Alpine.js](https://github.com/alpine-collective/awesome)
- [Alpine.js Magic Helper](https://github.com/alpine-collective/alpine-magic-helpers)

---
class: 'bg-[#5952e1] h-full text-white text-center'
layout: center
---

# Übung Nr. 3

Notification System mit Events

---
class: ''
---

# Übung Nr. 3

Notification System mit Events

<BrowserMockup><iframe src="/beispiel-aufgabe-3.html" frameborder="0" class="w-full h-full"></iframe></BrowserMockup>

---
class: ''
---

# Übung Nr. 3

Notification System mit Events

- `x-model` Two-Way binding
- `$dispatch` Events zur Kommunikation

<br/>
<br/>
<div v-click>

1. `aufgabe-3.html` in `aufgaben/aufgabe-3` öffnen
2. Event dispatchen wenn Button gedrückt wird
3. Event Listener an Notification hängen
4. Je nach Event zugehöriges Icon anzeigen und Texte für Heading und Message setzen
5. Notification schließen wenn "close Button" gedrückt wird
6. BONUS: Transitions

</div>
<div class="flex justify-center">

<h2 class="text-[#9313ce] mt-20">Dauer 30 - 40 Minuten</h2>

</div>

<!--
html zeigen!
-->
