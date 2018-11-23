## EJERCICIO VALIDAR NIF EN JAVA
##### En mi perfil dispones del proyecto para descargar. Este se encuentra aquí por temas de la asignatura.

```java
import java.util.*;

public class validarNIF {

	public static boolean validar(String dni) {		        
        String letraMayuscula = "";
             
        if(dni.length() != 9 || Character.isLetter(dni.charAt(8)) == false ) {
            return false;
        }
 
        letraMayuscula = (dni.substring(8)).toUpperCase();
 
        if(soloNumeros(dni) == true && letraDNI(dni).equals(letraMayuscula)) {
            System.out.println("El DNI es correcto.");
        	return true;
        }
        else {
        	System.out.println("El DNI es incorrecto.");
            return false;
        }
    }
 
        private static boolean soloNumeros(String dni) {
 
            int i, j = 0;
            String numero = "";
            String miDNI = "";
            String[] unoNueve = {"0","1","2","3","4","5","6","7","8","9"};
 
            for(i = 0; i < dni.length() - 1; i++) {
                numero = dni.substring(i, i+1);
 
                for(j = 0; j < unoNueve.length; j++) {
                    if(numero.equals(unoNueve[j])) {
                        miDNI += unoNueve[j];
                    }
                }
            }
 
            if(miDNI.length() != 8) {
                return false;
            }
            else {
                return true;
            }
        }
 
        private static String letraDNI(String dni) {
       
        int miDNI = Integer.parseInt(dni.substring(0,8));
        int resto = 0;
        String miLetra = "";
        String[] asignacionLetra = {"T", "R", "W", "A", "G", "M", "Y", "F", "P", "D", "X", "B", "N", "J", "Z", "S", "Q", "V", "H", "L", "C", "K", "E"};
 
        resto = miDNI % 23;
 
        miLetra = asignacionLetra[resto];
 
        return miLetra;
    }
	
	public static Scanner lector = new Scanner(System.in);
    public static void main(String[] args) {
				
		String dni;
			System.out.println("¿Cual es tu DNI?");
			dni=lector.nextLine();
			
			validar(dni);			
	}
}
```
