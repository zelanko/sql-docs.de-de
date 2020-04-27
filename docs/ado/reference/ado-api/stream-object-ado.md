---
title: Stream-Objekt (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream
helpviewer_keywords:
- Stream object [ADO]
ms.assetid: 0514531f-009d-4519-abc3-d727014a39f1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c70a22a3048c769aac343d51e621e4d755d3baeb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67916718"
---
# <a name="stream-object-ado"></a>Stream-Objekt (ADO)
Stellt einen Stream von Binärdaten oder Text dar.  
  
 In Struktur strukturierten Hierarchien, wie z. b. einem Dateisystem oder einem e-Mail-System, kann ein [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) über einen standardmäßigen binären Stream von Bits verfügen, der den Inhalt der Datei oder der e-Mail enthält. Ein **Stream** -Objekt kann verwendet werden, um Felder oder Datensätze zu bearbeiten, die diese Datenströme enthalten. Ein **Stream** -Objekt kann auf folgende Weise abgerufen werden:  
  
-   Aus einer URL, die auf ein Objekt (in der Regel eine Datei) verweist, das binäre Daten oder Textdaten enthält. Bei diesem Objekt kann es sich um ein einfaches Dokument, ein **Daten Satz** Objekt, das ein strukturiertes Dokument darstellt, oder einen Ordner handeln.  
  
-   Durch Öffnen des einem **Datensatz** -Objekt zugeordneten **standardstreamobjekts** . Sie können den Standardstream abrufen, der einem **Datensatz** -Objekt zugeordnet ist, wenn der **Datensatz** geöffnet wird, um einen Roundtrip zu vermeiden, um den Stream zu öffnen.  
  
-   Durch Instanziieren eines **Streamobjekts** . Diese **Streamobjekte** können verwendet werden, um Daten für die Zwecke ihrer Anwendung zu speichern. Im Gegensatz zu einem **Stream** , der einer URL oder dem Standarddaten **Strom** eines **Datensatzes**zugeordnet ist, hat ein instanziierter **Stream** standardmäßig keine Zuordnung zu einer zugrunde liegenden Quelle.  
  
 Mit den Methoden und Eigenschaften eines **Stream** -Objekts können Sie folgende Aufgaben ausführen:  
  
-   Öffnen Sie ein **Stream** -Objekt aus einem **Datensatz** oder einer URL mit der [Open](../../../ado/reference/ado-api/open-method-ado-stream.md) -Methode.  
  
-   Schließen Sie einen **Stream** mit der [Close](../../../ado/reference/ado-api/close-method-ado.md) -Methode.  
  
-   Eingabe Bytes oder Text in einen **Stream** mit den [Write](../../../ado/reference/ado-api/write-method.md) -und Write- [Text](../../../ado/reference/ado-api/writetext-method.md) -Methoden.  
  
-   Liest Bytes aus dem **Stream** mit den [Read](../../../ado/reference/ado-api/read-method.md) -und Read- [Text](../../../ado/reference/ado-api/readtext-method.md) -Methoden.  
  
-   Schreiben Sie mit der [Flush](../../../ado/reference/ado-api/flush-method-ado.md) -Methode alle **Streamdaten** , die sich noch im ADO-Puffer befinden, in das zugrunde liegende Objekt  
  
-   Kopieren Sie den Inhalt eines **Streams** mit der [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) -Methode in einen anderen **Stream** .  
  
-   Steuern Sie, wie Zeilen mit der [SkipLine](../../../ado/reference/ado-api/skipline-method.md)-Methode und der [lineseparser](../../../ado/reference/ado-api/lineseparator-property-ado.md) -Eigenschaft aus der Quelldatei gelesen werden.  
  
-   Bestimmen Sie das Ende der Streamposition mit der [EOS](../../../ado/reference/ado-api/eos-property.md)- [Eigenschaft](../../../ado/reference/ado-api/seteos-method.md) und der-Methode.  
  
-   Speichern und Wiederherstellen von Daten in Dateien mit den Methoden " [savedefile](../../../ado/reference/ado-api/savetofile-method.md)" und " [LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md) ".  
  
-   Geben Sie den Zeichensatz an, der zum Speichern des **Streams** mit der [CharSet](../../../ado/reference/ado-api/charset-property-ado.md) -Eigenschaft verwendet wird.  
  
-   Stoppt einen asynchronen **streamvorgang** mit der [Cancel](../../../ado/reference/ado-api/cancel-method-ado.md) -Methode.  
  
-   Bestimmen Sie die Anzahl der Bytes in einem **Stream** mit der [size](../../../ado/reference/ado-api/size-property-ado-stream.md) -Eigenschaft.  
  
-   Steuern der aktuellen Position innerhalb eines **Streams** mit der [Positions](../../../ado/reference/ado-api/position-property-ado.md) -Eigenschaft.  
  
-   Bestimmen Sie den Typ der Daten in einem **Stream** mit der [Type](../../../ado/reference/ado-api/type-property-ado-stream.md) -Eigenschaft.  
  
-   Bestimmen Sie den aktuellen Status des **Streams** (geschlossen, geöffnet oder ausgeführt) mit der [State](../../../ado/reference/ado-api/state-property-ado.md) -Eigenschaft.  
  
-   Geben Sie den Zugriffsmodus für den Daten **Strom** mit der [Mode](../../../ado/reference/ado-api/mode-property-ado.md) -Eigenschaft an.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Das **Stream** -Objekt ist für die Skripterstellung sicher.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Streamen von Objekteigenschaften, Methoden und Ereignissen](../../../ado/reference/ado-api/stream-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datensätze und Datenströme](../../../ado/guide/data/records-and-streams.md)
