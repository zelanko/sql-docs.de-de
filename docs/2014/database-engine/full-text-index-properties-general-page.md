---
title: Voll Text Index-Eigenschaften (Seite "Allgemein") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.general.f1
ms.assetid: f4dff61c-8c2f-4ff9-abe4-70a34421448f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1701479fe7469769d75f4b8ad3d8e65dcc75af91
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2020
ms.locfileid: "83858672"
---
# <a name="full-text-index-properties-general-page"></a>Volltextindex-Eigenschaften (Seite 'Allgemein')
  **So zeigen Sie die veränderbaren Eigenschaften eines Volltextindexes an oder ändern Sie diese**  
  
-   [Verwalten von Volltextindizes](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
 **Voll Text Katalog**  
 Zeigt den Namen des Volltextkatalogs an, dem dieser Volltextindex zugeordnet wird.  
  
 **Datenbank**  
 Zeigt den Namen der Datenbank an, in der sich der Volltextindex befindet.  
  
 **Tabelle**  
 Zeigt den Namen der Tabelle an, für die der Volltextindex definiert wurde.  
  
 **Volltext-Indexschlüssel**  
 Zeigt den Namen des Volltext-Indexschlüssels an, der einen eindeutigen Index für eine einzelne Spalte der Tabelle darstellt.  
  
 **Volltext-Auffüllstatus-Tabelle**  
 Zeigt den Auffüllungsstatus der volltextindizierten Tabelle an.  
  
 Die folgenden Werte sind möglich:  
  
 0 = Im Leerlauf.  
  
 1 = Vollständige Auffüllung wird ausgeführt.  
  
 2 = Inkrementelle Auffüllung wird ausgeführt.  
  
 3 = Propagierung der Überarbeitungen wird ausgeführt.  
  
 4 = Indexupdate wird im Hintergrund ausgeführt, z. B. automatische Änderungsnachverfolgung.  
  
 5 = Volltextindizierung wurde gedrosselt oder angehalten.  
  
 **Aktiver Volltextindex**  
 Gibt an, ob die Tabelle über einen aktiven Volltextindex verfügt.  
  
 1 = True  
  
 0 = False  
  
 **Volltextindex-Dateigruppe**  
 Die Dateigruppe, zu der der Volltextindex gehört.  
  
 **Volltextindex-Stoppliste**  
 Die Stoppliste, die gegenwärtig dem Volltextindex zugeordnet ist. Eine Stoppliste ist eine Liste von [Stoppwörtern](../relational-databases/search/full-text-search.md). Die ggf. einem Volltextindex zugeordnete Stoppliste wird auf Volltextabfragen für diesen Index angewendet. Sie können die Stopp Liste aus dem Index entfernen, indem Sie ** \<>** aus der Liste auswählen, oder Sie können eine andere Stopp Liste auswählen. ** \< System>** gibt die System Stopp Liste an.  
  
 **So erstellen Sie eine Stoppliste**  
  
-   [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../relational-databases/search/full-text-search.md)  
  
 **Sucheigenschaftenliste**  
 Die Sucheigenschaftenliste, die ggf. derzeit dem Volltextindex zugeordnet ist. Eine Sucheigenschaftenliste gibt einen Satz von Dokumenteigenschaften an, die im zugeordneten Volltextindex enthalten sind, wenn dieser aufgefüllt ist. Weitere Informationen finden Sie unter [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 ** \< Off>** gibt an, dass dem Index derzeit keine Such Eigenschaften Liste zugeordnet ist. Sie können die aktuelle Such Eigenschaften Liste aus dem Index entfernen, indem Sie ** \<>** aus der Liste auswählen, oder Sie können in der Liste eine andere Such Eigenschaften Liste auswählen. An dieser Stelle werden nur Sucheigenschaftenlisten in der aktuellen Datenbank aufgeführt.  
  
> [!NOTE]  
>  Sie können eine Sucheigenschaftenliste mehr als einem Volltextindex in der gleichen Datenbank zuordnen.  
  
 **So erstellen Sie eine Sucheigenschaftenliste**  
  
-   [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
 **Volltext-Elementanzahl-Tabelle**  
 Gibt die Anzahl der Zeilen an, die erfolgreich volltextindiziert wurden.  
  
 Diese Eigenschaft entspricht der von der OBJECTPROPERTYEX-Funktion von [!INCLUDE[tsql](../includes/tsql-md.md)] zurückgegebenen `TableFulltextItemCount`-Eigenschaft.  
  
 **Tabelle für verarbeitete Volltextdokumente**  
 Zeigt die Anzahl der seit dem Start der Volltextindizierung verarbeiteten Zeilen an. In einer Tabelle, die für die Volltextsuche indiziert wird, werden alle Spalten einer Zeile als Teil eines zu indizierenden Dokuments betrachtet. Gelöschte Zeilen werden nicht gezählt.  
  
|||  
|-|-|  
|0|Gibt an, dass die Volltextindizierung abgeschlossen ist und keine aktive Auffüllung ausgeführt wird.|  
|> 0|Gibt bei einer aktiven Auffüllung die Anzahl der Dokumente an, die seit einer der folgenden Aktionen mithilfe von Einfüge- und Updatevorgängen verarbeitet wurden: Auffüllung, Aktivieren der Änderungsnachverfolgung mit Indexupdate im Hintergrund (z. B. automatische Änderungsnachverfolgung), Änderung des Schemas für den Volltextindex, Neuerstellung des Volltextkatalogs, Neustart de Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], usw.|  
  
 **Tabelle für ausstehende Volltextänderungen**  
 Anzahl der zu verarbeitenden ausstehenden Änderungsnachverfolgungseinträge.  
  
 0 = Änderungsnachverfolgung ist nicht aktiviert.  
  
 NULL = Die Tabelle besitzt keinen Volltextindex.  
  
 **Volltext-Fehlerzahl-Tabelle**  
 Die Anzahl der Zeilen, die von der Volltextsuche nicht indiziert wurden.  
  
 0 = Die Auffüllung ist abgeschlossen.  
  
 \>0 = eine der folgenden:  
  
-   Die Anzahl der Dokumente, die seit dem Start der Auffüllung mithilfe der vollständigen, inkrementellen und manuellen Änderungsnachverfolgung nicht indiziert wurden.  
  
-   Bei der Änderungsnachverfolgung mit Indexupdate im Hintergrund die Anzahl der Zeilen, die seit dem Start der Auffüllung oder dem Neustart der Auffüllung nicht indiziert wurden. Dies könnte durch eine Schemaänderung, eine erneute Erstellung des Katalogs, einen Neustart des Servers usw. verursacht werden.  
  
 **Volltextindizierung aktiviert**  
 Gibt an, ob die Volltextindizierung aktiviert ist.  
  
|||  
|-|-|  
|**Fall**|Aktiviert|  
|**Alarm**|Disabled|  
  
 **Änderungsnachverfolgung**  
 Gibt an, ob die Volltext-Änderungsnachverfolgung für die Tabelle aktiviert ist, und wenn dies der Fall ist, deren Typ. Bei der Volltext-Änderungsnachverfolgung werden die Zeilen aufgezeichnet, die in einer Tabelle oder indizierten Sicht geändert wurden, die für die Volltextindizierung eingerichtet wurde. Diese Änderungen können an den Volltextindex weitergegeben werden.  
  
 Folgende Werte für **Änderungsnachverfolgung** sind möglich:  
  
|||  
|-|-|  
|**Aus**|Der Volltextindex wird nicht mit Änderungen an den zugrunde liegenden Daten aktualisiert.|  
|**Manuell**|Der Volltextindex wird bei Änderungen zu den zugrunde liegenden Daten nicht automatisch aktualisiert. Änderungen an den zugrunde liegenden Daten werden jedoch beibehalten, und Sie können sie an den Volltextindex weitergeben, entweder nach einem Zeitplan unter Verwendung des SQL-Server-Agents oder manuell.|  
|**Automatisch**|Der Volltextindex wird bei Änderungen zu den zugrunde liegenden Daten in der Basistabelle automatisch aktualisiert.|  
  
 **Index neu auffüllen**  
 Klicken Sie, um beim Beenden des Dialogfelds die Auffüllung des Volltextindexes zu starten. Wählen Sie einen der folgenden Auffüllungstypen aus:  
  
|||  
|-|-|  
|**Vollständig**|Während einer vollständigen Auffüllung einer Tabelle werden Indexeinträge für alle Zeilen erstellt.|  
|**Inkrementell**|Bei der inkrementellen Auffüllung wird der Volltextindex bezüglich der Zeilen aktualisiert, die seit der letzten Auffüllung oder während des letzten Auffüllungsvorgangs hinzugefügt, gelöscht oder geändert wurden. Für eine inkrementelle Auffüllung muss die Basistabelle eine Spalte des Datentyps `timestamp` enthalten.|  
|**Aktualisieren**|Der Volltextindex wird stets aktualisiert, wenn die Daten in der Basistabelle geändert werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erste Schritte mit der Volltextsuche](../relational-databases/search/get-started-with-full-text-search.md)  
  
  
