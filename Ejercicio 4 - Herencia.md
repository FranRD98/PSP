## EJERCICIO HERENCIA EN JAVA
##### En mi perfil dispones del proyecto para descargar. Este se encuentra aquí por temas de la asignatura.

## Directivo
```java
public class Directivo extends Empleado{

	Directivo(String nombre){
		super(nombre);
	}
	
	Directivo(){
		super();
	}
	
	//TOSTRING
	public String toString() {
		return super.toString() +" -> Directivo";
	}
}
```
## Empleado
```java
public class Empleado {
	private String nombre;
	
	//CONSTRUCTORES
	Empleado(String nombre){
		this.nombre=nombre;
	}
	
	Empleado(){
		
	}
		
	//SETTERS Y GETTERS
	public String getNombre() {
		return nombre;
	}
	
	public void setNombre(String nombre) {
		this.nombre = nombre;
	}

	//TOSTRING
	public String toString() {
		return "Empleado " +nombre;
	}		
}
```
## Oficial
```java
public class Oficial extends Operario{

	Oficial(String nombre){
		super(nombre);
	}
	
	Oficial(){
		super();
	}
	
	//TOSTRING
	public String toString() {
		return super.toString() +" -> Oficial";
	}	
}
```
## Operario
```java
public class Operario extends Empleado{

	Operario(String nombre){
		super(nombre);
	}
	
	Operario(){
		super();
	}
	
	//TOSTRING
	public String toString() {
		return super.toString() +" -> Operario";
	}	
}
```
## Tecnico
```java
public class Tecnico extends Operario{

	Tecnico(String nombre){
		super(nombre);
	}
	
	Tecnico(){
		super();
	}
	
	//TOSTRING
	public String toString() {
		return super.toString() +" -> Tecnico";
	}	
}
```
## Main
```java
public class Main {

	public static void main(String[] args) {
		Empleado E1 = new Empleado("Rafa");
		Directivo D1 = new Directivo("Mario");
		Operario OP1 = new Operario("Alfonso");
		Oficial OF1 = new Oficial("Luis");
		Tecnico T1 = new Tecnico("Pablo");
		System.out.println(E1);
		System.out.println(D1);
		System.out.println(OP1);
		System.out.println(OF1);
		System.out.println(T1);
	}
}
```

## RESULTADO
![alt text](https://i.imgur.com/JqUUcfJ.png "ResultadoHerencia")

