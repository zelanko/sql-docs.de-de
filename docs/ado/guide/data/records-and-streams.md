---
title: Datensätze und Datenströme | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- streams [ADO]
- streams [ADO], about streams
- records [ADO]
ms.assetid: 4d68868e-2611-4b5c-9a89-7caa5f753151
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b9e26930db786b986fd1f4ba633e2cc5953f3df3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681358"
---
# <a name="records-and-streams"></a>Datensätze und Datenströme
ADO bietet derzeit die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt als das primäre Mittel für den Zugriff auf Informationen in den Datenquellen, z. B. relationalen Datenbanken. Einige Anbieter unterstützen jedoch die [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) und [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekte als alternative oder Ergänzung-Objekte, die mit dem Daten von Anbietern bearbeitet werden können. Einzelheiten zur **Datensatz** Verhalten, finden Sie in der Dokumentation des Anbieters.  
  
## <a name="records"></a>Datensätze  
 **Datensatz** Objekte funktionieren im Wesentlichen als einzeilige **Recordset**s. Allerdings **Datensätze** haben eingeschränkte Funktionalität, die im Vergleich zu **Recordsets** und verfügen über unterschiedliche Eigenschaften und Methoden. Die Quelle für die Daten in einem **Datensatz** -Objekt eines Befehls, der eine Zeile mit Daten vom Anbieter zurückgegeben werden kann. Mithilfe von **Datensatz** Objekte statt **Recordset** Objekte auf die Ergebnisse aus einer Abfrage, die eine Zeile mit Daten zurückgibt erübrigt den Aufwand der Instanziierung je komplexer **Recordset**  Objekt.  
  
 **Datensatz** Objekte können einen anderen Zweck dienen, insbesondere bei Anbietern für andere Datenquellen als herkömmlichen relationalen Datenbanken, z. B. die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Ein Großteil der Informationen, die verarbeitet werden muss, vorhanden ist, nicht als Tabellen in Datenbanken, sondern als Nachrichten in e-Mail-Systeme und Dateien in modernen Dateisystemen. Die **Datensatz** und **Stream** Objekte erleichtern den Zugriff auf Informationen aus anderen Quellen als relationale Datenbanken.  
  
 Die **Datensatz** Objekt darstellen und Verwalten von Daten, z. B. Verzeichnisse und Dateien in einem Dateisystem oder Ordner und Nachrichten in einem e-Mail-System kann. Für diese Zwecke, die Quelle für die **Datensatz** möglich, dass die aktuelle Zeile eines geöffneten **Recordset**, eine absolute URL oder eine relative URL in Verbindung mit einem geöffneten [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt.  
  
 In der Regel eine **Recordset** können verwendet werden, um einen Container oder das übergeordnete Element in einer Hierarchie, z. B. einen Ordner oder Verzeichnis darstellen. Ein **Datensatz** können verwendet werden, um bestimmte Informationen zu einem Knoten im übergeordneten Container, z. B. eine Datei oder des Dokuments zurückgeben. Der Hauptgrund **Datensätze** werden verwendet, um diese Art von Informationen darstellen, dass diese Datenquellen heterogen sind. Dies bedeutet, dass jedes **Datensatz** möglicherweise einen anderen Satz und die Anzahl der Felder. Herkömmliche **Recordsets** enthaltenen Zeilen aus einer Datenbank sind homogen, was bedeutet, dass jede Zeile die gleiche Anzahl und Art der Felder enthält.  
  
 Weitere Informationen zur Verwendung der **Datensatz** -Objekt für die Verarbeitung dieser heterogene Daten von Anbietern wie dem Internet-Publishing-Anbieter, finden Sie unter [mithilfe von ADO für Internet Publishing](../../../ado/guide/data/using-ado-for-internet-publishing.md).  
  
## <a name="streams"></a>Datenströme  
 Die **Stream** Objekt bietet die Möglichkeit, lesen, schreiben und verwalten einen Stream von Bytes. Dieser Bytedatenstrom kann Text oder binär sein und ist in ihrer Größe nur durch die verfügbaren Systemressourcen begrenzt. In der Regel ADO **Stream** Objekte werden für folgende Zwecke verwendet:  
  
-   Um die Daten von aufzunehmen eine **Recordset** im XML-Format gespeichert. Diese XML-Streams aus gespeicherten **Recordset**s kann als Quelle verwendet werden, wenn Sie ein neues öffnen **Recordset**. Weitere Informationen finden Sie unter [Streams und Persistenz](../../../ado/guide/data/streams-and-persistence.md).  
  
-   Enthält [CommandStreams](../../../ado/reference/ado-api/commandstream-property-ado.md) für den Anbieter ausgeführt werden, als Alternative zur [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md). Beispielsweise kann XML-UpdateGrams als Quelle für einen Befehl für den Microsoft OLE DB-Anbieter für SQL Server verwendet werden.  
  
-   Ergebnisse als vom Anbieter in einem Format erhält eine **Recordset**, z. B. XML-Ergebnisse aus der Microsoft OLE DB-Anbieter für SQL Server. Weitere Informationen finden Sie unter [Abrufen von Resultsets in Streams](../../../ado/guide/data/retrieving-resultsets-into-streams.md).  
  
-   Enthält den Text oder die Bytes, die eine Datei oder eine Nachricht, die in der Regel mit Anbietern wie Microsoft OLE DB-Anbieter für Internet Publishing verwendet besteht. Weitere Informationen zu dieser Verwendung von **Stream** Objekten finden Sie [mithilfe von ADO für Internet Publishing](../../../ado/guide/data/using-ado-for-internet-publishing.md).  
  
 Ein **Stream** Objekt kann auf geöffnet werden:  
  
-   Eine einfache Datei, die mit einer URL angegeben.  
  
-   Ein Feld einer **Datensatz** oder **Recordset** mit einem **Stream** Objekt.  
  
-   Der standardmäßigen Datenstrom ein **Datensatz** oder **Recordset** Objekt, das ein Verzeichnis oder die Verbunddatei darstellt.  
  
-   Ein Feld für die Ressource, die eine einfache Datei-URL enthält.  
  
-   Kein bestimmtes Quelle. In diesem Fall eine **Stream** Objekt im Arbeitsspeicher geöffnet ist. Daten können in Sie geschrieben wird und dann gespeichert, in einer anderen **Stream** oder Datei.  
  
-   Ein BLOB-Feld in einem **Recordset**.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Streams und Persistenz](../../../ado/guide/data/streams-and-persistence.md)  
  
-   [Command-Streams](../../../ado/guide/data/command-streams.md)  
  
-   [Abrufen von Resultsets in Streams](../../../ado/guide/data/retrieving-resultsets-into-streams.md)  
  
-   [Using ADO for Internet Publishing (Verwenden von ADO für Internet-Publishing)](../../../ado/guide/data/using-ado-for-internet-publishing.md)
