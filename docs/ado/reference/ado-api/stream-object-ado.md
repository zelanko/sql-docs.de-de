---
description: Stream-Objekt (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: de91c32d62a0180ccab263ececd9e2f9e0442aed
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777229"
---
# <a name="stream-object-ado"></a>Stream-Objekt (ADO)
Stellt einen Stream von Binärdaten oder Text dar.  
  
 In Struktur strukturierten Hierarchien, wie z. b. einem Dateisystem oder einem e-Mail-System, kann ein [Datensatz](./record-object-ado.md) über einen standardmäßigen binären Stream von Bits verfügen, der den Inhalt der Datei oder der e-Mail enthält. Ein **Stream** -Objekt kann verwendet werden, um Felder oder Datensätze zu bearbeiten, die diese Datenströme enthalten. Ein **Stream** -Objekt kann auf folgende Weise abgerufen werden:  
  
-   Aus einer URL, die auf ein Objekt (in der Regel eine Datei) verweist, das binäre Daten oder Textdaten enthält. Bei diesem Objekt kann es sich um ein einfaches Dokument, ein **Daten Satz** Objekt, das ein strukturiertes Dokument darstellt, oder einen Ordner handeln.  
  
-   Durch Öffnen des einem **Datensatz** -Objekt zugeordneten **standardstreamobjekts** . Sie können den Standardstream abrufen, der einem **Datensatz** -Objekt zugeordnet ist, wenn der **Datensatz** geöffnet wird, um einen Roundtrip zu vermeiden, um den Stream zu öffnen.  
  
-   Durch Instanziieren eines **Streamobjekts** . Diese **Streamobjekte** können verwendet werden, um Daten für die Zwecke ihrer Anwendung zu speichern. Im Gegensatz zu einem **Stream** , der einer URL oder dem Standarddaten **Strom** eines **Datensatzes**zugeordnet ist, hat ein instanziierter **Stream** standardmäßig keine Zuordnung zu einer zugrunde liegenden Quelle.  
  
 Mit den Methoden und Eigenschaften eines **Stream** -Objekts können Sie folgende Aufgaben ausführen:  
  
-   Öffnen Sie ein **Stream** -Objekt aus einem **Datensatz** oder einer URL mit der [Open](./open-method-ado-stream.md) -Methode.  
  
-   Schließen Sie einen **Stream** mit der [Close](./close-method-ado.md) -Methode.  
  
-   Eingabe Bytes oder Text in einen **Stream** mit den [Write](./write-method.md) -und Write- [Text](./writetext-method.md) -Methoden.  
  
-   Liest Bytes aus dem **Stream** mit den [Read](./read-method.md) -und Read- [Text](./readtext-method.md) -Methoden.  
  
-   Schreiben Sie mit der [Flush](./flush-method-ado.md) -Methode alle **Streamdaten** , die sich noch im ADO-Puffer befinden, in das zugrunde liegende Objekt  
  
-   Kopieren Sie den Inhalt eines **Streams** mit der [CopyTo](./copyto-method-ado.md) -Methode in einen anderen **Stream** .  
  
-   Steuern Sie, wie Zeilen mit der [SkipLine](./skipline-method.md)-Methode und der [lineseparser](./lineseparator-property-ado.md) -Eigenschaft aus der Quelldatei gelesen werden.  
  
-   Bestimmen Sie das Ende der Streamposition mit der [EOS](./eos-property.md)- [Eigenschaft](./seteos-method.md) und der-Methode.  
  
-   Speichern und Wiederherstellen von Daten in Dateien mit den Methoden " [savedefile](./savetofile-method.md)" und " [LoadFromFile](./loadfromfile-method-ado.md) ".  
  
-   Geben Sie den Zeichensatz an, der zum Speichern des **Streams** mit der [CharSet](./charset-property-ado.md) -Eigenschaft verwendet wird.  
  
-   Stoppt einen asynchronen **streamvorgang** mit der [Cancel](./cancel-method-ado.md) -Methode.  
  
-   Bestimmen Sie die Anzahl der Bytes in einem **Stream** mit der [size](./size-property-ado-stream.md) -Eigenschaft.  
  
-   Steuern der aktuellen Position innerhalb eines **Streams** mit der [Positions](./position-property-ado.md) -Eigenschaft.  
  
-   Bestimmen Sie den Typ der Daten in einem **Stream** mit der [Type](./type-property-ado-stream.md) -Eigenschaft.  
  
-   Bestimmen Sie den aktuellen Status des **Streams** (geschlossen, geöffnet oder ausgeführt) mit der [State](./state-property-ado.md) -Eigenschaft.  
  
-   Geben Sie den Zugriffsmodus für den Daten **Strom** mit der [Mode](./mode-property-ado.md) -Eigenschaft an.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../guide/data/absolute-and-relative-urls.md).  
  
 Das **Stream** -Objekt ist für die Skripterstellung sicher.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Streamen von Objekteigenschaften, Methoden und Ereignissen](./stream-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datensätze und Datenströme](../../guide/data/records-and-streams.md)