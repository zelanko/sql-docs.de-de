---
title: Abrufen von Daten mittels AdomdDataReader | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- retrieving data
- AdomdDataReader object
- data retrieval [ADOMD.NET], AdomdDataReader object
ms.assetid: 8ed7ea26-b5f8-4852-80fc-75dd62df5b3a
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5631238b78804bb593e8db90f910aec0ddebb933
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321230"
---
# <a name="retrieving-data-using-the-adomddatareader"></a>Abrufen von Daten mittels AdomdDataReader
  Beim Abruf von analytischen Daten stellt das <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekt ein ausgewogenes Gleichgewicht zwischen Verwaltung und Interaktivität bereit. Das <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekt ruft einen schreibgeschützten, vereinfachten Vorwärtsdatenstrom von einer analytischen Datenquelle ab. Dieser nicht zwischengespeicherte Datenstrom ermöglicht es der prozeduralen Logik, die Ergebnisse von einer analytischen Datenquelle effektiv sequenziell zu verarbeiten. Daher ist <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> eine gute Wahl für das Abrufen großer Datenmengen zu Anzeigezwecken, da die Daten nicht zwischengespeichert werden.  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> kann darüber hinaus die Anwendungsleistung erhöhen, indem Daten abgerufen werden, sobald diese zur Verfügung stehen, anstatt darauf zu warten, dass die vollständigen Ergebnisse der Abfrage zurückgegeben werden. <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> reduziert des Weiteren den Systemverwaltungsaufwand, da dieser Leser standardmäßig nur jeweils eine Zeile speichert.  
  
 Der Nachteil der optimierten Leistung ist, dass das <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekt weniger Informationen über die abgerufenen Daten bereitstellt als andere Datenabrufmethoden. Das <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekt unterstützt kein großes Objektmodell für die Darstellung von Daten oder Metadaten. Darüber hinaus ermöglicht dieses Objektmodell keine komplexeren Analysefunktionen, wie beispielsweise Zellenrückschreiben. Allerdings bietet das <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekt eine Gruppe von Methoden mit starker Typisierung für das Abrufen von Cellset-Daten und eine Methode für das Abrufen von Cellset-Metadaten im Tabellenformat. Darüber hinaus <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> implementiert die **IDbDataReader** -Schnittstelle für die Unterstützung von Datenbindung und das Abrufen von Daten mithilfe der `SelectCommand` -Methode, aus der **"System.Data"** Namespace der Microsoft .NET Framework-Klassenbibliothek.  
  
## <a name="retrieving-data-from-the-adomddatareader"></a>Abrufen von Daten aus AdomdDataReader  
 Um das <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekt für das Abrufen von Daten zu verwenden, führen Sie die folgenden Schritte durch:  
  
1.  **Erstellen Sie eine neue Instanz des Objekts.**  
  
     Um eine neue Instanz der <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Klasse zu erstellen, rufen Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A>- oder <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A>-Methode des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>-Objekts auf.  
  
2.  **Abrufen von Daten.**  
  
     Während der Befehl die Abfrage ausführt, gibt ADOMD.NET die Ergebnisse im `Resultset`-Format zurück. Dies ist ein Tabellenformat, wie es in der XML for Analysis-Spezifikation angegeben wird, das die Daten des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekts vereinfacht. In Anbetracht der variablen Dimensionalität derartiger Daten ist das Tabellenformat bei der Abfrage analytischer Daten ungewöhnlich.  
  
     ADOMD.NET speichert diese Tabellenergebnisse im Netzwerkpuffer auf dem Client, bis Sie diese über eine der folgenden Methoden anfordern:  
  
    -   Rufen Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A>-Methode des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekts auf.  
  
         Die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A>-Methode ruft eine Zeile aus den Abfrageergebnissen ab. Sie können dann den Namen oder den Ordnungszahlverweis der Spalte an die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Item%2A>-Eigenschaft übergeben, um auf jede Spalte der zurückgegebenen Zeile zuzugreifen. Der Name der ersten Spalte in der aktuellen Zeile ist beispielsweise ColumnName. Dann geben entweder `reader[0].ToString()` oder `reader["ColumnName"].ToString()` die Inhalte der ersten Spalte in der aktuellen Zeile zurück.  
  
    -   Rufen Sie eine der typisierten Accessormethoden auf.  
  
         <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> stellt eine Reihe an typisierten Accessormethoden bereit – Methoden, über die Sie auf Spaltenwerte in deren systemeigenen Datentypen zugreifen können. Wenn Sie den zugrunde liegenden Datentyp eines Spaltenwerts kennen, verringert eine typisierte Accessormethode den erforderlichen Aufwand für die Typkonvertierung beim Abruf des Spaltenwerts und bietet damit die höchste Leistung.  
  
         Zu den verfügbaren typisierten Accessormethoden gehören <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDateTime%2A>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDouble%2A> und <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetInt32%2A>. Eine vollständige Liste der typisierten Accessormethoden finden Sie unter <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
3.  **Schließen Sie den Leser ein.**  
  
     Sie sollten immer die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Close%2A>-Methode aufrufen, wenn Sie die Verwendung des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekts abgeschlossen haben. Während eine Instanz eines <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekts geöffnet ist, wird <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> ausschließlich von diesem <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> verwendet. Sie sind in diesem Fall nicht in der Lage, Befehle auf einer Instanz von <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> auszuführen, einschließlich der Erstellung eines weiteren <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> oder `System.Xml.XmlReader`, bis Sie den ursprünglichen <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> schließen.  
  
### <a name="example-of-retrieving-data-from-the-adomddatareader"></a>Beispiel für das Abrufen von Daten aus AdomdDataReader  
 Das folgende Codebeispiel führt eine Iteration durch ein <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekt durch und gibt die ersten beiden Werte aus jeder Zeile als Zeichenfolgen zurück.  
  
```vb  
If Reader.HasRows Then  
    Do While objReader.Read()  
        Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
            objReader.GetString(0), objReader.GetString(1))  
    Loop  
Else  
  Console.WriteLine("No rows returned.")  
End If  
  
objReader.Close()  
```  
  
```csharp  
if (objReader.HasRows)  
  while (objReader.Read())  
    Console.WriteLine("\t{0}\t{1}", _  
        objReader.GetString(0), objReader.GetString(1));  
else  
  Console.WriteLine("No rows returned.");  
  
objReader.Close();  
```  
  
## <a name="retrieving-metadata-from-the-adomddatareader"></a>Abrufen von Metadaten aus AdomdDataReader  
 Während eine Instanz eines <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> -Objekts geöffnet ist, können Sie Schemainformationen oder Metadaten über den aktuellen Recordset mithilfe der <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A>-Methode abrufen. <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A>Gibt eine `DataTable` Objekt, das mit den Schemainformationen für das aktuelle Recordset gefüllt ist. Die `DataTable` enthält eine Zeile für jede Spalte des Recordsets. Jede Spalte der Schematabellenzeile ist einer Eigenschaft der im Cellset zurückgegebenen Spalte zugeordnet, wobei `ColumnName` der Name der Eigenschaft und der Wert der Spalte der Wert der Eigenschaft ist.  
  
### <a name="example-of-retrieving-metadata-from-the-adomddatareader"></a>Beispiel für das Abrufen von Metadaten aus AdomdDataReader  
 Im folgenden Codebeispiel werden die Schemainformationen für ein <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekt ausgeschrieben.  
  
```vb  
Dim schemaTable As DataTable = objReader.GetSchemaTable()  
  
Dim objRow As DataRow  
Dim objColumn As DataColumn  
  
For Each objRow In schemaTable.Rows  
  For Each objColumn In schemaTable.Columns  
    Console.WriteLine(objColumn.ColumnName & " = " & objRow(objColumn).ToString())  
  Next  
  Console.WriteLine()  
Next  
DataTable schemaTable = objReader.GetSchemaTable();  
```  
  
```csharp  
foreach (DataRow objRow in schemaTable.Rows)  
{  
  foreach (DataColumn objColumn in schemaTable.Columns)  
    Console.WriteLine(objColumn.ColumnName + " = " + objRow[objColumn]);  
  Console.WriteLine();  
}  
```  
  
## <a name="retrieving-multiple-result-sets"></a>Abrufen mehrerer Resultsets  
 Data Mining unterstützt das Konzept der geschachtelten Tabellen, welche ADOMD.NET als geschachtelte Rowsets verfügbar macht. Um das jeder Zeile zugehörige Rowset abzurufen, rufen Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDataReader%2A>-Methode auf.  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen von Daten aus einer analytischen Datenquelle](retrieving-data-from-an-analytical-data-source.md)   
 [Abrufen von Daten mittels CellSet](retrieving-data-using-the-cellset.md)   
 [Abrufen von Daten mittels XmlReader](retrieving-data-using-the-xmlreader.md)  
  
  
