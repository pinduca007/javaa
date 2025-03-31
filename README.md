# javaagit clone https://github.com/seu-usuario/analise-mercado-java.git
cd analise-mercado-java
mvn compile
mvn exec:java -Dexec.mainClass="GraficoPesquisaMercado"


## Arquivo 3: pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.exemplo</groupId>
  <artifactId>analise-mercado</artifactId>
  <version>1.0.0</version>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
  </properties>

  <dependencies>
    <dependency>
      <groupId>org.jfree</groupId>
      <artifactId>jfreechart</artifactId>
      <version>1.5.3</version>
    </dependency>
  </dependencies>

  <build>
    <plugins>
      <plugin>
        <groupId>org.codehaus.mojo</groupId>
        <artifactId>exec-maven-plugin</artifactId>
        <version>3.0.0</version>
        <configuration>
          <mainClass>GraficoPesquisaMercado</mainClass>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>

import org.jfree.chart.ChartFactory;
import org.jfree.chart.ChartFrame;
import org.jfree.chart.JFreeChart;
import org.jfree.chart.plot.PlotOrientation;
import org.jfree.data.category.DefaultCategoryDataset;

/**
 * Classe que demonstra a criação de gráficos para análise de mercado
 */
public class GraficoPesquisaMercado {

    public static void main(String[] args) {
        // Criando um dataset para o gráfico de barras
        DefaultCategoryDataset dataset = new DefaultCategoryDataset();
        
        // Dados fictícios de participação de mercado (em porcentagem)
        dataset.addValue(24.1, "Participação", "Apple");
        dataset.addValue(19.4, "Participação", "Samsung");
        dataset.addValue(11.7, "Participação", "Xiaomi");
        dataset.addValue(9.8, "Participação", "Oppo");
        dataset.addValue(6.1, "Participação", "Vivo");
        dataset.addValue(28.9, "Participação", "Outros");
        
        // Criando o gráfico de barras
        JFreeChart graficoBarras = ChartFactory.createBarChart(
            "Participação de Mercado no Setor de Smartphones (2023)", 
            "Empresas", 
            "Participação de Mercado (%)", 
            dataset,
            PlotOrientation.VERTICAL,
            true,
            true,
            false
        );
        
        // Exibindo o gráfico
        ChartFrame frame = new ChartFrame("Análise de Mercado", graficoBarras);
        frame.pack();
        frame.setVisible(true);
    }
}

import org.jfree.chart.ChartFactory;
import org.jfree.chart.ChartFrame;
import org.jfree.chart.JFreeChart;
import org.jfree.chart.plot.PlotOrientation;
import org.jfree.data.category.DefaultCategoryDataset;

/**
 * Classe que demonstra a criação de gráficos para análise econômica
 */
public class GraficoCrescimentoPIB {

    public static void main(String[] args) {
        DefaultCategoryDataset dataset = new DefaultCategoryDataset();
        
        // Dados fictícios de crescimento do PIB (% anual)
        dataset.addValue(2.3, "Crescimento", "EUA");
        dataset.addValue(1.6, "Crescimento", "Zona Euro");
        dataset.addValue(5.2, "Crescimento", "China");
        dataset.addValue(6.8, "Crescimento", "Índia");
        dataset.addValue(-0.5, "Crescimento", "Japão");
        dataset.addValue(1.2, "Crescimento", "Brasil");
        
        JFreeChart grafico = ChartFactory.createBarChart(
            "Crescimento do PIB - Principais Economias (2023)", 
            "Países", 
            "Crescimento Anual (%)", 
            dataset,
            PlotOrientation.VERTICAL,
            true, 
            true, 
            false
        );
        
        ChartFrame frame = new ChartFrame("Indicadores Econômicos", grafico);
        frame.pack();
        frame.setVisible(true);
    }
}