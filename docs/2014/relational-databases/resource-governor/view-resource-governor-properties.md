---
title: Anzeigen der Eigenschaften der Ressourcenkontrolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties.f1
helpviewer_keywords:
- Resource Governor, properties
ms.assetid: de3510df-f792-4a9d-80fa-f198fd36cdc8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 35d4720a8fe8b8c1b404a97e27b36896f36dd5f7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63209686"
---
# <a name="view-resource-governor-properties"></a>Anzeigen der Eigenschaften der Ressourcenkontrolle
  Auf der Seite Eigenschaften der Ressourcenkontrolle in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]können Sie Ressourcenkontrollentitäten erstellen oder konfigurieren, z. B. Ressourcenpools und Arbeitsauslastungsgruppen.  
  
1.  **Vorbereitungen:**  [Berechtigungen](#Permissions)  
  
2.  **Eigenschaften der Ressourcenkontrolle anzeigen mit:**  [Seite „Eigenschaften der Ressourcenkontrolle“](#ViewRGProp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
 Neben dem Anzeigen der Eigenschaften von Ressourcenkontrollentitäten können Sie auf der Seite **Eigenschaften der Ressourcenkontrolle** mehrere Konfigurationstasks ausführen. Weitere Informationen finden Sie in den folgenden Themen:  
  
-   [Aktivieren der Ressourcenkontrolle](enable-resource-governor.md)  
  
-   [Deaktivieren der Ressourcenkontrolle](disable-resource-governor.md)  
  
-   [Erstellen eines Ressourcenpools](create-a-resource-pool.md)  
  
-   [Erstellen einer Arbeits Auslastungs Gruppe](create-a-workload-group.md)  
  
-   [Ändern der Einstellungen für den Ressourcenpool](change-resource-pool-settings.md)  
  
-   [Ändern der Einstellungen von Arbeitsauslastungsgruppen](change-workload-group-settings.md)  
  
-   [Verschieben von Arbeitsauslastungsgruppen](move-a-workload-group.md)  
  
 Nachdem Sie eine Arbeitsauslastungsgruppe oder einen Ressourcenpool hinzugefügt, gelöscht oder verschoben haben, wird die Anweisung ALTER RESOURCE GOVERNOR RECONFIGURE ausgeführt, wenn Sie auf **OK** klicken.  
  
 Bei einem Fehler beim Erstellungs- oder Neukonfigurierungsvorgang für den Ressourcenpool oder die Arbeitsauslastungsgruppe wird unter dem Titel der Eigenschaftenseite eine zusammenfassende Fehlermeldung angezeigt. Klicken Sie auf den Abwärtspfeil an der Fehlermeldung, um eine ausführliche Fehlermeldung anzuzeigen.  
  
 Sie können feststellen, ob eine ausstehende Konfiguration vorliegt, indem Sie die dynamische Verwaltungssicht [sys.dm_resource_governor_configuration](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) abfragen, um den aktuellen Status von is_configuration_pending zu erhalten.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Zum Anzeigen der Ressourcenkontrolleigenschaften ist die VIEW SERVER STATER-Berechtigung erforderlich. Für die Konfigurationstasks für die Ressourcenkontrolle ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="view-the-resource-governor-properties-page"></a><a name="ViewRGProp"></a>Anzeigen der Resource Governor Eigenschaften Seite  
 **So zeigen Sie die Eigenschaften der Ressourcenkontrolle auf der Seite Eigenschaften von Resource Governor in[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer, und erweitern Sie den Knoten **Verwaltung** rekursiv, bis **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Resource Governor** , und klicken Sie dann auf **Eigenschaften**. Damit öffnen Sie die Seite **Eigenschaften des Resource Governors** .  
  
3.  Beschreibungen der Felder auf der Seite finden Sie unter [Eigenschaften der Ressourcenkontrolle](#RGProp).  
  
4.  Klicken Sie auf **OK**, um Änderungen zu speichern.  
  
##  <a name="resource-governor-properties"></a><a name="RGProp"></a>Eigenschaften von Resource Governor  
 **Der Name der Klassifizierungsfunktion**  
 Geben Sie die Klassifizierungsfunktion durch Auswahl aus der Liste an.  
  
 **Aktivieren der Ressourcenkontrolle**  
 Aktivieren oder deaktivieren Sie die Ressourcenkontrolle, indem Sie das Kontrollkästchen aktivieren oder deaktivieren.  
  
 **Ressourcenpools**  
 Erstellen oder ändern Sie die Konfiguration von Ressourcenpools mithilfe des vorhandenen Rasters. Dieses Raster wird mit Informationen für die vordefinierten internen Pools und Standardpools ausgefüllt. Wählen Sie einen Pool aus, mit dem Sie arbeiten möchten, indem Sie auf die erste Spalte in der Zeile für den Pool klicken. Klicken Sie zur Erstellung eines neuen Ressourcenpools auf die Zeile, der ein Sternchen (**&#42;**) vorangestellt ist.  
  
 **Name**  
 Geben Sie den Namen des Ressourcenpools an.  
  
 **Minimaler CPU-Prozentsatz**  
 Geben Sie die garantierte durchschnittliche CPU-Bandbreite für alle Anforderungen im Ressourcenpool an, wenn CPU-Konflikte bestehen. Der Bereich liegt zwischen 0 und 100.  
  
 **Maximaler CPU-Prozentsatz**  
 Geben Sie die maximale durchschnittliche CPU-Bandbreite an, die allen Anforderungen im Ressourcenpool zugewiesen wird, wenn CPU-Konflikte bestehen. Der Bereich liegt zwischen 0 und 100. Die Standardeinstellung ist 100.  
  
 **Minimaler Arbeitsspeicherprozentsatz**  
 Geben Sie den Mindestarbeitsspeicher an, der für diesen Ressourcenpool reserviert ist und nicht gemeinsam mit anderen Ressourcenpools verwendet werden kann. Der Bereich liegt zwischen 0 und 100.  
  
 **Maximaler Arbeitsspeicherprozentsatz**  
 Geben Sie den gesamten Serverspeicher an, der für Anforderungen in diesem Ressourcenpool verwendet werden kann. Der Bereich liegt zwischen 0 und 100. Die Standardeinstellung ist 100.  
  
 Weitere Informationen finden Sie unter [Erstellen eines Ressourcenpools &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql).  
  
 **Arbeitsauslastungsgruppen für Ressourcenpool**  
 Erstellen oder ändern Sie die Konfiguration von Arbeitsauslastungsgruppen mithilfe des vorhandenen Rasters. Dieses Raster wird mit Informationen für die vordefinierten internen Gruppen und Standardgruppen ausgefüllt. Wählen Sie eine Gruppe aus, mit der Sie arbeiten möchten, indem Sie auf die erste Spalte in der Zeile für den Pool klicken. Klicken Sie zur Erstellung einer neuen Arbeitsauslastungsgruppe auf die Zeile, der ein Sternchen (**&#42;**) vorangestellt ist.  
  
 **Name**  
 Geben Sie den Namen der Arbeitsauslastungsgruppe an.  
  
 **Wichtigkeit**  
 Geben Sie die relative Wichtigkeit einer Anforderung in der Arbeitsauslastungsgruppe an. Die verfügbaren Einstellungen lauten Niedrig, Mittel und Hoch.  
  
 **Maximale Anforderungen**  
 Geben Sie die maximale Anzahl gleichzeitiger Anforderungen an, die in der Arbeitsauslastungsgruppe ausgeführt werden können. Dieser Wert muss 0 (null) oder eine positive Ganzzahl sein.  
  
 **CPU-Zeit (Sek.)**  
 Geben Sie die maximale CPU-Zeit für eine Anforderung an. Dieser Wert muss 0 (null) oder eine positive Ganzzahl sein. Bei 0 ist die Zeit unbegrenzt.  
  
 **Arbeitsspeicherzuweisung (%)**  
 Geben Sie die Höchstmenge an Arbeitsspeicher an, die eine einzelne Anforderung vom Pool in Anspruch nehmen kann. Der Bereich liegt zwischen 0 und 100.  
  
 **Timeout für Arbeitsspeicherzuweisung (Sek)**  
 Geben Sie die maximale Zeit in Sekunden an, die eine Abfrage auf das Freiwerden einer Ressource wartet, bevor die Abfrage fehlschlägt. Dieser Wert muss 0 (null) oder eine positive Ganzzahl sein.  
  
 **Grad der Parallelität**  
 Geben Sie den maximalen Grad der Parallelität (DOP) für parallele Anforderungen an. Der Bereich liegt zwischen 0 und 64.  
  
 Weitere Informationen finden Sie unter [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql).  
  
## <a name="view-resource-governor-properties-by-using-transact-sql"></a>Anzeigen von Eigenschaften der Ressourcenkontrolle mit Transact-SQL  
 **Anzeigen von Eigenschaften der Ressourcenkontrolle mit Transact-SQL**  
  
1.  Um die Definitionen von Resource Governor-Entitäten anzuzeigen, verwenden Sie die [Katalogsichten des Resource Governors &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql).  
  
2.  Um die aktuelle Konfiguration von Resource Governor-Entitäten anzuzeigen, verwenden Sie die [dynamischen Verwaltungssichten in Verbindung mit dem Resource Governor &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Resource Governor](resource-governor.md)   
 [Aktivieren von Resource Governor](enable-resource-governor.md)   
 [Ressourcen Pool Resource Governor](resource-governor-resource-pool.md)   
 [Resource Governor Auslastungs Gruppe](resource-governor-workload-group.md)   
 [Resource Governor Classifier Function](resource-governor-classifier-function.md)  
  
  
