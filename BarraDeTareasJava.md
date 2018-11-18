# BARRA DE TARES SENCILLA CON WINDOWS BUILDER

![alt text](https://i.imgur.com/hDufHpm.png "BarraDeTareas")

```java
import java.awt.BorderLayout;
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

public class Barra extends JFrame {

	private JPanel contentPane;
	private ImageIcon imgChrome;
	private Icon iconoChrome;
	private ImageIcon imgSpotify;
	private Icon iconoSpotify;
	private ImageIcon imgEclipse;
	private Icon iconoEclipse;
	private ImageIcon imgAudacity;
	private Icon iconoAudacity;
	
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
		setBounds(100, 100, 463, 200);
		contentPane = new JPanel();
		contentPane.setBackground(Color.DARK_GRAY);
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		// TITULO.
		JLabel lbTitulo = new JLabel("TU BARRA DE TAREAS");
		lbTitulo.setForeground(Color.WHITE);
		lbTitulo.setFont(new Font("Times New Roman", Font.BOLD, 30));
		lbTitulo.setBounds(53, 11, 336, 28);
		contentPane.add(lbTitulo);
		
		// BOTÓN CHROME.
		JButton btChrome = new JButton();
		btChrome.setBackground(Color.WHITE);
		btChrome.setBounds(10, 50, 100, 100);		
		imgChrome = new ImageIcon("chrome.png");
		iconoChrome = new ImageIcon(imgChrome.getImage().getScaledInstance(btChrome.getWidth(), btChrome.getHeight(), Image.SCALE_DEFAULT));
		btChrome.setIcon(iconoChrome);		
		contentPane.add(btChrome);
		
		// BOTÓN CHROME CLICK.
		btChrome.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				try {
					ProcessBuilder pbChrome = new ProcessBuilder("C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe");
					pbChrome.start();
				} catch (Exception ex) {
					System.out.println("No se encuentra el programa en la ruta:  " + ex);
				}
			}
		});
				
		// BOTÓN SPOTIFY.
		JButton btSpotify = new JButton();
		btSpotify.setBackground(Color.WHITE);
		btSpotify.setBounds(120, 50, 100, 100);
		imgSpotify = new ImageIcon("spotify.png");
		iconoSpotify = new ImageIcon(imgSpotify.getImage().getScaledInstance(btSpotify.getWidth(), btSpotify.getHeight(), Image.SCALE_DEFAULT));
		btSpotify.setIcon(iconoSpotify);
		contentPane.add(btSpotify);
		
		// BOTÓN SPOTIFY CLICK.
		btSpotify.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				try {
					ProcessBuilder pbSpotify = new ProcessBuilder("C:\\Users\\vesprada\\AppData\\Roaming\\Spotify\\Spotify.exe");
					pbSpotify.start();
				} catch (Exception ex) {
					System.out.println("No se encuentra el programa en la ruta:  " + ex);
				}
			}
		});
		
		// BOTÓN ECLIPSE.
		JButton btEclipse = new JButton("");
		btEclipse.setBackground(Color.WHITE);
		btEclipse.setBounds(230, 50, 100, 100);
		imgEclipse = new ImageIcon("eclipse.png");
		iconoEclipse = new ImageIcon(imgEclipse.getImage().getScaledInstance(btEclipse.getWidth(), btEclipse.getHeight(), Image.SCALE_DEFAULT));
		btEclipse.setIcon(iconoEclipse);
		contentPane.add(btEclipse);
		
		// BOTÓN ECLIPSE CLICK.
		btEclipse.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				try {
					ProcessBuilder pbEclipse = new ProcessBuilder("C:\\Users\\vesprada\\eclipse\\committers-2018-09\\eclipse\\eclipse.exe");
					pbEclipse.start();
				} catch (Exception ex) {
					System.out.println("No se encuentra el programa en la ruta:  " + ex);
				}
			}
		});
		
		// BOTÓN AUDACITY.
		JButton btAudacity = new JButton();
		btAudacity.setBackground(Color.WHITE);
		btAudacity.setBounds(340, 50, 100, 100);
		imgAudacity = new ImageIcon("Audacity.png");
		iconoAudacity = new ImageIcon(imgAudacity.getImage().getScaledInstance(btAudacity.getWidth(), btAudacity.getHeight(), Image.SCALE_DEFAULT));
		btAudacity.setIcon(iconoAudacity);
		contentPane.add(btAudacity);
		
		// BOTÓN AUDACITY CLICK.
		btAudacity.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				try {
					ProcessBuilder pbAudacity = new ProcessBuilder("C:\\Program Files (x86)\\Audacity\\audacity.exe");
					pbAudacity.start();
				} catch (Exception ex) {
					System.out.println("No se encuentra el programa en la ruta:  " + ex);
				}
			}
		});
	}
}
