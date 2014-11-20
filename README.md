repositorioR
============


package pruebasescritorio;


import org.w3c.dom.NodeList;
import org.w3c.dom.Document;
import org.w3c.dom.Node;
import org.w3c.dom.Element;
import java.io.File;
import java.io.IOException;
import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;
import javax.xml.parsers.ParserConfigurationException;
import org.xml.sax.SAXException;

public class javaXML{
    
    public static void main(String[]args) throws ParserConfigurationException, SAXException, IOException {
        File archivoXML=new File("C:/Users/Public/Documents/alumno.xml");
        DocumentBuilderFactory dbf=DocumentBuilderFactory.newInstance();
        DocumentBuilder dbb=dbf.newDocumentBuilder();
        Document doc=dbb.parse(archivoXML);
        
        doc.getDocumentElement().normalize();
        System.out.println("Elemento Pricipal: "+ doc.getDocumentElement().getNodeName());
        NodeList nlist = doc.getElementsByTagName("Alumnos");
        for(int t=0; t<nlist.getLength();t++){
            Node nNode=nlist.item(t);
            System.out.println("Dato"+nNode.ELEMENT_NODE);
           if(nNode.getNodeType()==Node.ELEMENT_NODE)
            {
                Element eElement=(Element) nNode;
                System.out.println("Nombre"+ eElement.getAttribute("nombre"));
                System.out.println("Nombre"+ eElement.getElementsByTagName("Apellido").item(0).getTextContent());
               // System.out.println("Carrera"+ eElement.getElementsByTagName("Apellido").item(0).getTextContent());
                //System.out.println("NuneroControl"+ eElement.getElementsByTagName("numControl").item(0).getTextContent());
              
            }
        }
        
    }
    
}
