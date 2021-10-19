## Se elige la plantilla html para el componente
```<h1 class="fs-1 mb-5 fw-bold d-flex justify-content-center">  </h1>
<form class=" w-50 d-flex justify-content-center mx-auto flex-wrap">
    <div class="mb-3 col-12">
      <label >  </label>
      <input type="number" class="form-control" >
    </div>
    <br>
    <div class="mb-3 mx-auto d-block col-12">
      <label >  </label>
      <input type="number" class="form-control" >
    </div>
    <button  type="submit" class="d-block btn btn-primary">  </button>
    <p class="fs-5 my-auto mx-auto">  </p>
  </form>
```


## Se agregan las respectivas interpolaciones
```<h1 class="fs-1 mb-5 fw-bold d-flex justify-content-center"> {{titulo}} </h1>
<form class=" w-50 d-flex justify-content-center mx-auto flex-wrap">
    <div class="mb-3 col-12">
      <label > {{a}} </label>
      <input type="number" class="form-control" >
    </div>
    <br>
    <div class="mb-3 mx-auto d-block col-12">
      <label > {{b}} </label>
      <input type="number" class="form-control" >
    </div>
    <button  type="submit" class="d-block btn btn-primary"> {{btnRes}} </button>
    <p class="fs-5 my-auto mx-auto"> {{resultado}} </p>
  </form>
  ```


# Estas interpolaciones haciendo referencias a lo que se halla en el componente.ts
```
import { Component } from '@angular/core';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  titulo = 'Aplicación Calculadora';
  a = 'operando';
  b = 'operando';
  btnRes = 'resultado'
}
```

# Se importa el FormsModule en el module.ts para usar la propiedad de two way binding, 
# y para hacer uso de esta propiedad, se escribe hacia qué variable se hace referencia del componente.ts, en este caso operandoA, operandoB
```export class AppComponent {
  titulo = 'Aplicación Calculadora';
  a = 'operando';
  b = 'operando';
  btnRes = 'resultado'
  operandoA: number = 0;
  operandoB: number = 0;
  resultado: number = 0;
}
}, 
```
mediante el uso de ngModel.


# Nota: Es importante definir el nombre de los inputs
```
<div class="mb-3 col-12">
      <label > {{a}} </label>
      <input type="number" class="form-control" [(ngModel)] = "operandoA" name = "operandoA">
    </div>
    <br>
    <div class="mb-3 mx-auto d-block col-12">
      <label > {{b}} </label>
      <input type="number" class="form-control" [(ngModel)] = "operandoB" name = "operandoB">
    </div>
```

# Mediante la propiedad event binding se vincula el botón con un evento click a la función de sumar ambos operandos.
```<button (click)="sumar()" type="submit" class="d-block btn btn-primary"> {{btnRes}} </button>
```

# Esta  función ubicada en el componente.ts
```
export class AppComponent {
  titulo = 'Aplicación Calculadora';
  a = 'operando';
  b = 'operando';
  btnRes = 'resultado'
  operandoA: number = 0;
  operandoB: number = 0;
  resultado: number = 0;
  
 
  sumar():void{
    this.resultado = this.operandoA + this.operandoB;
  }
}

```
