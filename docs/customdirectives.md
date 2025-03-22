
# custom directive 

A custom directive in Angular allows you to extend the behavior of DOM elements.
 Below is a clear and concise example of how to create a custom directive that changes 
 the background color of an element when the mouse hovers over it
 
## creat a custom directive 
 
```
ng generate directive hoverColor

```

## directive code in the directive.ts

```
// hover-color.directive.ts
import { Directive, ElementRef, Renderer2, HostListener } from '@angular/core';

@Directive({
  selector: '[appHoverColor]'  // This will be the selector used in the HTML
})
export class HoverColorDirective {

  constructor(private el: ElementRef, private renderer: Renderer2) { }

here in the el all the data will come from the html 

for example if we give hello angular in html and use custom direct when the el will the complete data 

here we need to give ElementRef as its type 

  // Listen for mouse enter event and change background color
  @HostListener('mouseenter') onMouseEnter() {
    this.changeBackgroundColor('yellow');
  }

  // Listen for mouse leave event and reset background color
  @HostListener('mouseleave') onMouseLeave() {
    this.changeBackgroundColor('white');
  }

  // Method to change background color
  private changeBackgroundColor(color: string) {
    this.renderer.setStyle(this.el.nativeElement, 'backgroundColor', color);
  }
}
```

## where we need to use in html file 
```
<!-- In your component HTML file -->
<div appHoverColor>
  Hover over this box to change its background color.
</div>
```

ts file (We need to import in the ts file)