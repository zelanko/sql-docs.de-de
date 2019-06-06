---
title: Datensätze und Felder Anbieter bereitgestellte | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- records-provided fields [ADO]
- provider-supplied fields [ADO]
ms.assetid: 77f95e0a-0cf2-411a-a792-593f77330fbd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2b7ce62ebedbd5d0622c8b69720f7153d7711a48
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700445"
---
# <a name="records-and-provider-supplied-fields"></a>Datensätze und von Anbietern bereitgestellte Felder
Wenn eine [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt geöffnet wird, kann die Quelle der aktuellen Zeile ein offenes [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), eine absolute URL oder eine relative URL in Verbindung mit einem geöffneten [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt .  
  
 Wenn die **Datensatz** geöffnet wird eine **Recordset**, **Datensatz** Objekt [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Sammlung enthält alle Felder aus der  **Recordset**, sowie alle Felder, die von den zugrunde liegenden Anbieter hinzugefügt.  
  
 Der Anbieter kann zusätzliche Felder, die als zusätzliche Merkmale des dienen Einfügen der **Datensatz**. Daher eine **Datensatz** möglicherweise eindeutige Felder nicht in der **Recordset** als Ganzes oder eines **Datensatz** abgeleitet von einer anderen Zeile der **Recordset**.  
  
 Z. B. alle Zeilen von einer **Recordset** in einer E-mail-Datenquelle verfügen über Spalten, die solche aus, um, und für die Themenbereichsdatenbank abgeleitet. Ein **Datensatz** abgeleitet, die **Recordset** müssen die gleichen Felder. Allerdings die **Datensatz** möglicherweise auch andere Felder, die nur auf eine bestimmte Nachricht durch, die dargestellt **Datensatz**, z. B. Anlage und Cc (Carbon Copy).  
  
 Obwohl die **Datensatz** -Objekt und der aktuellen Zeile die **Recordset** haben die gleichen Felder, sie unterscheiden sich da **Datensatz** und **Recordset**Objekte verfügen über verschiedene Methoden und Eigenschaften.  
  
 Ein Feld frei, die gemeinsam die **Datensatz** und **Recordset** auf eines der Objekte geändert werden kann. Allerdings kann nicht das Feld gelöscht werden, auf die **Datensatz** Objekt, auch wenn die zugrunde liegenden Anbieter unterstützt das Feld auf null festlegen.  
  
 Nach der **Datensatz** wird geöffnet, Sie können programmgesteuert Felder hinzufügen. Sie können auch Felder, die Sie hinzugefügt haben, löschen, aber Sie können keine Felder löschen, aus dem ursprünglichen **Recordset**.  
  
 Sie können auch öffnen, die **Datensatz** Objekt direkt über eine URL. In diesem Fall die Felder hinzugefügt, um die **Datensatz** hängen von den zugrunde liegenden Anbieter. Derzeit die meisten Anbieter hinzufügen einen Satz von Feldern, die beschreiben, die Entität, dargestellt durch die **Datensatz**. Wenn die Entität besteht aus einem Stream von Bytes, beispielsweise eine einfache Datei, eine [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt kann in der Regel geöffnet werden, aus der **Datensatz**.  
  
## <a name="special-fields-for-document-source-providers"></a>Spezielle Felder für Quellcode-Anbieter  
 Eine besondere Klasse von Anbietern aufgerufen *dokumentieren quellanbietern*, Ordnern und Dokumenten. Wenn eine **Datensatz** Objekt, das ein Dokument oder eine **Recordset** Objekt stellt einen Ordner von Dokumenten dar, die ein Anbieter füllt diese Objekte mit einem eindeutigen Satz von Feldern, die beschreiben, Eigenschaften des Dokuments dokumentieren Sie stattdessen den tatsächlichen selbst. In der Regel ein Feld enthält einen Verweis auf die **Stream** , das das Dokument darstellt.  
  
 Diese Felder bilden eine Ressource **Datensatz** oder **Recordset** und aufgelistet werden, für die Anbieter, die sie in unterstützen [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md).  
  
 Zwei Konstanten Index die **Felder** Auflistung einer Ressource **Datensatz** oder **Recordset** ein Paar von häufig verwendeten Feldern abrufen. Die **Feld** Objekt [Wert](../../../ado/reference/ado-api/value-property-ado.md) Eigenschaft gibt den gewünschten Inhalt zurück.  
  
-   Das Feld zugegriffen wird, mit der **AdDefaultStream** Konstante enthält einen Standarddatenstrom zugeordneten der **Datensatz** oder **Recordset** Objekt. Der Anbieter weist einen Standarddatenstrom auf ein Objekt an.  
  
-   Das Feld mit Zugriff auf die **AdRecordURL** Konstante enthält die absolute URL, die das Dokument kennzeichnet.  
  
 Ein Anbieter unterstützt nicht die [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung von **Datensatz** und **Feld** Objekte. Den Inhalt der **Eigenschaften** Auflistung ist null für solche Objekte.  
  
 Ein Anbieter kann eine anbieterspezifische Eigenschaft hinzufügen, z. B. **Datenquellentyp** ermitteln, ob es sich um ein Anbieter ist. Weitere Informationen zum Ermitteln des Anbietertyps, finden Sie in der Dokumentation Ihres Anbieters.  
  
## <a name="resource-recordset-columns"></a>Ressource Recordsetspalten  
 Ein *Ressourcenrecordset* besteht aus den folgenden Spalten.  
  
|Spaltenname|Typ|Description|  
|-----------------|----------|-----------------|  
|RESOURCE_PARSENAME|AdVarWChar|Schreibgeschützt. Gibt die URL der Ressource an.|  
|RESOURCE_PARENTNAME|AdVarWChar|Schreibgeschützt. Gibt die absolute URL des übergeordneten Datensatzes an.|  
|RESOURCE_ABSOLUTEPARSENAME|AdVarWChar|Schreibgeschützt. Gibt an, die absolute URL der Ressource, die die Verkettung von PARENTNAME und PARSENAME ist.|  
|RESOURCE_ISHIDDEN|AdBoolean|True, wenn die Ressource ausgeblendet ist. Wenn der Befehl, der das Rowset explizit erstellt Zeilen auswählt, in denen RESOURCE_ISHIDDEN "true" ist, werden keine Zeilen zurückgegeben werden.|  
|RESOURCE_ISREADONLY|AdBoolean|True, wenn die Ressource schreibgeschützt ist. Versuche zum Öffnen dieser Ressource mit DBBINDFLAG_WRITE wird fehl schlägt der Vorgang fehl. Diese Eigenschaft kann bearbeitet werden, auch wenn die Ressource nur zum Lesen geöffnet wurde.|  
|RESOURCE_CONTENTTYPE|AdVarWChar|Gibt an, die häufige Verwendung des Dokuments – z. B. ein Anwalt zu kontaktieren des kurzen. Dies kann der Office-Projektvorlage entsprechen, die zum Erstellen des Dokuments verwendet wurde.|  
|RESOURCE_CONTENTCLASS|AdVarWChar|Gibt den MIME-Typ des Dokuments, der angibt, wie z. B. auf des Formats "`text/html`".|  
|RESOURCE_CONTENTLANGUAGE|AdVarWChar|Gibt die Sprache, in der der Inhalt gespeichert ist.|  
|RESOURCE_CREATIONTIME|adFileTime|Schreibgeschützt. Gibt einen FILETIME-Struktur mit der Uhrzeit der Erstellung die Ressource an. Die Zeit wird im Format der koordinierten Weltzeit (Coordinated Universal Time, UTC) gemeldet.|  
|RESOURCE_LASTACCESSTIME|AdFileTime|Schreibgeschützt. Gibt einen FILETIME-Struktur, die die Zeit enthält, die des letzten Zugriffs auf die Ressource an. Die Zeit wird im UTC-Format. Die FILETIME-Member sind 0 (null), wenn der Anbieter diese Zeitelement nicht unterstützt.|  
|RESOURCE_LASTWRITETIME|AdFileTime|Schreibgeschützt. Gibt eine FILETIME-Struktur, die die Zeit enthält, die die Ressource zuletzt geschrieben wurde. Die Zeit wird im UTC-Format. Die FILETIME-Member sind 0 (null), wenn der Anbieter diese Zeitelement nicht unterstützt.|  
|RESOURCE_STREAMSIZE|asUnsignedBigInt|Schreibgeschützt. Gibt die Größe der Ressource standardmäßig Streams in Bytes an.|  
|RESOURCE_ISCOLLECTION|AdBoolean|Schreibgeschützt. True, wenn die Ressource eine Auflistung, z. B. ein Verzeichnis ist. "False", wenn die Ressource eine einfache Datei ist.|  
|RESOURCE_ISSTRUCTUREDDOCUMENT|AdBoolean|True, wenn die Ressource ein strukturiertes Dokument ist. False, wenn die Ressource nicht mit einem strukturierten Dokument ist. Es kann es sich um eine Sammlung oder eine einfache Datei handeln.|  
|DEFAULT_DOCUMENT|AdVarWChar|Schreibgeschützt. Gibt an, dass diese Ressource eine URL für das einfache Standarddokument eines Ordners oder eines strukturierten Dokuments enthält. Verwendet, wenn es sich bei der Standarddatenstrom aus einer Ressource angefordert wird. Diese Eigenschaft ist leer, um eine einfache Datei.|  
|CHAPTERED_CHILDREN|AdChapter|Schreibgeschützt. Optional. Gibt an, im Kapitel über das Rowset, das die untergeordneten Elemente der Ressource enthält. (Die *OLE DB-Anbieter für Internet Publishing* diese Spalte nicht verwendet.)|  
|RESOURCE_DISPLAYNAME|AdVarWChar|Schreibgeschützt. Gibt den Anzeigenamen der Ressource an.|  
|RESOURCE_ISROOT|AdBoolean|Schreibgeschützt. True, wenn die Ressource der Stamm einer Sammlung oder eine strukturierte Dokument ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Record Object (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
