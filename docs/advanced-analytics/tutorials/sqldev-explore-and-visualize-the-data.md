---
title: Lektion 3 durchsuchen und Visualisieren von Daten mithilfe von R und T-SQL (SQL Server-Machine Learning) | Microsoft-Dokumentation
description: Veranschaulicht, wie Sie R in SQL Server Einbetten von gespeicherten Prozeduren und T-SQL-Funktionen
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6b34de3c71629a1563bf0d480306680dc6253748
ms.sourcegitcommit: 320958d0f55b6974abf46f8a04f7a020ff86a0ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "42703623"
---
# <a name="lesson-3-explore-and-visualize-the-data"></a>Lektion 3: Untersuchen und Visualisieren von Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Tutorials für SQL-Entwickler zur Verwendung von R in SQL Server.

In dieser Lektion werden Sie überprüfen Sie die Beispieldaten, und generieren anschließend einige Diagramme mit [RxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) aus [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) und die generische [Hist](https://www.rdocumentation.org/packages/graphics/versions/3.5.0/topics/hist) -Funktion in r Basis. Dieser R-Funktionen befinden sich bereits im [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Eine wichtige Ziel zeigt das Aufrufen von R-Funktionen aus [!INCLUDE[tsql](../../includes/tsql-md.md)] in gespeicherten Prozeduren und speichern Sie die Ergebnisse im Application-Dateiformate:

+ Erstellen Sie eine gespeicherte Prozedur mit **RxHistogram** einer R-Zeichnung als Varbinary-Daten zu generieren. Verwendung **Bcp** den binären Datenstrom in eine Bilddatei exportieren.
+ Erstellen Sie eine gespeicherte Prozedur mit **Hist** auf eine Zeichnung, speichern die Ergebnisse als JPG- und PDF-Ausgabe zu generieren.

> [!NOTE]
> Da Visualisierung ein leistungsfähiges Tool für das Verständnis der Form "Daten" und die Verteilung ist, stellt eine Reihe von Funktionen und Pakete von R zum Generieren von Histogrammen, Punktdiagrammen, boxplots und andere Daten Diagramme bereit. R erstellt in der Regel Bilder mithilfe eines R-Geräts für die grafische Ausgabe, die Sie erfassen und speichern Sie als können eine **Varbinary** Datentyp für das Rendering in einer Anwendung. Sie können auch die Bilder auf eine der Support-Dateiformate speichern (. JPG. PDF-Datei usw.).

## <a name="review-the-data"></a>Überprüfen Sie die Daten

Das Entwickeln einer Data Science-Lösung bringt normalerweise die intensive Untersuchung und Visualisierung von Daten mit sich. Zuerst kurz, überprüfen die Beispieldaten, sofern Sie noch nicht geschehen.

Im ursprünglichen Dataset wurden die Taxi-IDs und die Fahrtendatensätze in separaten Dateien bereitgestellt. Aber damit wird die Beispieldaten einfacher zu verwenden, die beiden ursprünglichen Datasets verknüpft wurde für die Spalten _"medallion"_, _hack\_Lizenz_, und _Pickup\_ "DateTime"_.  Die Datensätze wurden ebenso auf Stichproben reduziert, um nur 1 % der ursprünglichen Anzahl der Datensätze zu erhalten. Der auf Stichproben reduzierte Datensatz hat 1.703.957 Zeilen und 23 Spalten.

**Taxi-IDs**
  
-   Die Spalte _medallion_ stellt die eindeutige ID-Nummer des Taxis dar.
  
-   Die _hack\_Lizenz_ Spalte enthält die Taxi Führerscheinnummer (anonymisierte).
  
**Datensätze von Fahrten und Fahrpreisen**
  
-   Jeder Datensatz für Fahrten enthält den genauen Abhol- und Zielort und die Zeit sowie die Fahrstrecke.
  
-   Jeder Fahrpreisdatensatz enthält die Zahlungsinformationen wie die Zahlungsart, der Gesamtbetrag und den Fahrtpreis.
  
-   Die letzten drei Spalten können für verschiedene Machine Learning-Tasks verwendet werden. Die _Tipp\_Menge_ Spalte kontinuierliche numerische Werte enthält, und kann verwendet werden, als die **Bezeichnung** Spalte für die Regressionsanalyse. Die Spalte _tipped_ verfügt nur über Ja/Nein-Werte und wird für die binäre Klassifikation verwendet. Die _Tipp\_Klasse_ Spalte verfügt über mehrere **klassenbezeichnungen** und können daher für mehrklassige Klassifizierungsaufgaben als Bezeichnung verwendet werden.
  
    Diese exemplarische Vorgehensweise enthält nur die binäre Klassifizierungsaufgabe. Sie können gerne versuchen, Modelle für die anderen beiden Machine Learning-Tasks und für mehrklassige Klassifizierung zu erstellen.
  
-   Die Werte für die Bezeichnungsspalten basieren alle auf die _Tipp\_Menge_ Spalte verwenden folgende Geschäftsregeln:
  
    |Name der abgeleiteten Spalte|Regel|
    |-|-|
     |tipped|If tip_amount > 0, tipped = 1, otherwise tipped = 0|
    |tip_class|Class 0: tip_amount = $0<br /><br />Class 1: tip_amount > $0 and tip_amount <= $5<br /><br />Class 2: tip_amount > $5 and tip_amount <= $10<br /><br />Class 3: tip_amount > $10 and tip_amount <= $20<br /><br />Class 4: tip_amount > $20|

## <a name="create-a-stored-procedure-using-rxhistogram-to-plot-the-data"></a>Erstellen einer gespeicherten Prozedur, die mit RxHistogram zum Zeichnen der Daten

Verwenden Sie zum Erstellen des Plots [RxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram), eine der erweiterten R-Funktionen [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler). Dieser Schritt stellt ein Histogramm, das basierend auf Daten aus einer [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage. Sie können diese Funktion in einer gespeicherten Prozedur umschließen **PlotHistogram**.

1. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in Objekt-Explorer, mit der rechten Maustaste die **NYCTaxi_Sample** Datenbank **Programmierbarkeit**, und erweitern Sie dann **gespeicherte Prozeduren** an die die Verfahren in Lektion 2 erstellt haben.

2. Mit der rechten Maustaste **PlotHistogram** , und wählen Sie **ändern** zum Anzeigen der Quelle. Sie können diese Prozedur aufrufen, ausführen **RxHistogram** auf Daten in der tipped-Spalte der Tabelle der Nyctaxi_sample.

3. Erstellen Sie optional als eine Übung lernen Ihr eigenes Exemplar dieser gespeicherten Prozedur, die anhand des folgenden Beispiels. Öffnen Sie ein neues Abfragefenster ein, und fügen Sie das folgende Skript in einer gespeicherten Prozedur zu erstellen, die das Histogramm zeichnet. In diesem Beispiel heißt **PlotHistogram2** um Benennungskonflikte mit dem bereits vorhandenen Verfahren zu vermeiden.

    ```SQL
    CREATE PROCEDURE [dbo].[PlotHistogram2]
    AS
    BEGIN
      SET NOCOUNT ON;
      DECLARE @query nvarchar(max) =  
      N'SELECT tipped FROM nyctaxi_sample'  
      EXECUTE sp_execute_external_script @language = N'R',  
                                         @script = N'  
       image_file = tempfile();  
       jpeg(filename = image_file);  
       #Plot histogram  
       rxHistogram(~tipped, data=InputDataSet, col=''lightgreen'',   
       title = ''Tip Histogram'', xlab =''Tipped or not'', ylab =''Counts'');  
       dev.off();  
       OutputDataSet <- data.frame(data=readBin(file(image_file, "rb"), what=raw(), n=1e6));  
       ',  
       @input_data_1 = @query  
       WITH RESULT SETS ((plot varbinary(max)));  
    END
    GO
    ```

Die gespeicherte Prozedur **PlotHistogram2** ist eine bereits vorhandene gespeicherte Prozedur mit **PlotHistogram** erstellt die `RunSQL_SQL_Walkthrough.ps1` Skript. 
  
+ Die Variable `@query` definiert den Abfragetext (`'SELECT tipped FROM nyctaxi_sample'`), der an das R-Skript als das Argument für die Skripteingabevariable, `@input_data_1`, übergeben wird.
  
+ Das R-Skript ist recht einfach: eine R-Variable (`image_file`) wird definiert, um das Bild zu speichern und dann die **RxHistogram** Funktion wird aufgerufen, um die Zeichnung zu generieren.
  
+ Das R-Gerät nastaven NA hodnotu **aus** da mit diesem Befehl als ein externes Skript in SQL Server ausgeführt wird. Öffnet in der Regel in R, wenn Sie einen Zeichenbefehl für hohe ausgeben R ein Grafikfenster, das Namen einer *Gerät*. Sie können die Größe und Farben sowie andere Aspekte des Fensters ändern. Sie können alternativ das Gerät ausschalten, wenn Sie in eine Datei schreiben oder die Ausgabe auf eine andere Art handhaben.
  
+ Das R-Grafikobjekt wird zu einem R-Datenrahmen für die Ausgabe serialisiert.

### <a name="execute-the-stored-procedure-and-use-bcp-to-export-binary-data-to-an-image-file"></a>Führen Sie die gespeicherte Prozedur, und Verwenden von Bcp zum Exportieren von Binärdaten in eine Bilddatei

Die gespeicherte Prozedur gibt das Bild als Strom von varbinary-Daten zurück, die Sie natürlich nicht direkt anzeigen können. Sie können jedoch das Hilfsprogramm **bcp** verwenden, um die varbinary-Daten abzurufen und sie als Bilddatei auf einem Clientcomputer zu speichern.
  
1.  Führen Sie die folgende Anweisung in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]aus:
  
    ```SQL
    EXEC [dbo].[PlotHistogram]
    ```
  
    **Ergebnisse**
    
    *Plot*
    *0xFFD8FFE000104A4649...*
  
2.  Öffnen Sie eine PowerShell-Eingabeaufforderung und führen Sie den folgenden Befehl, der Bereitstellung den erforderlichen Instanznamen, Datenbanknamen, Benutzernamen und Anmeldeinformationen als Argumente. Sie können für Benutzer, die Windows-Identitäten, ersetzen **- U** und **-P** mit **-T**.
  
     ```text
     bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  TaxiNYC_Sample  -U <user name> -P <password>
     ```

    > [!NOTE]
    > Befehlsoptionen für Bcp-beachtet werden.
  
3.  Wenn die Verbindung erfolgreich hergestellt wurde, werden Sie dazu aufgefordert, weitere Informationen über das Format der Grafikdatei einzugeben. 

   Drücken Sie bei jeder Eingabeaufforderung die EINGABETASTE, um die bestehenden Angaben zu akzeptieren, außer der folgenden Änderungen:
    
    -   Geben Sie für **prefix-length of field plot**0 ein
  
    -   Geben Sie **Y** ein, wenn Sie die Ausgabeparameter für den späteren Gebrauch speichern möchten.
  
    ```
    Enter the file storage type of field plot [varbinary(max)]: 
    Enter prefix-length of field plot [8]: 0
    Enter length of field plot [0]:
    Enter field terminator [none]:
  
    Do you want to save this format information in a file? [Y/n]
    Host filename [bcp.fmt]:
    ```
  
    **Ergebnisse**
    
    ```
    Starting copy...
    1 rows copied.
    Network packet size (bytes): 4096
    Clock Time (ms.) Total     : 3922   Average : (0.25 rows per sec.)
    ```

    > [!TIP]
    > Wenn Sie die Formatinformationen in einer Datei (bcp.fmt) speichern, generiert das Hilfsprogramm **bcp** eine Formatdefinition, die Sie zukünftig auf ähnliche Befehle anwenden können, ohne zur Eingabe von Formatoptionen für Grafikdateien aufgefordert zu werden. Fügen Sie zum Verwenden der Formatdatei `-f bcp.fmt` an das Ende einer beliebigen Befehlszeile nach dem Argument „Kennwort“ ein.
  
4.  Die Ausgabedatei wird im gleichen Verzeichnis erstellt, in dem Sie den PowerShell-Befehl ausgeführt haben. Um die Grafik anzuzeigen, öffnen Sie einfach die Datei plot.jpg.
  
    ![Taxifahrten mit und ohne Trinkgeld](media/rsql-devtut-tippedornot.jpg "Taxifahrten mit und ohne Trinkgeld")  
  
## <a name="create-a-stored-procedure-using-hist-and-multiple-output-formats"></a>Erstellen einer gespeicherten Prozedur mithilfe von HIS und mehrere Ausgabeformate

Data Scientists generieren in der Regel mehrere datenvisualisierungen, um Einblicke in die Daten aus verschiedenen Perspektiven zu erhalten. In diesem Beispiel verwendet die gespeicherte Prozedur die HIS-Funktion, um das Histogramm, exportieren die binären Daten in gängigen Formaten wie z. B. zu erstellen. JPG. PDF-Datei, und. PNG. 

1. Verwenden Sie die vorhandene gespeicherte Prozedur **PlotInOutputFiles**, Histogrammen, Punktdiagrammen und anderen R-Grafiken zu schreiben. JPG und. PDF-Format. Die `RunSQL_SQL_Walkthrough.ps1` erstellt **PlotInOutputFiles** und fügt es die Datenbank. Verwenden Sie mit der rechten Maustaste **ändern** zum Anzeigen der Quelle.

2. Erstellen Sie eine eigene Kopie der Prozedur als optional als eine Übung Learning **PlotInOutputFiles2**, durch einen eindeutigen Namen ein, um Namenskonflikte zu vermeiden.

    In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], öffnen Sie ein neues **Abfrage** Fenster, und fügen Sie die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.
  
    ```SQL
    CREATE PROCEDURE [dbo].[PlotInOutputFiles2]  
    AS  
    BEGIN  
      SET NOCOUNT ON;  
      DECLARE @query nvarchar(max) =  
      N'SELECT cast(tipped as int) as tipped, tip_amount, fare_amount FROM [dbo].[nyctaxi_sample]'  
      EXECUTE sp_execute_external_script @language = N'R',  
      @script = N'  
       # Set output directory for files and check for existing files with same names   
        mainDir <- ''C:\\temp\\plots''  
        dir.create(mainDir, recursive = TRUE, showWarnings = FALSE)  
        setwd(mainDir);  
        print("Creating output plot files:", quote=FALSE)
        
        # Open a jpeg file and output histogram of tipped variable in that file.  
        dest_filename = tempfile(pattern = ''rHistogram_Tipped_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.jpg'',sep="")  
        print(dest_filename, quote=FALSE);  
        jpeg(filename=dest_filename);  
        hist(InputDataSet$tipped, col = ''lightgreen'', xlab=''Tipped'',   
            ylab = ''Counts'', main = ''Histogram, Tipped'');  
         dev.off();  

        # Open a pdf file and output histograms of tip amount and fare amount.   
        # Outputs two plots in one row  
        dest_filename = tempfile(pattern = ''rHistograms_Tip_and_Fare_Amount_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.pdf'',sep="")  
        print(dest_filename, quote=FALSE);  
        pdf(file=dest_filename, height=4, width=7);  
        par(mfrow=c(1,2));  
        hist(InputDataSet$tip_amount, col = ''lightgreen'',   
            xlab=''Tip amount ($)'',   
            ylab = ''Counts'',   
            main = ''Histogram, Tip amount'', xlim = c(0,40), 100);  
        hist(InputDataSet$fare_amount, col = ''lightgreen'',   
            xlab=''Fare amount ($)'',   
            ylab = ''Counts'',   
            main = ''Histogram,   
            Fare amount'',   
            xlim = c(0,100), 100);  
       dev.off();  
  
        # Open a pdf file and output an xyplot of tip amount vs. fare amount using lattice;  
        # Only 10,000 sampled observations are plotted here, otherwise file is large.  
        dest_filename = tempfile(pattern = ''rXYPlots_Tip_vs_Fare_Amount_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.pdf'',sep="")  
        print(dest_filename, quote=FALSE);  
        pdf(file=dest_filename, height=4, width=4);  
        plot(tip_amount ~ fare_amount,   
            data = InputDataSet[sample(nrow(InputDataSet), 10000), ],   
            ylim = c(0,50),   
            xlim = c(0,150),   
            cex=.5,   
            pch=19,   
            col=''darkgreen'',    
            main = ''Tip amount by Fare amount'',   
            xlab=''Fare Amount ($)'',   
            ylab = ''Tip Amount ($)'');   
        dev.off();',  
     @input_data_1 = @query  
     END
    ```
  
+ Die Ausgabe der SELECT-Abfrage in der gespeicherten Prozedur wird im Standarddatenrahmen von R, `InputDataSet`, gespeichert. Anschließend können verschiedene Zeichenfunktionen von R aufgerufen werden, um die tatsächlichen Grafikdateien zu generieren. Die meisten der eingebetteten R-Skripts stellen Optionen für diese Grafikfunktionen dar, z.B. `plot` oder `hist`.
  
+ Alle Dateien werden im lokalen Ordner _C:\temp\Plots\\_ gespeichert. Der Zielordner wird durch die Argumente für das R-Skript als Teil der gespeicherten Prozedur definiert.  Sie können den Zielordner ändern, indem Sie den Wert der Variable, `mainDir`, ändern.

+ Um die Dateien in einem anderen Ordner auszugeben, ändern Sie den Wert der `mainDir` -Variable im R-Skript, das in der gespeicherten Prozedur gespeichert ist. Sie können auch das Skript ändern, damit es verschiedene Formate, mehr Dateien usw. ausgibt.

### <a name="execute-the-stored-procedure"></a>Ausführen der gespeicherten Prozedur

Führen Sie die folgende Anweisung aus, um die binäre Darstellung von Daten in Formate, JPEG und PDF-Datei zu exportieren.

```SQL
EXEC PlotInOutputFiles
```

**Ergebnisse**
    
```
STDOUT message(s) from external script:
[1] Creating output plot files:[1] C:\temp\plots\rHistogram_Tipped_18887f6265d4.jpg[1] 

C:\temp\plots\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]

C:\temp\plots\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf
```

Die Zahlen in den Dateinamen werden nach dem Zufallsprinzip generiert, um sicherzustellen, dass Sie keinen Fehler erhalten, wenn beim Schreiben in die vorhandene Datei.

### <a name="view-output"></a>Anzeigen der Ausgabe 

Um die Grafik anzuzeigen, öffnen Sie den Zielordner aus, und überprüfen Sie die Dateien, die vom R-Code in der gespeicherten Prozedur erstellt wurden.

1. Wechseln Sie in der Meldung "stdout" angegebenen Ordner (in diesem Beispiel ist dies C:\temp\plots\)

2. Open `rHistogram_Tipped.jpg` um die Anzahl von Fahrten anzuzeigen, die einen Tipp vs. die Fahrten erhalten haben, die kein Trinkgeld erhalten haben. (Das Histogramm ist ähnlich wie das im vorherigen Schritt erstellten.)

3. Open `rHistograms_Tip_and_Fare_Amount.pdf` zum Anzeigen der Verteilung von trinkgeldbeträgen, im Vergleich zu den Mengen "fare".
    
  ![Histogramm mit "Tip_amount" und "fare_amount" an](media/rsql-devtut-tipamtfareamt.PNG "Histogramm mit \"Tip_amount\" und \"fare_amount\" an")

4. Open `rXYPlots_Tip_vs_Fare_Amount.pdf` ein Punktdiagramm mit der Höhe des Fahrpreises auf der x-Achse und der die Höhe des trinkgelds auf der y-Achse an.

   ![die Höhe des trinkgelds dargestellt über Fahrpreis](media/rsql-devtut-tipamtbyfareamt.PNG "die Höhe des trinkgelds zeitlichen Verlauf Fahrpreis dargestellt.")

## <a name="next-lesson"></a>Nächste Lektion

[Lektion 3: Erstellen von Datenfunktionen mit T-SQL](sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[Lektion 1: Einrichten von NYC Taxi-Demo-Daten](sqldev-download-the-sample-data.md)
