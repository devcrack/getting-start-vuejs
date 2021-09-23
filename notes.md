# Directivas
Atributos especiales en las etiquetas html. Las directivas son facilmente identificables con el prefijo **v-**, esto le indica a vuejs hacer algo en el DOM para aplicar cambios en este.

Ejemplo:
```
<element v-directivaId="[argumento:] expresion [|filtros..]>
</element>
```

Mas ejemplos de directivas en VUEJS:
<br>
Estas 2 directivas son equivalentes, lo que hacen es mostrar el valor de la variable mensaje
```html
<span>{{mensaje}}</span>
<span v-text="mensaje"></span>
```

## Directivas condcionales y Ciclos


```javascript
data:{
    show:true,
    usuarios:[
        {nombre:"Groover"},
        {nombre:"Maria"},
    ]
}
```
### **v-if**
Si show es verdadero mostrar "Hola", si show es falso mostrar
"Bye"
<p v-if="show">Hola</p>
<p v-else>Bye</p>

### v-show
Es semejante al caso anterior solo que aqui no tenemos condicional, pero aqui directamente hacemos la comparacion con respecto true:
<p v-show>

### For-loop
Sirve para recorrer colecciones como arreglos y listas, al momento de recorrer la coleccion podemos realizar 
manipulaciones de cada elemento que se encuentra en la coleccion.

```html
<li v-for="user in usuarios">{{user.nombre}}</li>
```

## Ejmemplos y Ejersicios Simples
### Data Binding

Aqui podemos ver como en control input, se enlaza automaticamente con el modelo entrada que esta definido con el identificador de entrada, en la instancia de vuejs. 
Los cambios en el valor del modelos entrada se veran reflejados automaticamente, en donde se este usando el modelo.

```html
<div id="app">
<h1>{{entrada}}</h1>
<input type="text" v-model="entrada">
</div>
```

```javascript
new Vue({
el:"#app",
data: //Aqui indicamos lo valores que queremos mostrar/usar en la vista
	{
		entrada:"Hola"
	}
})
```

### Enlazar datos desde la vista hacia el modelo pero atraves de un atributo de una etiqueta en la vista.

En el siguiente ejemplo vemos como enlazamos el valor que tenemos en el modelo url, para pasarlo como valor al atributo href. Para esto usamos la directiva v-bind.
```html
<div id="app">
<h1>{{entrada}}</h1>
<input type="text" v-model="entrada">
<br>
<a v-bind:href="url">Ir a Youtube</a>
</div>
```

```javascript
new Vue({
el:"#app",
data: //Aqui indicamos lo valores que queremos mostrar en la vista
	{
		entrada:"Hola",
        url:"https://www.youtube.com/",
	}
})
```

Binding

Binding viene del ingles Union/Uniones.

Al hacer data-binding lo que hacemos es unir el manejo del dato, del objeto data que se tiene en la instancia de VueJS, donde podemos almacenar varios valores, pudiendolos hacer interactuar en la vista, dicha interaccion o enlace entre la instancia de Vuejs y la vista es el data-binding. 


### Data Binding a Doble Via

En el siguiente ejemplo vemos como se usa un data-binding a doble via, donde vamos almacenando los valores de un input en este caso tipo checkbox en un arreglo. 

```html
<div id="app">
  <form action="">
    <input type="text" v-model="options"><br>
    <input type="checkbox" value="opcion-1" v-model="options">Opcion1
    <input type="checkbox" value="opcion-2" v-model="options">Opcion2
    <input type="checkbox" value="opcion-3" v-model="options">Opcion3
    <p>
      Selecciono: {{options.join(",")}}
    </p>
  </form>
</div>
```

```javascript
new Vue({
el:"#app",
data: //Aqui indicamos lo valores que queremos mostrar en la vista
	{
  	options:[], // Aqui guardaran los valores de cada checkbox
		entrada:"Hola"
	}
})
```

### Listas usando la directiva v-for

Creacion de una lista haciendo uso de la directiva **v-for** 
<br>
Motrar en una lista desordenada los numeros del 1 al 5
```html
<div id="app">
    <ul>
        <li v-for="n in 5">{{n}}</li>
    </ul>
</div>
```
<br>
Mostrar los numeos del 10 al 1:

```html
<div id="app">
    <ul>
        <li v-for="n in 10">{{11-n}}</li>
    </ul>
</div>
```
<br>
Semejante al caso anterior pero listando los valores almacenados en una lista:

```html
<div id="app">
<ul>
  <li v-for="n in contador">{{n}}</li>
</ul>
</div>
```

```javascript
new Vue({
el:"#app",
data: //Aqui indicamos lo valores que queremos mostrar en la vista
	{
  	options:[],
		entrada:"Hola",
    contador:[10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
	}
})
```

### Matriz con notacion indice
En el siguiente ejemplo vemos como utilizamos la directiva v-for para recorrer arreglos tambien usando la notacion de indice para acceder a los valores de un arreglo.

```html
<div id="app">
<ul>
  <li v-for="animal, i in animales">{{n}}
    El animal {{animal}} hace el sonido {{sonido[i]}}
  </li>
</ul>
</div>
```

```javascript
new Vue({
el:"#app",
data: //Aqui indicamos lo valores que queremos mostrar en la vista
	{
  	animales:["Gato", "Perro", "Pajaro"],
    sonido: ["Miau", "Woof", "Tweet!"]
	}
})
```

Resultado obtenido:
<br>
<br>
- El animal Gato hace el sonido Miau
- El animal Perro hace el sonido Woof
- El animal Pajaro hace el sonido Tweet!

<br>
<br>
Mismo caso anterior pero ahora en lugar de utilizar un arreglo para almacenar los valores utilizamos un objeto:

```html
<div id="app">
<ul>
  <li v-for="sonido, nombre in animales">
    El animal {{nombre}} hace el sonido {{sonido}}
  </li>
</ul>
</div>
```

```javascript
new Vue({
el:"#app",
data: //Aqui indicamos lo valores que queremos mostrar en la vista
	{
  	animales:
    {
    	Gato: "Miau",
     	Perro: "Woof",
        Pajaro: "Tweet!"
    }
	}
})
```

El resultado obtenido es exactamente el mismo que en el caso anterior.


## Objeto Methods
El objeto methods, es un objeto que forma parte de la instancia de Vuejs. Dicho objeto methods puede contener dentro de si varias funciones. Dichas funciones podran realizar diferentes tipos de acciones.


Ejemplo: Mostramos el metodo desde la vista 

```html
<div id="app">
{{mostrar_titulo()}}
</div>
```

```javascript
new Vue({
el:"#app",
data: //Aqui indicamos lo valores que queremos mostrar en la vista
	{
  	
	},
methods:{
	    mostrar_titulo:function(){
  	    return 'Hola Mundo desde Methods'
    }
    }  
})
```

### Directiva **v-once**

Esta directiva nos evita hacer el doble renderizado, que podemos tener en nuestro codigo. 

Ejemplo: 
<br>
Si hacemos lo siguiente veremos que el valor mostrador sera el mismo ya que VueJS es reactivo, entonces esa caracteristica de 
Vuejs hace que en todas las llamadas de la variable sea modificada, ya que se hace un doble renderizado. 

```html
<div id="app">
<h1>
  {{titulo}}
</h1>
{{mostrar_titulo()}}
</div>
```
```javascript
new Vue({
el:"#app",
data: //Aqui indicamos lo valores que queremos mostrar en la vista
	{
  	titulo: "Hola Mundo desde Vuejs"	
	},
methods:{
	mostrar_titulo:function(){
  	this.titulo = "Hola Mundo desde Methods"
  	return this.titulo
  }
}  
})
```

Para evitar este comportamiento podemos usar la directiva **v-once** . Esto nos permite mostrar el valor como se obtiene al momento de llamarlo sin importar que se cambie posteriormente.



```html
<div id="app">
<h1 v-once>
  {{titulo}}
</h1>
{{mostrar_titulo()}}
</div>
```
```javascript
new Vue({
el:"#app",
data: //Aqui indicamos lo valores que queremos mostrar en la vista
	{
  	titulo: "Hola Mundo desde Vuejs"	
	},
methods:{
	mostrar_titulo:function(){
  	this.titulo = "Hola Mundo desde Methods"
  	return this.titulo
  }
}  
})
```

### Directiva **v-html**
Esta directiva se usa con el fin de dar formato un codigo, que puedo tenerlo almacenado y que puedo manipularlo con codigo html. Esto puede ser util cuando tienes codigo guardado en la base de datos o en tu modelo, pero para que vue lo interprete como codigo html se hace uso de esta directiva.
<br>
Ejemplo:
```html
<div id="app">
<h1 v-once>
  {{titulo}}
</h1>
{{mostrar_titulo()}}
<p v-html="enlace_html">
</p>
</div> 
```

```javascript
new Vue({
el:"#app",
data: //Aqui indicamos lo valores que queremos mostrar en la vista
	{
  	titulo: "Hola Mundo desde Vuejs",
    enlace_html:"<a href='https://www.google.com.mx/'>Ir a Google</a>"
	},
methods:{
	mostrar_titulo:function(){
  	this.titulo = "Hola Mundo desde Methods"
  	return this.titulo
  }
}
  
})
```

