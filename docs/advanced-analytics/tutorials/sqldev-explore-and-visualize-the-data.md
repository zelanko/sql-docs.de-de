---
title: 'Lektion 1: untersuchen und Visualisieren von Daten mit R und T-SQL'
description: Tutorial, das zeigt, wie Sie SQL Server Daten mithilfe von R-Funktionen untersuchen und visualisieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 2bd91aa464dd4a9e6a58dda5d802a3b81716cf11
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344518"
---
# <a name="lesson-1-explore-and-visualize-the-data"></a>Lektion 1: Untersuchen und Visualisieren der Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Tutorials für SQL-Entwickler zur Verwendung von R in SQL Server.

In diesem Schritt überprüfen Sie die Beispiel Daten und generieren dann einige Plots mithilfe von [rxhistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) aus [revoscaler](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) und der generischen [Hist](https://www.rdocumentation.org/packages/graphics/versions/3.5.0/topics/hist) -Funktion in Basis-R. Diese R-Funktionen sind bereits in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]enthalten.

Ein wichtiges Ziel dieser Lektion ist das Aufrufen von R-Funktionen aus [!INCLUDE[tsql](../../includes/tsql-md.md)] in gespeicherten Prozeduren und das Speichern der Ergebnisse in Anwendungsdatei Formaten:

+ Erstellen Sie mithilfe von **rxhistogram** eine gespeicherte Prozedur, um einen R-Plot als varbinary-Daten zu generieren. Verwenden Sie **bcp** , um den binären Stream in eine Bilddatei zu exportieren.
+ Erstellen Sie eine gespeicherte Prozedur mit **Hist** , um ein Diagramm zu generieren, und speichern Sie die Ergebnisse als jpg-und PDF-Ausgabe.

> [!NOTE]
> Da die Visualisierung ein leistungsfähiges Tool zum Verständnis der Daten Form und-Verteilung ist, bietet R eine Reihe von Funktionen und Paketen zum Erstellen von Histogrammen, Punkt Diagrammen, Boxplots und anderen Diagrammen zum Durchsuchen von Daten. R erstellt in der Regel Bilder mithilfe eines R-Geräts für die grafische Ausgabe, das Sie als **varbinary** -Datentyp zum Rendern in einer Anwendung erfassen und speichern können. Sie können die Bilder auch in einem beliebigen unterstützten Dateiformat speichern (. JPG,. PDF, usw.).

## <a name="review-the-data"></a>Überprüfen der Daten

Das Entwickeln einer Data Science-Lösung bringt normalerweise die intensive Untersuchung und Visualisierung von Daten mit sich. Nehmen Sie sich also zunächst eine Minute Zeit, um die Beispiel Daten zu überprüfen, sofern noch nicht geschehen.

Im ursprünglichen öffentlichen DataSet wurden die Taxi-IDs und die Fahrt Datensätze in separaten Dateien bereitgestellt. Um die Verwendung der Beispiel Daten zu vereinfachen, wurden die beiden ursprünglichen Datasets mit den Spalten " _Medallion_", " _\_Hack License_" und " _Pickup\_DateTime_" verknüpft.  Die Datensätze wurden ebenso auf Stichproben reduziert, um nur 1 % der ursprünglichen Anzahl der Datensätze zu erhalten. Der auf Stichproben reduzierte Datensatz hat 1.703.957 Zeilen und 23 Spalten.

**Taxi-IDs**
  
-   Die Spalte " _Medallion_ " stellt die eindeutige ID-Nummer des Taxis dar.
  
-   Die Spalte " _Hack\_-Lizenz_ " enthält die Lizenznummer des Taxi Treibers (anonymisiert).
  
**Datensätze von Fahrten und Fahrpreisen**
  
-   Jeder Datensatz für Fahrten enthält den genauen Abhol- und Zielort und die Zeit sowie die Fahrstrecke.
  
-   Jeder Fahrpreisdatensatz enthält die Zahlungsinformationen wie die Zahlungsart, der Gesamtbetrag und den Fahrtpreis.
  
-   Die letzten drei Spalten können für verschiedene Machine Learning-Tasks verwendet werden. Die _Tip\_Amount_ -Spalte enthält fortlaufende numerische Werte und kann als Bezeichnungs **Spalte für** die Regressionsanalyse verwendet werden. Die Spalte _tipped_ verfügt nur über Ja/Nein-Werte und wird für die binäre Klassifikation verwendet. Die _Tip\_-Klassen_ Spalte verfügt über mehrere **Klassen Bezeichnungen** und kann daher als Bezeichnung für Klassifizierungs Aufgaben mit mehreren Klassen verwendet werden.
  
    Diese exemplarische Vorgehensweise enthält nur die binäre Klassifizierungsaufgabe. Sie können gerne versuchen, Modelle für die anderen beiden Machine Learning-Tasks und für mehrklassige Klassifizierung zu erstellen.
  
-   Die Werte, die für die Beschriftungs Spalten verwendet werden, basieren alle auf der _Tip\_Amount_ -Spalte, die diese Geschäftsregeln verwendet:
  
    |Name der abgeleiteten Spalte|Regel|
    |-|-|
     |tipped|If tip_amount > 0, tipped = 1, otherwise tipped = 0|
    |tip_class|Class 0: tip_amount = $0<br /><br />Class 1: tip_amount > $0 and tip_amount <= $5<br /><br />Class 2: tip_amount > $5 and tip_amount <= $10<br /><br />Class 3: tip_amount > $10 and tip_amount <= $20<br /><br />Class 4: tip_amount > $20|

## <a name="create-a-stored-procedure-using-rxhistogram-to-plot-the-data"></a>Erstellen einer gespeicherten Prozedur mithilfe von rxhistogram zum Zeichnen der Daten

Um das Diagramm zu erstellen, verwenden Sie [rxhistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram), eine der erweiterten R-Funktionen, die in [revoscaler](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)bereitgestellt werden. In diesem Schritt wird ein Histogramm auf der Grundlage von [!INCLUDE[tsql](../../includes/tsql-md.md)] Daten aus einer Abfrage gezeichnet. Sie können diese Funktion in einer gespeicherten Prozedur ( **plotrxhistogram**) einschließen.

1. Klicken [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Sie in Objekt-Explorer mit der rechten Maustaste auf die **NYCTaxi_Sample** -Datenbank, und wählen Sie **neue Abfrage**aus.

2. Fügen Sie das folgende Skript ein, um eine gespeicherte Prozedur zu erstellen, die das Histogramm erstellt. Dieses Beispiel heißt **rplotrxhistogram*.

    ```sql
    CREATE PROCEDURE [dbo].[RxPlotHistogram]
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

Folgende wichtige Punkte sind in diesem Skript zu verstehen: 
  
+ Die Variable `@query` definiert den Abfragetext (`'SELECT tipped FROM nyctaxi_sample'`), der an das R-Skript als das Argument für die Skripteingabevariable, `@input_data_1`, übergeben wird. Für R-Skripts, die als externe Prozesse ausgeführt werden, sollten Sie über eine eins-zu-Eins-Zuordnung zwischen Eingaben für Ihr Skript und Eingaben für die gespeicherte System Prozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) verfügen, die die R-Sitzung auf SQL Server startet.
  
+ Innerhalb des R-Skripts wird eine`image_file`Variable () zum Speichern des Bilds definiert. 

+ Die **rxhistogram** -Funktion aus der revoscaler-Bibliothek wird aufgerufen, um die Zeichnung zu generieren.
  
+ Das R-Gerät ist auf **Off** festgelegt, da Sie diesen Befehl in SQL Server als externes Skript ausführen. Wenn Sie in r einen allgemeinen plotbefehl ausgeben, öffnet r in der Regel ein Grafikfenster, das als *Gerät*bezeichnet wird. Sie können das Gerät ausschalten, wenn Sie in eine Datei schreiben oder die Ausgabe auf andere Weise verarbeiten.
  
+ Das R-Grafikobjekt wird zu einem R-Datenrahmen für die Ausgabe serialisiert.

### <a name="execute-the-stored-procedure-and-use-bcp-to-export-binary-data-to-an-image-file"></a>Ausführen der gespeicherten Prozedur und Verwenden von bcp zum Exportieren von Binärdaten in eine Bilddatei

Die gespeicherte Prozedur gibt das Bild als Strom von varbinary-Daten zurück, die Sie natürlich nicht direkt anzeigen können. Sie können jedoch das Hilfsprogramm **bcp** verwenden, um die varbinary-Daten abzurufen und sie als Bilddatei auf einem Clientcomputer zu speichern.
  
1. Führen Sie die folgende Anweisung in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]aus:
  
    ```sql
    EXEC [dbo].[RxPlotHistogram]
    ```
  
    **Ergebnisse**
    
    *Plot* *0xffd8ffe000104a4649...*
  
2. Öffnen Sie eine PowerShell-Eingabeaufforderung, und führen Sie den folgenden Befehl aus, um den entsprechenden Instanznamen, Datenbanknamen, Benutzernamen und Anmelde Informationen als Argumente anzugeben. Für diejenigen, die Windows-Identitäten verwenden, können Sie **-U** und **-P** durch **-T**ersetzen.
  
    ```powershell
    bcp "exec RxPlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  NYCTaxi_Sample  -U <user name> -P <password> -T
    ```

    > [!NOTE]
    > Bei Befehls Schaltern für bcp wird die Groß-/Kleinschreibung beachtet.
  
3. Wenn die Verbindung erfolgreich hergestellt wurde, werden Sie dazu aufgefordert, weitere Informationen über das Format der Grafikdatei einzugeben. 

   Drücken Sie bei jeder Eingabeaufforderung die EINGABETASTE, um die bestehenden Angaben zu akzeptieren, außer der folgenden Änderungen:
    
   + Geben Sie für **prefix-length of field plot**0 ein
  
   + Geben Sie **Y** ein, wenn Sie die Ausgabeparameter für den späteren Gebrauch speichern möchten.
  
    ```powershell
    Enter the file storage type of field plot [varbinary(max)]: 
    Enter prefix-length of field plot [8]: 0
    Enter length of field plot [0]:
    Enter field terminator [none]:
  
    Do you want to save this format information in a file? [Y/n]
    Host filename [bcp.fmt]:
    ```
  
    **Ergebnisse**
    
    ```powershell
    Starting copy...
    1 rows copied.
    Network packet size (bytes): 4096
    Clock Time (ms.) Total     : 3922   Average : (0.25 rows per sec.)
    ```

    > [!TIP]
    > Wenn Sie die Formatinformationen in einer Datei (bcp.fmt) speichern, generiert das Hilfsprogramm **bcp** eine Formatdefinition, die Sie zukünftig auf ähnliche Befehle anwenden können, ohne zur Eingabe von Formatoptionen für Grafikdateien aufgefordert zu werden. Fügen Sie zum Verwenden der Formatdatei `-f bcp.fmt` an das Ende einer beliebigen Befehlszeile nach dem Argument „Kennwort“ ein.
  
4.  Die Ausgabedatei wird im gleichen Verzeichnis erstellt, in dem Sie den PowerShell-Befehl ausgeführt haben. Um die Grafik anzuzeigen, öffnen Sie einfach die Datei plot.jpg.
  
    ![Taxifahrten mit und ohne Trinkgeld](media/rsql-devtut-tippedornot.jpg "Taxifahrten mit und ohne Trinkgeld")  
  
## <a name="create-a-stored-procedure-using-hist-and-multiple-output-formats"></a>Erstellen einer gespeicherten Prozedur mithilfe von Hist-und mehreren Ausgabeformaten

Datenanalysten generieren in der Regel mehrere Datenvisualisierungen, um Einblicke in die Daten aus unterschiedlichen Perspektiven zu erhalten. In diesem Beispiel erstellen Sie eine gespeicherte Prozedur mit dem Namen **rplothist** , um Histogramme, Scatterplots und andere R-Grafiken in zu schreiben. JPG und. PDF-Format.

Diese gespeicherte Prozedur verwendet die **Hist** -Funktion, um das Histogramm zu erstellen, wobei die Binärdaten in beliebte Formate wie exportiert werden. JPG,. PDF und. PNG. 

1. Klicken [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Sie in Objekt-Explorer mit der rechten Maustaste auf die **NYCTaxi_Sample** -Datenbank, und wählen Sie **neue Abfrage**aus.

2. Fügen Sie das folgende Skript ein, um eine gespeicherte Prozedur zu erstellen, die das Histogramm erstellt. Dieses Beispiel heißt " **rplothist** ".
  
    ```sql
    CREATE PROCEDURE [dbo].[RPlotHist]  
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
  
+ Alle Dateien werden im lokalen Ordner c:\temp\plotgespeichert. Der Zielordner wird durch die Argumente für das R-Skript als Teil der gespeicherten Prozedur definiert.  Sie können den Zielordner ändern, indem Sie den Wert der Variable, `mainDir`, ändern.

+ Um die Dateien in einem anderen Ordner auszugeben, ändern Sie den Wert der `mainDir` -Variable im R-Skript, das in der gespeicherten Prozedur gespeichert ist. Sie können auch das Skript ändern, damit es verschiedene Formate, mehr Dateien usw. ausgibt.

### <a name="execute-the-stored-procedure"></a>Ausführen der gespeicherten Prozedur

Führen Sie die folgende Anweisung aus, um binäre Plotdaten in JPEG-und PDF-Dateiformate zu exportieren.

```sql
EXEC RPlotHist
```

**Ergebnisse**
    
```sql
STDOUT message(s) from external script:
[1] Creating output plot files:[1] C:\temp\plots\rHistogram_Tipped_18887f6265d4.jpg[1] 

C:\temp\plots\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]

C:\temp\plots\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf
```

Die Zahlen in den Dateinamen werden nach dem Zufallsprinzip generiert, um sicherzustellen, dass Sie beim Schreiben in eine vorhandene Datei keinen Fehler erhalten.

### <a name="view-output"></a>Ausgabe anzeigen 

Um das Diagramm anzuzeigen, öffnen Sie den Zielordner, und überprüfen Sie die Dateien, die vom R-Code in der gespeicherten Prozedur erstellt wurden.

1. Wechseln Sie in den in der stdout-Meldung aufgeführten Ordner (in diesem Beispiel ist dies c:\temp\plots).\)

2. Öffnen `rHistogram_Tipped.jpg` Sie, um die Anzahl von Fahrten mit einem Trinkgeld und den Fahrten anzuzeigen, die keinen Tipp haben. (Dieses Histogramm ähnelt dem, das Sie im vorherigen Schritt generiert haben.)

3. Öffnen `rHistograms_Tip_and_Fare_Amount.pdf` Sie, um die Verteilung von Trink Geldbeträgen anzuzeigen, die für die Kosten Beträge gezeichnet werden.
    
  ![Histogramm mit tip_amount und fare_amount](media/rsql-devtut-tipamtfareamt.PNG "Histogramm mit tip_amount und fare_amount")

4. Öffnen `rXYPlots_Tip_vs_Fare_Amount.pdf` Sie, um ein Punkt Diagramm mit dem Fahrpreis auf der x-Achse und dem trinkgeldbetrag auf der y-Achse anzuzeigen.

   ![trinkgeldbetrag über Fahr Preisbetrag gezeichnet](media/rsql-devtut-tipamtbyfareamt.PNG "trinkgeldbetrag über Fahr Preisbetrag gezeichnet")

## <a name="next-lesson"></a>Nächste Lektion

[Lektion 2: Erstellen von Datenfunktionen mit T-SQL](sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[Einrichten von NYC Taxi-Demodaten](demo-data-nyctaxi-in-sql.md)
