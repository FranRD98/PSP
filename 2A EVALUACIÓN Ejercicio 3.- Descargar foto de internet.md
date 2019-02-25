# EJERCICIO 3
## Crea una aplicación que descargue un fichero de internet.

```java
import java.io.FileOutputStream;
import java.io.InputStream;
import java.net.URL;
import java.net.URLConnection;
import java.util.Scanner;

public class Main {

	public static Scanner lector = new Scanner(System.in);
	public static void main(String[] args) {
		try {
			
			System.out.println("Índica el enlace donde se encuentra la imagen que quieres descargar.");
			String linkFoto = lector.nextLine();						
			
			// INDICAMOS LA RUTA DONDE SE ENCUENTRA LA FOTO QUE QUEREMOS DESCARGAR.
			URL urlFoto = new URL(linkFoto);

			// CONECTAMOS CON ESA URL PARA DESCARGAR LA IMAGEN.
			URLConnection urlConn = urlFoto.openConnection();
			
			// HACEMOS UNA VERIFICACIÓN PARA COMPROBAR QUE EL USUARIO QUIERE DESCARGAR LA FOTO CON EL FORMATO ENCONTRADO.
			String formatoCompleto = urlConn.getContentType().toString();						
			String formato=formatoCompleto.substring(formatoCompleto.lastIndexOf("/") + 1);
												
			System.out.println("Quiere descargar una imagen con formato "+formato+"?");
			
			System.out.println("¿Es correcto? (Y/N)");
			String respuesta = lector.nextLine();
			
			if(respuesta.equalsIgnoreCase("Y")) {
				
				// DEJAMOS QUE EL USUARIO INDIQUE LA RUTA DONDE GUARDAR LA IMAGEN.
				System.out.println("Índica la ruta donde quieres guardar la imagen.");
				String rutaGuardado = lector.nextLine();
								
				if(rutaGuardado.isEmpty()) {
					String usuarioActual = System.getProperty("user.name");
					rutaGuardado = "C:\\Users\\"+usuarioActual+"\\Desktop.";
				}

				// DEJAMOS QUE EL USUARIO INDIQUE LA RUTA DONDE GUARDAR LA IMAGEN.
				System.out.println("Índica el nombre de la imagen.");
				String nombreImagen = lector.nextLine();
				
				// OBTENEMOS UN INPUTSTREAM DE LA FOTO Y ABRIMOS EL FICHERO.
				InputStream is = urlConn.getInputStream();
				FileOutputStream fos = new FileOutputStream(rutaGuardado+"\\"+nombreImagen+"."+formato);
			
				// LEEMOS LA FOTO DE LA WEB Y LA PONEMOS EN EL FICHERO LOCAL.
				byte[] array = new byte[1000];
				int leido = is.read(array);
				
				while (leido > 0) {
					fos.write(array, 0, leido);
					leido = is.read(array);
				}
				
				//CERRAMOS LA CONEXIÓN Y LA LECTURA DEL FICHERO.
				is.close();
				fos.close();	
				
				System.out.println("La imagen se ha guardado correctamente en:");
				System.out.println(rutaGuardado+" con el nombre de "+nombreImagen+"."+formato);
			}

		} catch (Exception e) {
			e.printStackTrace();
		}
	}

}
