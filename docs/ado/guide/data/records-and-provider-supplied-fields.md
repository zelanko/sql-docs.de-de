---
description: Datensätze und von Anbietern bereitgestellte Felder
title: Datensätze und vom Anbieter bereitgestellte Felder | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- records-provided fields [ADO]
- provider-supplied fields [ADO]
ms.assetid: 77f95e0a-0cf2-411a-a792-593f77330fbd
author: rothja
ms.author: jroth
ms.openlocfilehash: 7cc7b8c4fb0116f96a2470a7161f9fbd30c7efb9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979951"
---
# <a name="records-and-provider-supplied-fields"></a>Datensätze und von Anbietern bereitgestellte Felder
Wenn ein [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekt geöffnet wird, kann seine Quelle die aktuelle Zeile eines geöffneten [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md), eine absolute URL oder eine relative URL in Verbindung mit einem geöffneten [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt sein.  
  
 Wenn der **Datensatz** von einem **Recordset**aus geöffnet wird, enthält die Auflistung der **Datensatz** -Objekt [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) alle Felder aus dem **Recordset**sowie alle Felder, die vom zugrunde liegenden Anbieter hinzugefügt werden.  
  
 Der Anbieter kann zusätzliche Felder einfügen, die als ergänzende Merkmale des **Datensatzes**fungieren. Folglich kann ein **Datensatz** eindeutige Felder enthalten, die sich nicht im **Recordset** als Ganzes befinden, oder einen **Datensatz** , der aus einer anderen Zeile des **Recordsets**abgeleitet ist.  
  
 Beispielsweise können alle Zeilen eines **Recordsets** , die aus einer e-Mail-Datenquelle abgeleitet sind, Spalten wie z. b. from, to und Subject enthalten. Ein **Datensatz** , der von diesem **Recordset** abgeleitet wird, hat dieselben Felder. Der **Datensatz** kann jedoch auch andere Felder aufweisen, die für die von diesem **Datensatz**dargestellte Nachricht eindeutig sind, wie z. b. Anhang und CC (Kohlendioxid Kopie).  
  
 Obwohl das **Datensatz** -Objekt und die aktuelle Zeile des **Recordsets** die gleichen Felder aufweisen, unterscheiden Sie sich, weil **Datensatz** -und **Recordset** -Objekte über unterschiedliche Methoden und Eigenschaften verfügen.  
  
 Ein Feld, das vom **Datensatz** und **Recordset** gemeinsam gehalten wird, kann für jedes Objekt geändert werden. Allerdings kann das Feld für das **Daten Satz** Objekt nicht gelöscht werden, obwohl der zugrunde liegende Anbieter das Festlegen des Felds auf NULL unterstützen kann.  
  
 Nachdem der **Datensatz** geöffnet wurde, können Sie Felder Programm gesteuert hinzufügen. Sie können auch Felder löschen, die Sie hinzugefügt haben, aber Sie können keine Felder aus dem ursprünglichen **Recordset**löschen.  
  
 Sie können das **Datensatz** -Objekt auch direkt über eine URL öffnen. In diesem Fall hängen die dem **Datensatz** hinzugefügten Felder vom zugrunde liegenden Anbieter ab. Derzeit fügen die meisten Anbieter einen Satz von Feldern hinzu, die die durch den **Datensatz**dargestellte Entität beschreiben. Wenn die Entität aus einem Bytestream besteht (z. b. einer einfachen Datei), kann normalerweise ein [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) aus dem **Datensatz**geöffnet werden.  
  
## <a name="special-fields-for-document-source-providers"></a>Besondere Felder für Dokument Quellen Anbieter  
 Eine spezielle Klasse von Anbietern, die als *Dokument Quellen Anbieter*bezeichnet werden, verwaltet Ordner und Dokumente. Wenn ein **Datensatz** -Objekt ein Dokument darstellt oder ein **Recordset** -Objekt einen Ordner mit Dokumenten darstellt, füllt der Dokument Quellen Anbieter diese Objekte mit einem eindeutigen Satz von Feldern auf, die die Merkmale des Dokuments anstelle des eigentlichen Dokuments selbst beschreiben. In der Regel enthält ein Feld einen Verweis auf den **Stream** , der das Dokument darstellt.  
  
 Diese Felder bilden einen Ressourcen **Daten Satz** oder ein **Recordset** und werden für die jeweiligen Anbieter aufgelistet, die Sie in [Anhang a: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)unterstützen.  
  
 Zwei Konstanten indizieren die **Fields** -Auflistung eines Ressourcen **Datensatzes** oder eines **Recordsets** zum Abrufen eines Paares häufig verwendeter Felder. Die Eigenschaft **Feld** Objekt [Wert](../../../ado/reference/ado-api/value-property-ado.md) gibt den gewünschten Inhalt zurück.  
  
-   Das Feld, auf das mit der **adDefaultStream** -Konstante zugegriffen wird, enthält einen dem **Datensatz** -oder **Recordset** -Objekt zugeordneten Standardstream. Der Anbieter weist einem Objekt einen Standarddaten Strom zu.  
  
-   Das Feld, auf das mit der **adRecordURL** -Konstante zugegriffen wird, enthält die absolute URL, die das Dokument identifiziert.  
  
 Ein Dokument Quellen Anbieter unterstützt die [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Sammlung von **Datensatz** -und **Feld** -Objekten nicht. Der Inhalt der **Properties** -Auflistung ist für solche Objekte NULL.  
  
 Ein Dokument Quellen Anbieter kann eine anbieterspezifische Eigenschaft wie den **DataSource-Typ** hinzufügen, um zu ermitteln, ob es sich um einen Dokument Quellen Anbieter handelt. Weitere Informationen zum Bestimmen des Anbieter Typs finden Sie in der Dokumentation Ihres Anbieters.  
  
## <a name="resource-recordset-columns"></a>Ressourcen-Recordsetspalten  
 Ein *Ressourcen-Recordset* besteht aus den folgenden Spalten.  
  
|Spaltenname|Typ|Beschreibung|  
|-----------------|----------|-----------------|  
|RESOURCE_PARSENAME|AdVarWchar|Schreibgeschützt. Gibt die URL der Ressource an.|  
|RESOURCE_PARENTNAME|AdVarWchar|Schreibgeschützt. Gibt die absolute URL des übergeordneten Datensatzes an.|  
|RESOURCE_ABSOLUTEPARSENAME|AdVarWchar|Schreibgeschützt. Gibt den absolute URL der Ressource an. Hierbei handelt es sich um die Verkettung von "Elementname" und "paramesename".|  
|RESOURCE_ISHIDDEN|Adboolean|True, wenn die Ressource ausgeblendet ist. Es werden keine Zeilen zurückgegeben, es sei denn, der Befehl, der das Rowset erstellt, wählt explizit Zeilen aus, in denen RESOURCE_ISHIDDEN true|  
|RESOURCE_ISREADONLY|Adboolean|True, wenn die Ressource schreibgeschützt ist. Versucht, diese Ressource mit DBBINDFLAG_WRITE zu öffnen, und schlägt mit DB_E_READONLY fehl. Diese Eigenschaft kann auch dann bearbeitet werden, wenn die Ressource nur zum Lesen geöffnet wurde.|  
|RESOURCE_CONTENTTYPE|AdVarWchar|Gibt die wahrscheinliche Verwendung des Dokuments an, z. b. den Brief eines Anwalts. Dies entspricht möglicherweise der Office-Vorlage, die zum Erstellen des Dokuments verwendet wurde.|  
|RESOURCE_CONTENTCLASS|AdVarWchar|Gibt den MIME-Typ des Dokuments an, das das Format (z `text/html` . b. "") angibt.|  
|RESOURCE_CONTENTLANGUAGE|AdVarWchar|Gibt die Sprache an, in der der Inhalt gespeichert wird.|  
|RESOURCE_CREATIONTIME|adFileTime|Schreibgeschützt. Gibt eine FILETIME-Struktur an, die den Zeitpunkt enthält, zu dem die Ressource erstellt wurde. Die Zeit wird im UTC-Format (koordinierte Weltzeit) gemeldet.|  
|RESOURCE_LASTACCESSTIME|Adfiletime|Schreibgeschützt. Gibt eine FILETIME-Struktur an, die die Uhrzeit des letzten Zugriffs auf die Ressource enthält. Die Uhrzeit liegt im UTC-Format vor. Die FILETIME-Member sind 0 (null), wenn der Anbieter dieses Zeitelement nicht unterstützt.|  
|RESOURCE_LASTWRITETIME|Adfiletime|Schreibgeschützt. Gibt eine FILETIME-Struktur an, die die Uhrzeit enthält, zu der die Ressource zuletzt geschrieben wurde. Die Uhrzeit liegt im UTC-Format vor. Die FILETIME-Member sind 0 (null), wenn der Anbieter dieses Zeitelement nicht unterstützt.|  
|RESOURCE_STREAMSIZE|asunsignedbigint|Schreibgeschützt. Gibt die Größe des Standarddaten Stroms der Ressource in Bytes an.|  
|RESOURCE_ISCOLLECTION|Adboolean|Schreibgeschützt. True, wenn die Ressource eine Auflistung ist, z. b. ein Verzeichnis. False, wenn die Ressource eine einfache Datei ist.|  
|RESOURCE_ISSTRUCTUREDDOCUMENT|Adboolean|True, wenn die Ressource ein strukturiertes Dokument ist. False, wenn die Ressource kein strukturiertes Dokument ist. Dabei kann es sich um eine Sammlung oder eine einfache Datei handeln.|  
|DEFAULT_DOCUMENT|AdVarWchar|Schreibgeschützt. Gibt an, dass diese Ressource eine URL zum standardmäßigen einfachen Dokument eines Ordners oder eines strukturierten Dokuments enthält. Wird verwendet, wenn der Standarddaten Strom von einer Ressource angefordert wird. Diese Eigenschaft ist für eine einfache Datei leer.|  
|CHAPTERED_CHILDREN|AdChapter|Schreibgeschützt. Optional. Gibt das Kapitel des Rowsets an, das die untergeordneten Elemente der Ressource enthält. (Der *OLE DB Anbieter für die Internet Veröffentlichung* verwendet diese Spalte nicht.)|  
|RESOURCE_DISPLAYNAME|AdVarWchar|Schreibgeschützt. Gibt den anzeigen amen der Ressource an.|  
|RESOURCE_ISROOT|Adboolean|Schreibgeschützt. True, wenn die Ressource der Stamm einer Sammlung oder eines strukturierten Dokuments ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
