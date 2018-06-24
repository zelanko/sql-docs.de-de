---
title: Volltextindex-Eigenschaften (Seite Allgemein) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.general.f1
ms.assetid: f4dff61c-8c2f-4ff9-abe4-70a34421448f
caps.latest.revision: 27
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 67fd5637e190d58cdcab186643d5233bb89b1b5e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050658"
---
# <a name="full-text-index-properties-general-page"></a>Volltextindex-Eigenschaften (Seite 'Allgemein')
  **Zum Anzeigen oder ändern die veränderbaren Eigenschaften eines Volltextindex-**  
  
-   [Verwalten von Volltextindizes](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Volltextkatalog**  
 Zeigt den Namen des Volltextkatalogs an, dem dieser Volltextindex zugeordnet wird.  
  
 **Datenbank**  
 Zeigt den Namen der Datenbank an, in der sich der Volltextindex befindet.  
  
 **Tabelle**  
 Zeigt den Namen der Tabelle an, für die der Volltextindex definiert wurde.  
  
 **Volltext-Indexschlüssel**  
 Zeigt den Namen des Volltext-Indexschlüssels an, der einen eindeutigen Index für eine einzelne Spalte der Tabelle darstellt.  
  
 **Tabelle Volltext-Auffüllstatus**  
 Zeigt den Auffüllungsstatus der volltextindizierten Tabelle an.  
  
 Die folgenden Werte sind möglich:  
  
 0 = Im Leerlauf.  
  
 1 = Vollständige Auffüllung wird ausgeführt.  
  
 2 = Inkrementelle Auffüllung wird ausgeführt.  
  
 3 = Propagierung der Überarbeitungen wird ausgeführt.  
  
 4 = Indexupdate wird im Hintergrund ausgeführt, z. B. automatische Änderungsnachverfolgung.  
  
 5 = Volltextindizierung wurde gedrosselt oder angehalten.  
  
 **Aktiven Volltextindex**  
 Gibt an, ob die Tabelle über einen aktiven Volltextindex verfügt.  
  
 1 = True  
  
 0 = False  
  
 **Volltextindex-Dateigruppe**  
 Die Dateigruppe, zu der der Volltextindex gehört.  
  
 **Volltextindex-Stoppliste**  
 Die Stoppliste, die gegenwärtig dem Volltextindex zugeordnet ist. Eine Stoppliste ist eine Liste der [Stoppwörter](../relational-databases/search/full-text-search.md). Die ggf. einem Volltextindex zugeordnete Stoppliste wird auf Volltextabfragen für diesen Index angewendet. Sie können die Stoppliste aus dem Index entfernen, dazu  **\<OFF >** aus der Liste aus, oder Sie können eine andere Stoppliste; auswählen  **\<SYSTEM >** gibt die Systemstoppliste an.  
  
 **So erstellen Sie eine Stoppliste**  
  
-   [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../relational-databases/search/full-text-search.md)  
  
 **Sucheigenschaftenliste**  
 Die Sucheigenschaftenliste, die ggf. derzeit dem Volltextindex zugeordnet ist. Eine Sucheigenschaftenliste gibt einen Satz von Dokumenteigenschaften an, die im zugeordneten Volltextindex enthalten sind, wenn dieser aufgefüllt ist. Weitere Informationen finden Sie unter [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 **\<Off >** gibt an, dass derzeit keine sucheigenschaftenliste dem Index zugeordnet. Sie können die aktuelle sucheigenschaftenliste aus dem Index entfernen, indem Sie auswählen  **\<deaktiviert >** aus der Liste aus, oder Sie können eine andere sucheigenschaftenliste auswählen, aus der Liste. An dieser Stelle werden nur Sucheigenschaftenlisten in der aktuellen Datenbank aufgeführt.  
  
> [!NOTE]  
>  Sie können eine Sucheigenschaftenliste mehr als einem Volltextindex in der gleichen Datenbank zuordnen.  
  
 **So erstellen eine sucheigenschaftenliste**  
  
-   [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
 **Tabelle Volltext-Elementanzahl**  
 Gibt die Anzahl der Zeilen an, die erfolgreich volltextindiziert wurden.  
  
 Diese Eigenschaft entspricht der `TableFulltextItemCount` von der OBJECTPROPERTYEX zurückgegebene Eigenschaft [!INCLUDE[tsql](../includes/tsql-md.md)] Funktion.  
  
 **Tabelle Volltextdokumente verarbeitet**  
 Zeigt die Anzahl der seit dem Start der Volltextindizierung verarbeiteten Zeilen an. In einer Tabelle, die für die Volltextsuche indiziert wird, werden alle Spalten einer Zeile als Teil eines zu indizierenden Dokuments betrachtet. Gelöschte Zeilen werden nicht gezählt.  
  
|||  
|-|-|  
|0|Gibt an, dass die Volltextindizierung abgeschlossen ist und keine aktive Auffüllung ausgeführt wird.|  
|> 0|Gibt bei einer aktiven Auffüllung die Anzahl der Dokumente an, die seit einer der folgenden Aktionen mithilfe von Einfüge- und Updatevorgängen verarbeitet wurden: Auffüllung, Aktivieren der Änderungsnachverfolgung mit Indexupdate im Hintergrund (z. B. automatische Änderungsnachverfolgung), Änderung des Schemas für den Volltextindex, Neuerstellung des Volltextkatalogs, Neustart de Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], usw.|  
  
 **Tabelle Volltext-ausstehende Änderungen**  
 Anzahl der zu verarbeitenden ausstehenden Änderungsnachverfolgungseinträge.  
  
 0 = Änderungsnachverfolgung ist nicht aktiviert.  
  
 NULL = Die Tabelle besitzt keinen Volltextindex.  
  
 **Tabelle Volltext-Fehlerzahl**  
 Die Anzahl der Zeilen, die von der Volltextsuche nicht indiziert wurden.  
  
 0 = Die Auffüllung ist abgeschlossen.  
  
 \>0 = eine der folgenden:  
  
-   Die Anzahl der Dokumente, die seit dem Start der Auffüllung mithilfe der vollständigen, inkrementellen und manuellen Änderungsnachverfolgung nicht indiziert wurden.  
  
-   Bei der Änderungsnachverfolgung mit Indexupdate im Hintergrund die Anzahl der Zeilen, die seit dem Start der Auffüllung oder dem Neustart der Auffüllung nicht indiziert wurden. Dies könnte durch eine Schemaänderung, eine erneute Erstellung des Katalogs, einen Neustart des Servers usw. verursacht werden.  
  
 **Volltextindizierung aktiviert**  
 Gibt an, ob die Volltextindizierung aktiviert ist.  
  
|||  
|-|-|  
|**Wahr**|Aktiviert|  
|**False**|Disabled|  
  
 **Änderungsnachverfolgung**  
 Gibt an, ob die Volltext-Änderungsnachverfolgung für die Tabelle aktiviert ist, und wenn dies der Fall ist, deren Typ. Bei der Volltext-Änderungsnachverfolgung werden die Zeilen aufgezeichnet, die in einer Tabelle oder indizierten Sicht geändert wurden, die für die Volltextindizierung eingerichtet wurde. Diese Änderungen können an den Volltextindex weitergegeben werden.  
  
 Folgende Werte für **Änderungsnachverfolgung** sind möglich:  
  
|||  
|-|-|  
|**Ausschalten**|Der Volltextindex wird nicht mit Änderungen an den zugrunde liegenden Daten aktualisiert.|  
|**Manuell**|Der Volltextindex wird bei Änderungen zu den zugrunde liegenden Daten nicht automatisch aktualisiert. Änderungen an den zugrunde liegenden Daten werden jedoch beibehalten, und Sie können sie an den Volltextindex weitergeben, entweder nach einem Zeitplan unter Verwendung des SQL-Server-Agents oder manuell.|  
|**Automatic**|Der Volltextindex wird bei Änderungen zu den zugrunde liegenden Daten in der Basistabelle automatisch aktualisiert.|  
  
 **Index neu auffüllen**  
 Klicken Sie, um beim Beenden des Dialogfelds die Auffüllung des Volltextindexes zu starten. Wählen Sie einen der folgenden Auffüllungstypen aus:  
  
|||  
|-|-|  
|**Full**|Während einer vollständigen Auffüllung einer Tabelle werden Indexeinträge für alle Zeilen erstellt.|  
|**Inkrementelle**|Bei der inkrementellen Auffüllung wird der Volltextindex bezüglich der Zeilen aktualisiert, die seit der letzten Auffüllung oder während des letzten Auffüllungsvorgangs hinzugefügt, gelöscht oder geändert wurden. Eine inkrementelle Auffüllung ist erforderlich, dass die Basistabelle enthält eine Spalte mit dem `timestamp` -Datentyp.|  
|**Update**|Der Volltextindex wird stets aktualisiert, wenn die Daten in der Basistabelle geändert werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte mit der Volltextsuche](../relational-databases/search/get-started-with-full-text-search.md)  
  
  