# PROGRAMACIÓN DE SERVICIOS 2DAM - IES N1 XÀBIA
 
## Clase:
Una clase es una plantilla que define la forma de un objeto. Especifica los datos y el código que operará en esos datos. Java usa una especificación de clase para construir objetos. Los objetos son instancias de una clase. Por lo tanto, una clase es esencialmente un conjunto de planes que especifican cómo construir un objeto.
```java
public class Personaje{

}
```
## Objeto: 
Un objeto es un fichero en Java que contiene una serie de caracteristicas y un comportamiento, por ejemplo una puerta tiene color,forma,dimensiones,material,etc(caracteristicas) tambien puede abrise, cerrarse,etc(comportamiento).
```java
public class Puerta{

	//ATRIBUTOS
	private String nombre;
	private String material;
	
	//CONSTRUCTORES
	public Puerta(String nombre, string material){
		this.nombre=nombre;
		this.material=material;
	}

	//GETTERS Y SETTERS
	public String getNombre() {
		return nombre;
	}
	public void setNombre(String nombre) {
		this.nombre = nombre;
	}
	
	//TOSTRING
	public String toString() {
		return "---INFORMACIÓN DE LA PUERTA---\n"+"Nombre:"+ nombre + "\nMaterial:" + material;
	}
}
```
## Sobrecarga de métodos:
La sobrecarga de métodos es la creación de varios métodos con el mismo nombre pero con diferente lista de tipos de parámetros. Java utiliza el número y tipo de parámetros para seleccionar cuál definición de método ejecutar. 
```java
public class Escritor{
	public void Escribe(){
		System.out.println("No tengo parametros");
	}
	public void Escribe(int numero){
		System.out.println("Número: "+numero.toString());
	}
	public void Escribe(int numero, String texto){
		System.out.println("Número: "+numero.toString()+", Texto: "+texto);
	}
	public void Escribe(int numero, String texto, DateTime fecha){
		System.out.println("Número: "+numero.toString()+", Texto: "+texto+", Fecha: "+fecha.toString());
	}
}
```
## Herencia:
La herencia es un mecanismo que permite la definición de una clase a partir de la definición de otra ya existente. La herencia permite compartir automáticamente métodos y datos entre clases, subclases y objetos.  Un ejemplo seria el objeto humano, puede tener dos subclases hombre y mujer (ambos son humanos).

![alt text](https://jarroba.com/wp-content/uploads/2014/04/PolimorfismoFutbol-diag.jpg "Herencia")

* Clase Padre 
```java
public abstract class SeleccionFutbol {

	protected int id;
	protected String nombre;
	protected String apellidos;
	protected int edad;

	// constructores, getter y setter

	public void viajar() {
	     System.out.println("Viajar (Clase Padre)");
	}

	public void concentrarse() {
	     System.out.println("Concentrarse (Clase Padre)");
	}

	// IMPORTANTE -> METODO ABSTRACTO => no se implementa en la clase abstracta pero si en la clases hijas
	public abstract void entrenamiento();

	public void partidoFutbol() {
	     System.out.println("Asiste al Partido de Fútbol (Clase Padre)");
	}
}
```
* Clase Futbolista
```java
public class Futbolista extends SeleccionFutbol {

   private int dorsal;
   private String demarcacion;

   // constructor, getter y setter

   @Override
   public void entrenamiento() {
      System.out.println("Realiza un entrenamiento (Clase Futbolista)");
   }

   @Override
   public void partidoFutbol() {
      System.out.println("Juega un Partido (Clase Futbolista)");
   }

   public void entrevista() {
      System.out.println("Da una Entrevista");
   }
}
```
* Clase Entrenador
```java
public class Entrenador extends SeleccionFutbol {

   private int idFederacion;

   // constructor, getter y setter
	
   @Override
   public void entrenamiento() {
      System.out.println("Dirige un entrenamiento (Clase Entrenador)");
   }

   @Override
   public void partidoFutbol() {
      System.out.println("Dirige un Partido (Clase Entrenador)");
   }

   public void planificarEntrenamiento() {
      System.out.println("Planificar un Entrenamiento");
   }
}
```
* Clase Masajista
```java
public class Masajista extends SeleccionFutbol {

   private String titulacion;
   private int aniosExperiencia;

   // constructor, getter y setter
	
   @Override
   public void entrenamiento() {
      System.out.println("Da asistencia en el entrenamiento (Clase Masajista)");
   }

   public void darMasaje() {
      System.out.println("Da un Masaje");
   }
}
```
## Polimorfismo:
Es como la herencia pero esta dispone de diversas clases.

## Interface:
Una interfaz es un conjunto de metodos. En las interfaces se especifica qué se debe hacer pero no su implementación. Por ejemplo una interfaz de Audio incluiriamos dentro (MP3,FLAC,WAV...)
