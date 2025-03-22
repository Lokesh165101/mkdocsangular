```
pipes.html
<h2>Using Pipes in Angular</h2>
<p>Original String: {{ 'Hello Angular' }}</p>
<p>Uppercase: {{ 'Hello Angular' | uppercase }}</p>
<p>Lowercase: {{ 'Hello Angular' | lowercase }}</p>
<p>Date: {{ today | date:'fullDate' }}</p>
<p>Currency: {{ 12345.67 | currency:'USD':'symbol':'1.2-2' }}</p>
<p>JSON: {{ { name: 'Angular', version: 12 } | json }}</p>

no import is required in ts for inbuild pipe 
```