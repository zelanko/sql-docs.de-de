---
title: Record-Objekt (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Record
helpviewer_keywords:
- Record object [ADO]
ms.assetid: db83ed2c-a8e3-460c-8682-64667e4d5d01
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d719ebf47757a48b034d2a0cadd0ed68f51f0ee5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62661631"
---
# <a name="record-object-ado"></a>Record-Objekt (ADO)
Stellt eine Zeile aus einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oder der Datenanbieter oder ein Objekt, das von einem Anbieter von teilweise strukturierten Daten, z. B. einer Datei oder eines Verzeichnisses zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein **Datensatz** -Objekt stellt eine Zeile mit Daten und verfügt über einige grundlegenden ähnlichkeiten mit einer einzeilige **Recordset**. Abhängig von den Funktionen des Anbieters **Datensatz** Objekte können direkt von Ihrem Anbieter, anstatt eine einzelne Zeilen zurückgegeben werden **Recordset**, beispielsweise wenn eine SQL-Abfrage, die nur eine Zeile auswählt. ausgeführt. Oder, eine **Datensatz** -Objekt abgerufen werden kann, direkt aus einer **Recordset** Objekt. Oder, eine **Datensatz** direkt von einem Anbieter zurückgegeben werden kann, um teilweise strukturierte Daten, z. B. Microsoft Exchange-OLE DB-Anbieters.  
  
 Sie können die zugeordneten Felder anzeigen der **Datensatz** Objekt mit der [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung auf die **Datensatz** Objekt. ADO ermöglicht, einschließlich Spalten mit Objektwerten **Recordset**, **SafeArray**, und Skalare Werte in der **Felder** Auflistung von **Datensatz** -Objekte.  
  
 Wenn die **Datensatz** Objekt repräsentiert eine Zeile in einer **Recordset**, es ist möglich, auf das ursprüngliche zurückgeben **Recordset** mit der [Quelle](../../../ado/reference/ado-api/source-property-ado-record.md) Diese Eigenschaft.  
  
 Die **Datensatz** Objekt kann auch verwendet werden von Anbietern für teilweise strukturierte Daten wie z. B. die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), um strukturierten Namespaces zu modellieren. Jeder Knoten in der Struktur ist eine **Datensatz** Objekt mit zugeordneten Spalten. Die Spalten können es sich um die Attribute dieses Knotens sowie weitere relevante Informationen darstellen. Die **Datensatz** Objekt kann sowohl einen Blattknoten als auch eine nicht-Blattknoten in der Struktur darstellen. Innerer Knoten als ihre Inhalte umfassen, aber Endknoten keine solche Inhalt. Blattknoten in der Regel enthalten binäre Datenströme und innerer Knoten möglicherweise auch einen binären Standarddatenstrom zugeordnet werden. Eigenschaften für die **Datensatz** Objekt identifiziert den Typ des Knotens.  
  
 Die **Datensatz** Objekt stellt auch eine alternative Möglichkeit für die Daten navigieren hierarchisch organisiert werden. Ein **Datensatz** Objekt ist möglicherweise für das Stammverzeichnis des eine bestimmte Unterstruktur in einer großen Struktur darstellen erstellt wurden und neue **Datensatz** Objekte können zur Darstellung von untergeordneten Knoten geöffnet werden.  
  
 Eine Ressource (z. B. eine Datei oder Verzeichnis) kann durch eine absolute URL eindeutig identifiziert werden. Ein [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt implizit erstellt und legen Sie auf die **Datensatz** Objekt bei der **Datensatz** mithilfe einer absoluten URLs geöffnet wird. Ein **Verbindung** Objekt kann explizit festgelegt werden, um die **Datensatz** -Objekt über die [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) Eigenschaft. Die Dateien und Verzeichnisse, die mithilfe von zugegriffen werden können die **Verbindung** Objekt definieren die *Kontext* in der **Datensatz** Vorgänge auftreten.  
  
 Daten ändern und Navigation-Methoden für die **Datensatz** -Objekt akzeptieren auch eine relative URL, die sucht eine Ressource mit der eine absolute URL oder die **Verbindung** Objektkontext als Ausgangspunkt.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Ein **Verbindung** Objekt ist für jeden **Datensatz** Objekt. Aus diesem Grund **Datensatz** Objektvorgänge können Teil einer Transaktion sein, durch den Aufruf **Verbindung** Transaktionsmethoden Objekt.  
  
 Die **Datensatz** Objekt ADO-Ereignisse wird nicht unterstützt und daher nicht auf Benachrichtigungen reagiert wird.  
  
 Mit den Methoden und Eigenschaften einer **Datensatz** -Objekts können Sie folgende Möglichkeiten:  
  
-   Festlegen oder Zurückgeben des zugeordneten **Verbindung** Objekt mit der [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) Eigenschaft.  
  
-   Angeben von Berechtigungen mit den [Modus](../../../ado/reference/ado-api/mode-property-ado.md) Eigenschaft.  
  
-   Die URL des Verzeichnisses zurück, sofern vorhanden, mit der Ressource durch dargestellt die **Datensatz** mit der [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md) Eigenschaft.  
  
-   Geben Sie die absolute URL, die relative URL oder **Recordset** aus dem der **Datensatz** abgeleitet ist, mit der [Quelle](../../../ado/reference/ado-api/source-property-ado-record.md) Eigenschaft.  
  
-   Geben Sie den aktuellen Status der **Datensatz** mit der [Zustand](../../../ado/reference/ado-api/state-property-ado.md) Eigenschaft.  
  
-   Geben Sie den Typ der **Datensatz** - *einfache*, *Auflistung*, oder *strukturiertes Dokument* – mit der [ "RecordType"](../../../ado/reference/ado-api/recordtype-property-ado.md)Eigenschaft.  
  
-   Beendet einen asynchronen Vorgang mit der [Abbrechen](../../../ado/reference/ado-api/cancel-method-ado.md) Methode.  
  
-   Aufheben der Zuordnung der **Datensatz** aus einer Datenquelle mit dem [schließen](../../../ado/reference/ado-api/close-method-ado.md) Methode.  
  
-   Kopieren Sie die Datei oder Verzeichnis dargestellt durch eine **Datensatz** an einen anderen Speicherort mit der [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) Methode.  
  
-   Löschen Sie die Datei oder das Verzeichnis und die Unterverzeichnisse, dargestellt durch eine **Datensatz** mit der [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md) Methode.  
  
-   Öffnen einer **Recordset** , enthält Zeilen, die darstellen, die Unterverzeichnisse und Dateien, der die Entität, dargestellt durch die **Datensatz** mit der [GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md) Methode.  
  
-   Verschieben (Umbenennen) der Datei oder Verzeichnis und Unterverzeichnissen, dargestellt durch eine **Datensatz** an einen anderen Speicherort mit der [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) Methode.  
  
-   Ordnen Sie die **Datensatz** mit einer vorhandenen Daten-Datenquelle aus, oder erstellen Sie eine neue Datei oder ein Verzeichnis mit der [öffnen](../../../ado/reference/ado-api/open-method-ado-record.md) Methode.  
  
 Die **Datensatz** Objekt für die Skripterstellung sicher ist.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Record-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/record-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Fields-Auflistung (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Datensätze und Datenströme](../../../ado/guide/data/records-and-streams.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
