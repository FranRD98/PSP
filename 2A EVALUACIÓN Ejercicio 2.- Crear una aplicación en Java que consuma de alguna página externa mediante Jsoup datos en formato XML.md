# EJERCICIO JSOUP  EN JAVA.
##### En mi perfil dispones del proyecto para descargar. Este se encuentra aquí por temas de la asignatura.
```java
package sample;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.geometry.Pos;
import javafx.scene.Group;
import javafx.scene.Parent;
import javafx.scene.Scene;
import javafx.scene.control.Alert;
import javafx.scene.control.Dialog;
import javafx.scene.control.Label;
import javafx.scene.control.ListView;
import javafx.scene.layout.VBox;
import javafx.scene.text.Font;
import javafx.stage.Stage;
import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

import java.awt.*;
import java.io.IOException;
import java.util.ArrayList;

public class Main extends Application {

    // ESTA APLICACIÓN MOSTRARÁ LOS LOS TITULOS POR CONSOLA Y POR LISTVIEW Y LAS FECHAS SOLO POR CONSOLA.
    private ListView lvNoticias = new ListView();

    private void rellenarListView(){
        ArrayList<String> noticias = new ArrayList();

        try {
            Document doc = Jsoup.connect("https://www.elmundo.es/deportes/motociclismo.html?intcmp=MENUDES22301&s_kw=motociclismo").get();

            Elements links = doc.select("h3>a[href]");

            for (Element link : links) {
                lvNoticias.getItems().add(link.text());
            }

        } catch (IOException e) { e.printStackTrace(); }
    }

    private void handleItemClicks(){
        lvNoticias.setOnMouseClicked(event -> {
            String selectedItem = lvNoticias.getSelectionModel().getSelectedItem().toString();
            Alert d = new Alert(Alert.AlertType.INFORMATION,selectedItem);
            d.show();
        });
    }

    @Override
    public void start(Stage primaryStage) throws Exception{
        Scene scene = new Scene(new Group());
        primaryStage.setTitle("Lector Noticias - JSOUP");
        primaryStage.setWidth(600);
        primaryStage.setHeight(600);

        Label lbCabecera = new Label("El Mundo Noticias Motociclismo");
        lbCabecera.setFont(new Font("Lucida",20));

        rellenarListView();
        handleItemClicks();

        final VBox vbox = new VBox();
        vbox.getChildren().addAll(lbCabecera,lvNoticias);
        vbox.setAlignment(Pos.CENTER);

        Group group = ((Group) scene.getRoot());
        group.getChildren().addAll(vbox);
        group.setLayoutX(100);

        primaryStage.setScene(scene);
        primaryStage.show();

        // DATOS POR CONSOLA
        Document doc = Jsoup.connect("https://www.elmundo.es/deportes/motociclismo.html?intcmp=MENUDES22301&s_kw=motociclismo").get();

        Elements links = doc.select("h3>a[href]");
        Elements fechas = doc.select("footer");
        int i = 1;

        System.out.println("===TITULOS===");
        for (Element link : links) {
            System.out.println("TITULO "+i+": "+link.text());

            for(Element fecha : fechas){
                System.out.println("FECHA: "+fecha.text()+"\n");
                break;
            }
            i++;
        }
    }


    public static void main(String[] args) { Application.launch(args); }
}

```
