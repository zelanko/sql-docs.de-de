---
description: Datensätze und Datenströme
title: Datensätze und Streams | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8afaae4221c57a7f7d832c34f0a374981e081cf6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452982"
---
# <a name="records-and-streams"></a>Datensätze und Datenströme
ADO stellt derzeit das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt als primäres Mittel für den Zugriff auf Informationen in Datenquellen, z. b. relationale Datenbanken, bereit. Einige Anbieter unterstützen jedoch die [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -und [Streamobjekte](../../../ado/reference/ado-api/stream-object-ado.md) als Alternative oder ergänzende Objekte, mit denen Daten von Anbietern bearbeitet werden können. Einzelheiten zum **Daten Satz** Verhalten finden Sie in der Dokumentation Ihres Anbieters.  
  
## <a name="records"></a>Datensätze  
 **Daten Satz** Objekte funktionieren im Wesentlichen als einzeilige **Recordsets**. Allerdings weisen **Datensätze** im Vergleich zu **Recordsets** eingeschränkte Funktionalität auf, und Sie verfügen über unterschiedliche Eigenschaften und Methoden. Die Quelle für die Daten in einem **Datensatz** -Objekt kann ein Befehl sein, der eine Daten Zeile vom Anbieter zurückgibt. Wenn Sie Daten **Satz** Objekte anstelle von **Recordset** -Objekten verwenden, um die Ergebnisse einer Abfrage zu empfangen, die eine Daten Zeile zurückgibt, entfällt der Aufwand der Instanziierung des komplexeren **Recordsetobjekts** .  
  
 Daten **Satz** Objekte können einen anderen Zweck erfüllen, insbesondere bei Anbietern für andere Datenquellen als herkömmliche relationale Datenbanken, wie z. b. den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Ein Großteil der Informationen, die verarbeitet werden müssen, ist nicht als Tabellen in Datenbanken, sondern als Nachrichten in elektronischen e-Mail-Systemen und Dateien in modernen Dateisystemen vorhanden. Der **Datensatz** und die **Streamobjekte** vereinfachen den Zugriff auf Informationen, die in anderen Quellen als relationalen Datenbanken gespeichert sind.  
  
 Das **Datensatz** -Objekt kann Daten, z. b. Verzeichnisse und Dateien in einem Dateisystem oder in Ordnern und Meldungen in einem e-Mail-System, darstellen und verwalten. Zu diesem Zweck kann die Quelle für den **Datensatz** die aktuelle Zeile eines geöffneten **Recordsets**, eine absolute URL oder eine relative URL in Verbindung mit einem geöffneten [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt sein.  
  
 In der Regel kann ein **Recordset** verwendet werden, um einen Container oder ein übergeordnetes Element in einer Hierarchie (z. b. Ordner oder Verzeichnis) darzustellen. Ein **Datensatz** kann verwendet werden, um bestimmte Informationen zu einem Knoten im übergeordneten Container zurückzugeben, z. b. eine Datei oder ein Dokument. Der Hauptgrund für Daten **Sätze** ist, diese Art von Informationen darzustellen, dass diese Datenquellen heterogen sind. Dies bedeutet, dass jeder **Datensatz** einen anderen Satz und eine andere Anzahl von Feldern aufweisen kann. Herkömmliche **Recordsets** , die Zeilen aus einer Datenbank enthalten, sind homogen, was bedeutet, dass jede Zeile dieselbe Anzahl und denselben Typ von Feldern hat.  
  
 Weitere Informationen zur Verwendung des **Datensatz** -Objekts für die Verarbeitung dieser heterogenen Daten von Anbietern, wie z. b. dem Internet Publishing Provider, finden Sie unter [Verwenden von ADO für die Internetveröffentlichung](../../../ado/guide/data/using-ado-for-internet-publishing.md).  
  
## <a name="streams"></a>Datenströme  
 Das **Stream** -Objekt bietet die Möglichkeit, einen Bytestream zu lesen, zu schreiben und zu verwalten. Dieser Bytestream kann Text oder binär sein und ist nur durch Systemressourcen beschränkt. In der Regel werden ADO- **Streamobjekte** für folgende Zwecke verwendet:  
  
-   , Wenn die Daten eines im XML-Format gespeicherten **Recordsets** enthalten sein sollen. Diese XML-Streams aus gespeicherten **Recordsets**können als Quelle beim Öffnen eines neuen **Recordsets**verwendet werden. Weitere Informationen finden Sie unter [Streams und Persistenz](../../../ado/guide/data/streams-and-persistence.md).  
  
-   , Um [commandstreams](../../../ado/reference/ado-api/commandstream-property-ado.md) zu enthalten, die für den Anbieter als Alternative zu [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)ausgeführt werden sollen. XML-Update grams können z. b. als Quelle für einen Befehl für den Microsoft OLE DB-Anbieter für SQL Server verwendet werden.  
  
-   Zum Empfangen von Ergebnissen vom Anbieter in einem anderen Format als einem **Recordset**, z. b. XML-Ergebnisse des Microsoft OLE DB-Anbieters für SQL Server. Weitere Informationen finden Sie unter [Abrufen von Resultsets in Streams](../../../ado/guide/data/retrieving-resultsets-into-streams.md).  
  
-   , Um den Text oder die Bytes zu enthalten, die eine Datei oder Nachricht enthalten, die in der Regel mit Anbietern wie dem Microsoft OLE DB-Anbieter für die Internet Veröffentlichung verwendet wird. Weitere Informationen zu dieser Verwendung von **Streamobjekten** finden Sie unter [Verwenden von ADO für die Internet Veröffentlichung](../../../ado/guide/data/using-ado-for-internet-publishing.md).  
  
 Ein **Stream** -Objekt kann geöffnet werden für:  
  
-   Eine einfache Datei, die mit einer URL angegeben ist.  
  
-   Ein Feld eines **Datensatzes** oder eines **Recordsets** , das ein **Streamobjekt** enthält.  
  
-   Der Standardstream eines **Datensatz** -oder **Recordset** -Objekts, das ein Verzeichnis oder eine Verbund Datei darstellt.  
  
-   Ein Ressourcen Feld, das die URL einer einfachen Datei enthält.  
  
-   Überhaupt keine bestimmte Quelle. In diesem Fall wird ein **Stream** -Objekt im Arbeitsspeicher geöffnet. Daten können darauf geschrieben und dann in einem anderen **Stream** oder einer anderen Datei gespeichert werden.  
  
-   Ein BLOB-Feld in einem **Recordset**.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Datenströme und Persistenz](../../../ado/guide/data/streams-and-persistence.md)  
  
-   [Command-Datenströme](../../../ado/guide/data/command-streams.md)  
  
-   [Abrufen von Resultsets in Datenströme](../../../ado/guide/data/retrieving-resultsets-into-streams.md)  
  
-   [Verwenden von ADO für die Veröffentlichung im Internet](../../../ado/guide/data/using-ado-for-internet-publishing.md)
