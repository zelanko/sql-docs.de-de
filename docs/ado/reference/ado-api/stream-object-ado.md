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
manager: craigg
ms.openlocfilehash: 976e822482efc530e3b055f61c242ee03a30e012
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63179833"
---
# <a name="stream-object-ado"></a>Stream-Objekt (ADO)
Stellt einen Datenstrom von Binärdaten oder Text dar.  
  
 In Hierarchien Strukturbaums, z. B. ein Dateisystem oder eine e-Mail-System eine [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) möglicherweise standardmäßig Binärdatenstrom Bits zugeordnet, die den Inhalt der Datei oder die e-Mail-Nachricht enthält. Ein **Stream** Objekt kann verwendet werden, um die Felder oder Einträge mit diese Datenströme zu bearbeiten. Ein **Stream** -Objekt abgerufen werden kann, auf folgende Weise:  
  
-   Über eine URL verweist auf ein Objekt (i. d. r. eine Datei), Binär oder Text-Daten enthält. Dieses Objekt kann ein einfaches Dokument, eine **Datensatz** Objekt, das ein strukturiertes Dokument oder einen Ordner darstellt.  
  
-   Durch Öffnen des **Stream** zugeordnete Objekt ein **Datensatz** Objekt. Sie erhalten den Standarddatenstrom zugeordnet eine **Datensatz** Objekt bei der **Datensatz** geöffnet wird, um einen Roundtrip zum Öffnen des Datenstroms zu entfernen.  
  
-   Durch die Instanziierung einer **Stream** Objekt. Diese **Stream** Objekte können zum Speichern von Daten im Rahmen Ihrer Anwendung verwendet werden. Im Gegensatz zu einer **Stream** eine URL oder die zugeordnete **Stream** von einer **Datensatz**, instanziierten **Stream** nicht zugeordnet ein zugrunde liegende Quelle standardmäßig.  
  
 Mit den Methoden und Eigenschaften einer **Stream** -Objekts können Sie folgende Möglichkeiten:  
  
-   Öffnen einer **Stream** -Objekt aus einer **Datensatz** oder eine URL mit der [öffnen](../../../ado/reference/ado-api/open-method-ado-stream.md) Methode.  
  
-   Schließen einer **Stream** mit der [schließen](../../../ado/reference/ado-api/close-method-ado.md) Methode.  
  
-   Eingeben von Bytes oder Text, der eine **Stream** mit der [schreiben](../../../ado/reference/ado-api/write-method.md) und [WriteText](../../../ado/reference/ado-api/writetext-method.md) Methoden.  
  
-   Lesen von Bytes aus dem **Stream** mit der [lesen](../../../ado/reference/ado-api/read-method.md) und [ReadText](../../../ado/reference/ado-api/readtext-method.md) Methoden.  
  
-   Schreiben Sie eine beliebige **Stream** Datenpuffers noch im ADO, auf das zugrunde liegende Objekt mit der [leeren](../../../ado/reference/ado-api/flush-method-ado.md) Methode.  
  
-   Kopieren Sie den Inhalt von einer **Stream** in ein anderes **Stream** mit der [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) Methode.  
  
-   Steuern Sie, wie Zeilen gelesen werden, aus der Quelldatei mit der [SkipLine](../../../ado/reference/ado-api/skipline-method.md)Methode und die [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) Eigenschaft.  
  
-   Bestimmen Sie das Ende des Streamposition mit der [EOS](../../../ado/reference/ado-api/eos-property.md)Eigenschaft und [SetEOS](../../../ado/reference/ado-api/seteos-method.md) Methode.  
  
-   Speichern und Wiederherstellen von Daten in Dateien mit der [SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)und [LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md) Methoden.  
  
-   Geben Sie den Zeichensatz für die Speicherung von der **Stream** mit der [Charset](../../../ado/reference/ado-api/charset-property-ado.md) Eigenschaft.  
  
-   Anhalten eines asynchronen **Stream** Vorgang mit der [Abbrechen](../../../ado/reference/ado-api/cancel-method-ado.md) Methode.  
  
-   Bestimmen Sie die Anzahl der Bytes in einem **Stream** mit der [Größe](../../../ado/reference/ado-api/size-property-ado-stream.md) Eigenschaft.  
  
-   Steuern Sie die aktuelle Position in einem **Stream** mit der [Position](../../../ado/reference/ado-api/position-property-ado.md) Eigenschaft.  
  
-   Bestimmen Sie den Typ der Daten in einem **Stream** mit der [Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) Eigenschaft.  
  
-   Bestimmen des aktuellen Status von der **Stream** (geschlossen, geöffnet oder ausgeführt) mit der [Zustand](../../../ado/reference/ado-api/state-property-ado.md) Eigenschaft.  
  
-   Geben Sie den Zugriffsmodus für die **Stream** mit der [Modus](../../../ado/reference/ado-api/mode-property-ado.md) Eigenschaft.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Die **Stream** Objekt für die Skripterstellung sicher ist.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Stream-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/stream-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datensätze und Datenströme](../../../ado/guide/data/records-and-streams.md)
