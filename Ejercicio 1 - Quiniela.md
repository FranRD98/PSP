# EJERCICIO QUINIELA EN JAVA.
##### En mi perfil dispones del proyecto para descargar. Este se encuentra aquí por temas de la asignatura.
```java
public class Quiniela {
	public static void main(String[] args) {

		int valido=0, novalido=0;
		String jornada = "";
		char[] marks = { '1', 'X', '2' };

		int uno, equis, dos;

		for (int r1 : marks) {
		  for (int r2 : marks) {
		    for (int r3 : marks) {
		      for (int r4 : marks) {
		        for (int r5 : marks) {
		          for (int r6 : marks) {
		            for (int r7 : marks) {
		              for (int r8 : marks) {
		                for (int r9 : marks) {
		                  for (int r10 : marks) {
		                    for (int r11 : marks) {
		                      for (int r12 : marks) {
		                        for (int r13 : marks) {
                              for (int r14 : marks) {
			                          jornada = jornada + (char)r1 + (char)r2 + (char)r3 + (char)r4 + (char)r5 + (char)r6 + (char)r7 + (char)r8 + (char)r9 + (char)r10 + (char)r11 + (char)r12 + (char)r13 + (char)r14;

			// Contar resultados
			uno = jornada.split("1", -1).length-1;
			equis = jornada.split("X", -1).length-1;
			dos = jornada.split("2", -1).length-1;

			// Mirar casos
			// if(  uno<11 && uno>6 &&  equis<11 && equis>2 && dos<12 && dos>3 ) {
			if(  (uno>5 && uno<11) && (equis>2 && equis<6) && (dos>3 && dos<9) ) {
				valido++;
				System.out.println( jornada + " " + valido );
			}
			else {
				novalido++;
				System.out.println( "--------------" + novalido );
			}
			jornada = "";
			
		                          }
                             }
                            }
                           }
                          }
                         }
                        }
                       }
                      }
                     }
                    }
                   }
                  }		
                  
		
    // Resultados
		System.out.println( "Validos " + valido );
		System.out.println( "No validos " + novalido );
		
	}
}
