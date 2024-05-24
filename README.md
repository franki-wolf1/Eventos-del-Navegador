# Eventos-del-Navegador
En Angular, el decorador @HostListener se utiliza para escuchar varios eventos del host, que puede ser el componente o la ventana del navegador. Aquí te doy una descripción de otros eventos comunes que puedes escuchar, similares a window:beforeunload.

Eventos del Navegador
window:unload:

Este evento se dispara cuando la ventana está a punto de descargarse. A diferencia de beforeunload, no permite cancelar la descarga.
typescript
Copiar código
@HostListener('window:unload', ['$event'])
unloadHandler(event: Event): void {
  console.log('Window is unloading');
}
window:resize:

Este evento se dispara cuando se cambia el tamaño de la ventana del navegador.
typescript
Copiar código
@HostListener('window:resize', ['$event'])
onResize(event: Event): void {
  console.log('Window resized');
}
window:scroll:

Este evento se dispara cuando se desplaza la ventana del navegador.
typescript
Copiar código
@HostListener('window:scroll', ['$event'])
onScroll(event: Event): void {
  console.log('Window scrolled');
}
window:click:

Este evento se dispara cuando se hace clic en cualquier parte de la ventana del navegador.
typescript
Copiar código
@HostListener('window:click', ['$event'])
onClick(event: MouseEvent): void {
  console.log('Window clicked');
}
window:keydown:

Este evento se dispara cuando se presiona una tecla en el teclado mientras la ventana tiene el foco.
typescript
Copiar código
@HostListener('window:keydown', ['$event'])
onKeydown(event: KeyboardEvent): void {
  console.log('Key pressed:', event.key);
}
Eventos del Document
document:visibilitychange:
Este evento se dispara cuando cambia la visibilidad del documento (por ejemplo, cuando la pestaña se oculta o se muestra).
typescript
Copiar código
@HostListener('document:visibilitychange', ['$event'])
onVisibilityChange(event: Event): void {
  console.log('Document visibility changed');
}
Eventos de Elementos HTML
element:mouseenter y element:mouseleave:

Estos eventos se disparan cuando el puntero del ratón entra y sale de un elemento, respectivamente.
typescript
Copiar código
@HostListener('mouseenter', ['$event'])
onMouseEnter(event: MouseEvent): void {
  console.log('Mouse entered element');
}

@HostListener('mouseleave', ['$event'])
onMouseLeave(event: MouseEvent): void {
  console.log('Mouse left element');
}
element:focus y element:blur:

Estos eventos se disparan cuando un elemento gana o pierde el foco, respectivamente.
typescript
Copiar código
@HostListener('focus', ['$event'])
onFocus(event: FocusEvent): void {
  console.log('Element focused');
}

@HostListener('blur', ['$event'])
onBlur(event: FocusEvent): void {
  console.log('Element lost focus');
}
Eventos de Formulario
submit:

Este evento se dispara cuando se envía un formulario.
typescript
Copiar código
@HostListener('submit', ['$event'])
onSubmit(event: Event): void {
  event.preventDefault();
  console.log('Form submitted');
}
input:

Este evento se dispara cuando el valor de un elemento de entrada cambia.
typescript
Copiar código
@HostListener('input', ['$event'])
onInput(event: Event): void {
  const input = event.target as HTMLInputElement;
  console.log('Input changed:', input.value);
}
Uso de @HostListener
El decorador @HostListener se puede aplicar a cualquier método en una clase de componente para escuchar eventos en el host de ese componente. Aquí hay un ejemplo genérico de cómo se usa:

typescript
Copiar código
import { Component, HostListener } from '@angular/core';

@Component({
  selector: 'app-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss']
})
export class ExampleComponent {

  @HostListener('window:resize', ['$event'])
  onResize(event: Event): void {
    console.log('Window resized');
  }

  @HostListener('window:scroll', ['$event'])
  onScroll(event: Event): void {
    console.log('Window scrolled');
  }

  @HostListener('click', ['$event'])
  onClick(event: MouseEvent): void {
    console.log('Element clicked');
  }

  @HostListener('window:keydown', ['$event'])
  onKeydown(event: KeyboardEvent): void {
    console.log('Key pressed:', event.key);
  }
}
Conclusión
El decorador @HostListener es una poderosa herramienta en Angular para escuchar eventos del host y del navegador de una manera declarativa y limpia. Esto permite que los componentes respondan a eventos globales como cambios de tamaño de la ventana, desplazamientos, clics y más, manteniendo el código modular y fácil de mantener.
