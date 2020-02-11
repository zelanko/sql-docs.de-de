---
title: Daten Import (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], about staging process
- importing data [Master Data Services]
- staging process [Master Data Services]
ms.assetid: 181d1e22-379c-45d1-b03c-e1e22ff14164
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7f5f5e7d6c4706dee09c90237c2363f6cbf46b02
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479015"
---
# <a name="data-import-master-data-services"></a>Datenimport (Master Data Services)
  Nach der Erstellung eines Modells für Ihre Daten in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie beginnen, Daten hinzufügen und Änderungen an Daten in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Datenbank vorzunehmen.   Sie verwenden [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Stagingtabellen, gespeicherte Prozeduren und Master Data Manager.  
  
 Sie können [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]auch das verwenden, um dem MDS-Repository ([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank) Daten hinzuzufügen. Weitere Informationen finden Sie unter [Veröffentlichen von Daten &#40;MDS-Add-in für Excel&#41;](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md).  
  
 Beim Hinzufügen und Aktualisieren von Daten können Sie Folgendes tun.  
  
-   Laden und Aktualisieren von Elementen und Aktualisieren von Attributwerten  
  
-   Deaktivieren und Löschen von Elementen  
  
-   Verschieben von Elementen der expliziten Hierarchie  
  
 Das Hinzufügen und Aktualisieren von Daten besteht hauptsächlich in den folgenden Aufgaben.  
  
1.  Laden von Daten in die Stagingtabellen in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank.  
  
2.  Laden von Daten aus den Stagingtabellen in die entsprechenden [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Tabellen.  
  
     Zum Laden der Daten verwenden Sie gespeicherte Prozeduren oder [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
> [!NOTE]  
>  In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]ist die Unterstützung für die [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] -Stagingprozesse veraltet.  
  
## <a name="deactivating-and-deleting-members"></a>Deaktivieren und Löschen von Elementen  
 Deaktivieren bedeutet, dass das Element erneut aktiviert werden kann. Wenn Sie ein Element erneut aktivieren, werden seine Attribute und Mitgliedschaft in Hierarchien und Auflistungen wiederhergestellt. Alle vorherigen Transaktionen sind intakt. Deaktivierungstransaktionen werden Administratoren im Funktionsbereich **Versionsverwaltung** von Master Data Manager angezeigt.  
  
 Löschen bedeutet, das Element dauerhaft vom System zu entfernen. Alle Transaktionen für das Element, alle Beziehungen und alle Attribute werden dauerhaft gelöscht.  
  
> [!NOTE]  
>  Per Staging können Sie keine Elemente erneut aktivieren. Diesen Vorgang müssen Sie manuell in Master Data Manager ausführen. Weitere Informationen finden Sie unter [Reaktivieren eines Elements oder einer Sammlung &#40;Master Data Services&#41](reactivate-a-member-or-collection-master-data-services.md).  
>   
>  Per Staging können Sie keine Auflistungen löschen oder deaktivieren. Weitere Informationen zum manuellen Deaktivieren von Sammlungen finden Sie unter [Löschen eines Elements oder einer Sammlung &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md).  
  
## <a name="moving-explicit-hierarchy-members"></a>Verschieben Elementen der expliziten Hierarchie  
 Beim Massenverschieben der Position von Elementen der expliziten Hierarchie können Sie die folgenden Festlegungen treffen.  
  
-   Ein konsolidiertes Element als übergeordnetes Element eines konsolidierten Elements  
  
-   Ein konsolidiertes Element als übergeordnetes Element eines Blattelements  
  
-   Ein Blattelement als ein gleichgeordnetes Element eines Blattelements oder eines konsolidierten Elements  
  
-   Ein konsolidiertes Element als ein gleichgeordnetes Element eines Blattelements oder eines konsolidierten Elements  
  
## <a name="staging-tables-and-stored-procedures"></a>Stagingtabellen und gespeicherte Prozeduren  
 Die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank enthält die folgenden Typen von Stagingtabellen, die Sie mit Ihren Daten auffüllen können.  
  
-   [&#40;Master Data Services der Stagingtabelle für Blatt Elemente&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md)  
  
-   [Konsolidierte Element-Stagingtabelle &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)  
  
-   [Stagingtabelle für Beziehungen &#40;Master Data Services&#41;](../../2014/master-data-services/relationship-staging-table-master-data-services.md)  
  
 Für jede Entität im Modell gibt es eine Stagingtabelle. Der Tabellenname gibt die entsprechende Entität und den Entitätstyp an, wie etwa ein Blattelement. In der folgenden Abbildung sind die Stagingtabellen für die Entitäten „Währung“, „Kunde“ und „Produkt“ dargestellt.  
  
 ![Stagingtabellen in der MDS-Datenbank](../../2014/master-data-services/media/mds-stagingtables.png "Stagingtabellen in der MDS-Datenbank")  
  
 Der Name der Tabelle wird beim Erstellen einer Entität angegeben und kann nicht geändert werden. Wenn der Stagingtabellenname eine _1 oder eine andere Zahl enthält, war eine andere Tabelle dieses Namens bereits vorhanden, als die Entität erstellt wurde.  
  
 
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] beinhaltet die folgenden Typen von gespeicherten Stagingprozeduren.  
  
-   stg.udp_\<name>_Leaf  
  
-   stg.udp_\<name>_Consolidated  
  
-   stg.udp_\<name>_Relationship  
  
 Für jede Entität im Modell gibt es drei gespeicherte Prozeduren, die dem Blattelement, dem konsolidierten Element und der Stagingtabelle für Beziehungen entsprechen.  In der folgenden Abbildung sind die gespeicherten Stagingprozeduren für die Entitäten „Währung“, „Kunde“ und „Produkt“ dargestellt.  
  
 ![Gespeicherte Stagingprozeduren in der MDS-Datenbank](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "Gespeicherte Stagingprozeduren in der MDS-Datenbank")  
  
 Weitere Informationen zu den gespeicherten Prozeduren finden Sie unter [Gespeicherte Stagingprozedur &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).  
  
## <a name="logging-transactions"></a>Protokollieren von Transaktionen  
 Alle Transaktionen, die auftreten, wenn Daten oder Beziehungen importiert oder aktualisiert werden, können protokolliert werden. Eine Option in der gespeicherten Prozedur ermöglicht diese Protokollierung. Wenn Sie den Stagingprozess mithilfe von [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]einleiten, erfolgt keine Protokollierung.  
  
 In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]wird die Einstellung **Protokollieren aller Stagingtransaktionen** nicht für diese Methode zum Bereitstellen von Daten angewendet.  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Master Data Services der Überprüfung &#40;&#41;](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [Master Data Services von Geschäftsregeln &#40;&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
