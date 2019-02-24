# INTENTO 1:

Este dispone de 2 clases (Servidor y Cliente)

## Clase Servidor:

```import java.io.DataInputStream;
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
}´´´

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
}```

INTENTO 2

Este dispone de 3 clases (Servidor, Cliente y Main)

## Clase Servidor:

```import java.io.IOException;
import java.net.ServerSocket;
import java.net.Socket;
import java.util.ArrayList;
import java.util.List;

public class Servidor {

	static void run() {
		try {
			int i = 1;
			ServerSocket serverSocket = new ServerSocket(9090);
			
			while(true) {
				Socket socket = serverSocket.accept();
				System.out.println("Funciona!");
				new Cliente(socket);
				i++;
			}
		} catch (IOException e) {
			e.printStackTrace();
		}	
	}
	static void enviarTodo(String mensaje) {
		for(Cliente handler : clientes) {
			handler.getOut().println(mensaje);				
		}
	}
	
	static List<Cliente> getHandlers(){
		return clientes;
	}
	
	private static List<Cliente> clientes = new ArrayList<Cliente>();
}```


## Clase Cliente:

```import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.io.PrintWriter;
import java.net.Socket;
import java.util.Scanner;

public class Cliente extends Thread{
	private Socket enCamino;
	private PrintWriter out;
	
	Cliente(Socket enCamino){
		this.enCamino = enCamino;
		this.start();
	}
	
	public void run() {
		try {
			try {
				Servidor.getHandlers().add(this);
				
				InputStream is = enCamino.getInputStream();
				OutputStream os = enCamino.getOutputStream();
				
				Scanner lector = new Scanner(is);
				out = new PrintWriter(os,true);
				
				out.println("dev::hubot.pl - Telnet Chat Demo");
				
				out.println("Elige el nick de tu chat:");
				String nick = "";
				nick = lector.nextLine();
				
				out.println("Bienvenido!, para salir escribe exit");
				
				boolean conexion = false;
				while (!conexion && lector.hasNextLine()){
					String line = lector.nextLine();
					Servidor.enviarTodo(nick + ": "+line);
					if (line.trim().equals("BYE"))
						conexion = true;
				}
			} finally {
				enCamino.close();
			}
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
	PrintWriter getOut() {
		return out;
	}
}```


## Clase Main:


```public class Main {

	public static void main(String[] args) {
		Servidor.run();
	}
}```



