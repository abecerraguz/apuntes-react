# Create React APP

## Instalando un proyecto con React

~~~
	
	npx create-react-app basicos

~~~

El nombre del proyecto debe ser en minuscula 

## Iniciando un proyecto en React
~~~
	
	cd bisicos
	npm start

~~~

npm start Inicia nuestro servidor

## Se levanta un servidor Local y uno para poder ver el proyecto en la misma red
~~~
	
  Local:            http://localhost:3000
  On Your Network:  http://192.168.0.11:3000

~~~

## El Proyecto nos queda con la sgte estructura:
~~~
	
	  my-app
	├── README.md
	├── node_modules
	├── package.json
	├── .gitignore
	├── public
	│   ├── favicon.ico
	│   ├── index.html
	│   └── manifest.json
	└── src
	    ├── App.css
	    ├── App.js
	    ├── App.test.js
	    ├── index.css
	    ├── index.js
	    ├── logo.svg
	    └── serviceWorker.js

~~~

### Una ves creado nuestro proyecto tenemos tres carpetas:

#### node_modules
Es donde se instalan todas las dependencias, si abres el archivo package.json, este importara todas las dependencias como react,react-dom,react-script. Dentro de este archivo tenemos además los "script" estos definen comportaminetos o comandos como por ejemplo "npm start", "npm build", "test","eject".

#### Public
En esta carpeta tenemos nuestro index.html, podemos cargar hojas de estilos css y hay varias formas de incorporar estilo en React. Recuerda los campbios son imediatos dado que hemos levantado el servidor con "npm start", su visualización local es "http://localhost:3000/".

Es importante saber que todo nuestro código Javascript se va a inyectar en el div que tiene asigando el "id" root.

~~~js
	
	 Todo el Js lo inyecta en este div
	 <div id="root"></div>

~~~

Importante para que la data pase a al index.html, en el archivo index.js que esta en "src" le pasa el JS al index.html a través de:

~~~js
	
	 ReactDOM.render(
  		<React.StrictMode>
    		<App />
  		</React.StrictMode>,
  	    document.getElementById('root')
	);

~~~


#### Carpeta src
Es donde vamos a dejar todos nuestros componentes, también se crearan carpetas que necesiten proyectos de mayor complejidad. El archivo principal es el "index.js", este importa :

~~~js
	
	 import React from 'react';
	 import ReactDOM from 'react-dom';

~~~

#### Sintaxis de un componente

~~~js
	
	 ReactDOM.render(
  		<React.StrictMode>
    		<App />
  		</React.StrictMode>,
  	    document.getElementById('root')
	);

~~~

React.render toma dos parametros Qué va a mostrar? y donde lo va a Motrar. O sea va a mostra el <App /> en el selector document.getElementById('root'). El App esta en el componente "App.js" en especifico en:

~~~js
	
	function App() {
	  return (


	  );
	}

~~~

Los dos archivos proncipales son "index.js" que es el que muestra el componente principal y "App.js" que es el componente que me sirve para cargar otros componentes.

#### Crear el primer componente
Para crear nuestros componentes debemos crear una carpeta llamada "components" esta puede estar en la raiz que es el caso de Publimetro o dentro de la carpeta "src" caso de una APP.

Los componentes deben crear con la letra mayuscula al inicio ejemplo:

~~~
	
	Header.js
	Header.jsx

~~~

#### Pasos dentro del componente

~~~js

	// Se debe Importar React todos sus metodos y funciones
	import  React from 'react';

	// Antiguamente los componentes se definian como Clases hoy son funciones
	function Header(){
		// Antes del Return podemos escribir JavaScript, como var,const,let estructuras de control

		// Todo lo que este dentro del Return se va ver dentro de la pantalla
		return(
			<h1>Desde el Header</h1>

		);
	}
	// Importante debemos exportar el Header para que este sea importado
	export default Header;
	// Se debe importar en el componente principal "App.js"

~~~

#### Incorporar el componente Header.jsx en App.js
~~~js

	// import Header from './components/Header';
	// Para que se visualice debemos ir al App.js y crear la etiqueta <Header/>
	import React from 'react';
	import Header from './components/Header';


	function App() {
	return (
		<div className="App">
		// Etiqueta para la visualización del contenido
		<Header/>
		</div>
	);
	}

	export default App;

~~~

#### Componente Header.jsx
~~~js

// Se debe Importar React todos sus metodos y funciones
import  React from 'react';

// Antiguamente los componentes se definian como Clases hoy son funciones
function Header(){
    // Antes del Return podemos escribir JavaScript, como var,const,let estructuras de control
    const edad = 18;
    let mensaje;
    if(edad >= 18){
        mensaje = 'Eres Mayor de Edad'
    }else{
        mensaje = 'Eres Menor de Edad'
    }
    // Todo lo que este dentro del Return se va ver dentro de la pantalla
	return(
		// Los datos de JavaScript en archivos 'jsx' se rescatan en {}
        <h1>{edad}</h1>
    );
}

~~~

#### Como applicamos clases
Podemos aplicar clases ejemplo `class=nombreClase` a una etiqueta HTML, pero en React esto nos da error en la consola para esto la forma correcta de aplicar clase en React es:

~~~js

	return(
        <h1 className="encabezado">{edad}</h1>
    );

~~~

#### Creando un segundo componente
Vamos a crear un segundo componente este se llamara "Footer.js", existe otra forma de crear un componente que no es a través de una `function declaration` si no a traves de una `function expresion o de flecha` Ejemplo:

~~~js

	// Esto lo podemos escribir con el snippet "sfc"
	const Footer = () => {
		return ( 
			<footer>
				<p>Todos los derechos reservados</p>
			</footer>
		);
	}
	
	export default Footer;

~~~

En ambos casos las dos `function` realizan lo mismo pero la `function expresion`puede ser con menos codigo ejemplo:

~~~js

	const Footer = () => ( 
			<footer>
				<p>Todos los derechos reservados</p>
			</footer>
		);
	
	export default Footer;

~~~

Lo que le decimos es que entre el parentesis es el `return`, o sea logramos menos lineas.


#### Incorporración de Fragment
Existe dentro de React la habilidad de crear fragmentos, esto con la finalidad de no sobrecargar de `DIV` nuestos componentes ejemplo sin fragment:

~~~js

	import React from 'react';
	import Header from './components/Header';
	import Footer from './components/Footer';

	function App() {
	return (
		<div>
			<Header/>
			<Footer/>
		</div>
	);
	}

	export default App;

~~~

En este otro ejemplo incorporamos a `Fragment` para la no sobre utilización de `DIV` vacios ejemplo

~~~js
	// Podemos ampliar más habilidades de react en este caso {Fragment}
	// Este permite no sobre cargar de contenedores vacios o inecesarios
	import React { Fragment } from 'react';
	import Header from './components/Header';
	import Footer from './components/Footer';

	function App() {
	return (
		<Fragment>
		<Header/>
		<Footer/>
		</Fragment>
	);
	}

	export default App;

~~~

#### Que son los Props (Como fluyen los datos entre componentes)
Existen distintas formas como fluyen los datos entre componentes, usualmente en React los datos fluyen desde el componente Principal hacia los componentes internos, en este caso queremos pasar una dato desde el componente principal `App.js` hacia el componente `Header.jsx`. Ejemplo componente Principal:

~~~js

// Archivo Componente Principal
import React { Fragment } from 'react';
import Header from './components/Header';
import Footer from './components/Footer';

function App() {
  return (
    <Fragment>
	  <Header
		  // Le pasamos un dato desde el principal
		  // Podemos pasar Boleanos,numeros,string y hasta funciones, en este caso le pasaremos un string
		  titulo='Tienda Virtual' // Este dato lo pasamos a traves de los Props
	  />
      <Footer/>
    </Fragment>
  );
}

export default App;

~~~

Ahora pasamos los datos desde el componente `App.js` principal hacia el componente `Header.jsx`, esto se realiza a traves de los `Props` Ejemplo:

~~~js

	// Archivo Header.jsx
	import  React from 'react';

	function Header(props.titulo){
		console.log(props)
		return(
			<h1 className="encabezado">{props.titulo}</h1>
		);
	}
	export default Header;

	// Forma mas realizada en la cominidad de React

	function Header({titulo}){
		console.log(props)
		return(
			<h1 className="encabezado">{titulo}</h1>
		);
	}

~~~

También podemos pasar datos desde el componente padre `App.js` a traves de JavaScript todo esto antes del `return` ejemplo:

~~~js

  function App() {
  
  // Declaramos una const rescatando la fecha actual con JavaScript
  const fecha  = new Date().getFullYear();

  return (
    <Fragment>
	  <Header
		  // Le pasamos un dato desde el principal
		  // Podemos pasar Boleanos,numeros,string y hasta funciones, en este caso le pasaremos un string
		  titulo='Tienda Virtual' // Este dato lo pasamos a traves de los Props
	  />
	  <Footer
	  	// Asignamos el dato de la constante
        fecha={fecha}
      />
    </Fragment>
  );
}

~~~

Finalmente recibimos el dato desde el componente padre hacia el hijo

~~~js

	import React from 'react';

	// Esto lo podemos escribir con el snnipet sfc
	const Footer = ({fecha}) => {
		return ( 
			<footer>
				<p>Todos los derechos reservados &copy; {fecha}</p>
			</footer>
		);
	}
	
	export default Footer;

~~~

#### Introducción a React Hook

#### State React
El state es el encargado de hacer que React sea más rapido, en nuestro state vamos a colocar todo lo que va a reaccionar con los usuarios, el state reaccina a los datos del usuario





# Create React PUBLIMETRO

~~~
	
	 git clone repositorio
	 sudo npm install
	 npm run dev

~~~




