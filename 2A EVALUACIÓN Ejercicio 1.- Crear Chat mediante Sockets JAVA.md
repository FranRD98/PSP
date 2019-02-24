# INTENTO 1:

Este dispone de 2 clases (Servidor y Cliente)

## Clase Servidor:
```java

import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.ServerSocket;
import java.net.Socket;
import java.util.Scanner;

public class Servidor {

	public static void main(String[] args) {
		try {
			ServerSocket server = new ServerSocket(9090);
			Socket socket = server.accept();
			
			DataInputStream dis = new DataInputStream(socket.getInputStream());
			DataOutputStream dos = new DataOutputStream(socket.getOutputStream());
				
			String res = dis.readUTF();
			System.out.println("Cliente dice: "+res);
			
			Scanner lector = new Scanner(System.in);
			String mes = lector.nextLine();
			System.out.println("Server: ");
			dos.writeUTF(mes);			
			
		} catch (IOException e) {
			e.printStackTrace();
		}				
	}
}```

## Clase Cliente:

import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;
import java.net.UnknownHostException;
import java.util.Scanner;

public class Cliente {

	public static void main(String[] args){
		try {
			Socket socket = new Socket("localhost",9090);
			
			DataInputStream dis = new DataInputStream(socket.getInputStream());
			DataOutputStream dos = new DataOutputStream(socket.getOutputStream());
			
			Scanner lector = new Scanner(System.in);
			System.out.println("Cliente: ");
			String mensaje = lector.nextLine();
			dos.writeUTF(mensaje);
			
			String res = dis.readUTF();
			System.out.println("Servidor dijo: "+ res);
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}





