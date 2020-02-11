---
title: Foreach-Schleifencontainer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.f1
helpviewer_keywords:
- repeating control flow
- Foreach Loop containers
- foreach enumerators [Integration Services]
- containers [Integration Services], Foreach Loop
ms.assetid: dd6cc2ba-631f-4adf-89dc-29ef449c6933
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bb50b4000397ca3dd51be58867e45135d1d587f1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62831579"
---
# <a name="foreach-loop-container"></a>Foreach-Schleifencontainer
  Der Foreach-Schleifencontainer definiert eine sich wiederholende Ablaufsteuerung in einem Paket. Die Schleifenimplementierung ist mit der **Foreach**-Schleifenstruktur in Programmiersprachen zu vergleichen. In einem Paket wird die Schleife mithilfe eines Foreach-Enumerators aktiviert.  Der Foreach-Schleifencontainer wiederholt die Ablaufsteuerung für jedes Element eines angegebenen Enumerators.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] stellt die folgenden Enumeratortypen bereit:  
  
-   Foreach-ADO-Enumerator zum Aufzählen von Zeilen in Tabellen. Beispielsweise können Sie die Zeilen in einem ADO-Recordset abrufen.  
  
     Stattdessen speichert das Recordsetziel Daten im Speicher eines Recordsets, das in einer `Object`-Paketvariablen des Datentyps gespeichert ist. Sie verwenden einen Foreach-Schleifencontainer mit dem Foreach-ADO-Enumerator normalerweise, um die Zeilen eines Recordsets nacheinander zu verarbeiten. Die für den Foreach-ADO-Enumerator angegebene Variable muss vom Object-Datentyp sein. Weitere Informationen zum Recordsetziel finden Sie unter [Use a Recordset Destination](../data-flow/recordset-destination.md).  
  
-   Enumerator für Foreach-ADO.NET-Schemarowsets zum Aufzählen der Schemainformationen zu einer Datenquelle. Beispielsweise können Sie eine Liste der Tabellen in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbank auflisten und erhalten.  
  
-   Foreach-Datei-Enumerator zum Aufzählen von Dateien in einem Ordner. Der Enumerator kann Unterordner durchlaufen. Beispielsweise können Sie alle Dateien mit der Dateinamenerweiterung LOG im Windows-Ordner und in dessen Unterordnern lesen.  
  
-   Foreach-Enumerator für Daten aus Variablen zum Aufzählen des aufzählbaren Objekts, das in einer angegebenen Variable enthalten ist. Das aufzählbare Objekt kann z. B. ein Array, ein ADO.NET `DataTable`-Objekt oder ein [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Enumerator sein. Beispielsweise können Sie die Werte eines Arrays aufzählen, das Servernamen enthält.  
  
-   Foreach-Element-Enumerator zum Aufzählen von Elementen, bei denen es sich um Sammlungen handelt. Beispielsweise können Sie die Namen der ausführbaren Dateien und Arbeitsverzeichnisse aufzählen, die ein Task „Prozess ausführen“ verwendet.  
  
-   Foreach-NodeList-Enumerator zum Aufzählen des Resultsets eines XPATH-Ausdrucks (XML Path Language). Beispielsweise zählt der folgende Ausdruck alle Autoren der Klassik auf und ruft eine Liste dafür ab: `/authors/author[@period='classical']`.  
  
-   Foreach-SMO-Enumerator zum Aufzählen von SMO-Objekten ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects). Beispielsweise können Sie die Sichten in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank aufzählen und eine Liste dafür abrufen.  
  
-   Foreach-Azure-Blob-Enumerator zum Aufzählen von Blobs in einem BLOB-Container in einem Azure-Speicher.  
  
-   Foreach-ADLS-Datei-Enumerator zum Aufzählen von Dateien in einem ADLS-Verzeichnis.
  
 Das folgende Diagramm zeigt einen Foreach-Schleifencontainer mit einem Dateisystemtask. Die Foreach-Schleife verwendet den Foreach-Datei-Enumerator, und der Dateisystemtask ist so konfiguriert, dass eine Datei kopiert wird. Falls der vom Enumerator angegebene Ordner vier Dateien enthält, wird die Schleife viermal wiederholt, und die vier Dateien werden kopiert.  
  
 ![Foreach-Schleifencontainer, der einen Ordner aufzählt](../media/ssis-foreachloop.gif "Foreach-Schleifencontainer, der einen Ordner aufzählt")  
  
 Sie können eine Kombination aus Variablen und Eigenschaftsausdrücken verwenden, um die Paketobjekteigenschaft mit dem Wert aus der Enumeratorsammlung zu aktualisieren. Zunächst ordnen Sie den Sammlungswert einer benutzerdefinierten Variablen zu. Anschließend implementieren Sie einen Eigenschaftsausdruck für die Eigenschaft, die die Variable verwendet. Beispielsweise wird der Auflistungs Wert des Foreach-Datei Enumerators einer Variablen mit dem `MyFile` Namen zugeordnet, und die Variable wird dann im Eigenschafts Ausdruck für die Eigenschaft Betreff eines Tasks vom Typ "Mail senden" verwendet. Beim Ausführen des Pakets wird die Subject-Eigenschaft bei jeder Wiederholung der Schleife mit dem Namen einer Datei aktualisiert. Weitere Informationen finden Sie unter [Verwenden von Eigenschaftsausdrücken in Paketen](../expressions/use-property-expressions-in-packages.md).  
  
 Variablen, die dem Enumeratorsammlungswert zugeordnet sind, können auch in Ausdrücken und Skripts verwendet werden.  
  
 Ein Foreach-Schleifencontainer kann mehrere Tasks und Container umfassen, aber nur einen Enumeratortyp verwenden. Falls der Foreach-Schleifencontainer mehrere Tasks umfasst, können Sie den Enumeratorsammlungswert mehreren Eigenschaften jedes Tasks zuordnen.  
  
 Sie können ein Transaktionsattribut für den Foreach-Schleifencontainer festlegen, um eine Transaktion für eine Teilmenge der Paketablaufsteuerung zu definieren. Auf diese Weise können Sie Transaktionen statt auf der Paketebene auf der Ebene der Foreach-Schleife verwalten. Wenn z. B. ein Foreach-Schleifencontainer eine Ablaufsteuerung wiederholt, die Dimensions- und Faktentabellen in einem Sternschema aktualisiert, können Sie eine Transaktion konfigurieren, um sicherzustellen, dass entweder alle oder überhaupt keine Faktentabellen aktualisiert werden. Weitere Informationen finden Sie unter [Integration Services-Transaktionen](../integration-services-transactions.md).  
  
## <a name="enumerator-types"></a>Enumeratortypen  
 Enumeratoren sind konfigurierbar, und je nach Enumerator müssen Sie unterschiedliche Informationen angeben.  
  
 In der folgenden Tabelle sind die Informationen zusammengefasst, die für die einzelnen Enumeratortypen erforderlich sind.  
  
|Enumerator|Konfigurationsanforderungen|  
|----------------|--------------------------------|  
|Foreach-ADO-Enumerator|Geben Sie die ADO-Objektquellvariable und den Enumeratormodus an. Die Variable muss vom Datentyp „Object“ sein.|  
|Enumerator für Foreach-ADO.NET-Schemarowset|Geben Sie die Verbindung mit einer Datenbank und das aufzuzählende Schema an.|  
|Foreach-Datei-Enumerator|Geben Sie einen Ordner sowie die aufzuzählenden Dateien und das Format des Dateinamens der abgerufenen Dateien an. Geben Sie ferner an, ob Unterordner durchlaufen werden sollen.|  
|Foreach-Enumerator für Daten aus Variable|Geben Sie die Variable an, die die aufzuzählenden Objekte enthält.|  
|Foreach-Element-Enumerator|Definieren Sie die Elemente in der Foreach-Element-Sammlung, einschließlich der Spalten und Spaltendatentypen.|  
|Foreach-NodeList-Enumerator|Geben Sie die Quelle des XML-Dokuments an, und konfigurieren Sie den XPath-Vorgang.|  
|Foreach-SMO-Enumerator|Geben Sie die Verbindung mit einer Datenbank und die aufzuzählenden SMO-Objekte an.|  
|Foreach-Azure-Blob-Enumerator|Geben Sie den Azure-BLOB-Container an, der die aufzuzählenden BLOBs enthält.|  
|Foreach-ADLS-Datei|Geben Sie das ADLS-Verzeichnis an, das die aufzuzählenden Dateien enthält, sowie einige Filter.|
  
## <a name="property-expressions-in-foreach-loop-containers"></a>Eigenschaftsausdrücke in Foreach-Schleifencontainern  
 Pakete können so konfiguriert werden, dass mehrere ausführbare Dateien gleichzeitig ausgeführt werden. Diese Konfiguration sollte mit Vorsicht verwendet werden, wenn das Paket einen Foreach-Schleifencontainer enthält, der Eigenschaftsausdrücke implementiert.  
  
 Es ist häufig nützlich, einen Eigenschaftsausdruck zu implementieren, um den Wert der ConnectionString-Eigenschaft des Verbindungs-Managers festzulegen, den die Foreach-Schleifenenumeratoren verwenden. Der ConnectionString-Eigenschaftsausdruck wird durch eine Variable festgelegt, die dem Sammlungswert des Enumerators zugeordnet ist und bei jeder Iteration der Schleife aktualisiert wird.  
  
 Das Paket sollte so konfiguriert sein, dass jeweils nur eine ausführbare Datei ausgeführt wird, um in der Schleife negative Auswirkungen einer unbestimmten Zeitvorgabe der parallelen Taskausführung zu vermeiden. Wenn beispielsweise ein Paket mehrere Tasks gleichzeitig ausführen kann, können bei einem Foreach-Schleifencontainer, der im Ordner vorhandene Dateien aufzählt, die Dateinamen abruft und dann mithilfe eines Tasks „SQL ausführen“ die Dateinamen in eine Tabelle einfügt, Schreibkonflikte auftreten, falls zwei Instanzen des Tasks „SQL ausführen“ gleichzeitig zu schreiben versuchen. Weitere Informationen finden Sie unter [Verwenden von Eigenschaftsausdrücken in Paketen](../expressions/use-property-expressions-in-packages.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um nähere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Konfigurieren eines Foreach-Schleifencontainers](foreach-loop-container.md)  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum programmgesteuerten Festlegen dieser Eigenschaften anzuzeigen:  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Blogeintrag [SSIS – Foreach NodeList-Enumerator](https://go.microsoft.com/fwlink/?LinkId=220671)auf  auf bidn.combidn.com.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ablaufsteuerung](control-flow.md)   
 [SQL Server Integration Services-Container](integration-services-containers.md)  
  
  
