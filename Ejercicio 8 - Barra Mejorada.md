## EJERCICIO BARRA DE TAREAS MEJORADA EN JAVA
##### En este repositorio dispones del proyecto para descargar.

![alt text](https://i.imgur.com/mmuZFQ3.png "BarraDeTareasMejorada")

```java
import java.awt.EventQueue;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.border.EmptyBorder;
import javax.swing.Icon;
import javax.swing.ImageIcon;
import javax.swing.JButton;
import javax.swing.JLabel;
import java.awt.Font;
import java.awt.Image;
import java.awt.Color;
import java.awt.Toolkit;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Barra extends JFrame {

	private JPanel contentPane;
	private ImageIcon imgPDF;
	private Icon iconoPDF;
	private ImageIcon imgHojaCalculo;
	private Icon iconoHojaCalculo;
	private ImageIcon imgCMD;
	private Icon iconoCMD;
	
	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					Barra frame = new Barra();
					frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 */
	public Barra() {
		setIconImage(Toolkit.getDefaultToolkit().getImage("E:\\Escritorio\\2DAM\\ProgramacionServicios\\BarraDeTareas\\ico.ico"));
		setTitle("Tu barra de tareas");
		setForeground(Color.DARK_GRAY);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 353, 200);
		contentPane = new JPanel();
		contentPane.setBackground(Color.DARK_GRAY);
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		// TITULO.
		JLabel lbTitulo = new JLabel("TAREAS");
		lbTitulo.setForeground(Color.WHITE);
		lbTitulo.setFont(new Font("Times New Roman", Font.BOLD, 30));
		lbTitulo.setBounds(109, 11, 121, 28);
		contentPane.add(lbTitulo);
		
		// BOTÓN ABRIR APP PDF.
		JButton btPDF = new JButton();
		btPDF.setBackground(Color.WHITE);
		btPDF.setBounds(10, 50, 100, 100);		
		imgPDF = new ImageIcon("PDF.png");
		iconoPDF = new ImageIcon(imgPDF.getImage().getScaledInstance(btPDF.getWidth(),btPDF.getHeight(), Image.SCALE_DEFAULT));
		btPDF.setIcon(iconoPDF);		
		contentPane.add(btPDF);

		
		// BOTÓN PDF CLICK.
		btPDF.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				
				Process pPDF;
				try {
					pPDF = Runtime.getRuntime().exec("rundll32 url.dll,FileProtocolHandler Procesos_Hilos.pdf");
					pPDF.waitFor();
				} catch (IOException e1) {
					System.out.println("No se encuentra.");
				} catch (InterruptedException e1) {
					e1.printStackTrace();
				}
			}
		});
					  									
		// BOTÓN ABRIR HOJA CALCULO.
		JButton btHojaCalculo = new JButton();
		btHojaCalculo.setBackground(Color.WHITE);
		btHojaCalculo.setBounds(120, 50, 100, 100);
		imgHojaCalculo = new ImageIcon("HojaCalculo.png");
		iconoHojaCalculo = new ImageIcon(imgHojaCalculo.getImage().getScaledInstance(btHojaCalculo.getWidth(), btHojaCalculo.getHeight(), Image.SCALE_DEFAULT));
		btHojaCalculo.setIcon(iconoHojaCalculo);
		contentPane.add(btHojaCalculo);
		
		// BOTÓN ABRIR HOJA CALCULO CLICK.
		btHojaCalculo.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				Process pCalc;
				try {
					pCalc = Runtime.getRuntime().exec("cmd /c start hojaCalculo.ods");
					pCalc.waitFor();
				} catch (IOException e1) {
					System.out.println("No se encuentra.");
				} catch (InterruptedException e1) {
					e1.printStackTrace();
				}
			}
		});
		
		// BOTÓN VERSION JAVA CMD.		
		JButton btCMD = new JButton("");
		btCMD.setBackground(Color.WHITE);
		btCMD.setBounds(230, 50, 100, 100);
		imgCMD = new ImageIcon("CMD.jpg");
		iconoCMD = new ImageIcon(imgCMD.getImage().getScaledInstance(btCMD.getWidth(), btCMD.getHeight(), Image.SCALE_DEFAULT));
		btCMD.setIcon(iconoCMD);
		contentPane.add(btCMD);
		
		// BOTÓN VERSION JAVA CMD CLICK.		
		btCMD.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				
				try {					
					Process builder2 = Runtime.getRuntime().exec("cmd /c start cmd.exe /K \"@java -version\"");
					ProcessBuilder builder = new ProcessBuilder("cmd.exe","/c", "@java -version");
			        builder.redirectErrorStream(true);
			        Process p = builder.start();
			        BufferedReader r = new BufferedReader(new InputStreamReader(p.getInputStream()));
			        String line;
			        while (true) {
			            line = r.readLine();
			            if (line == null) { break; }
			            System.out.println(line);
			        }		
				} catch (IOException e1) {
					System.out.println("No se encuentra.");
				}
			        		        
			}
		});
		
	}
}
```
