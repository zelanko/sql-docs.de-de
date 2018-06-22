---
title: Master Data Services-Add-In für Microsoft Excel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33d9c8fc-9602-494d-b9ab-8f0f42785974
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 06f20a19801b43a25f3622424aa8ce76d2c34df2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058731"
---
# <a name="master-data-services-add-in-for-microsoft-excel"></a>Master Data Services-Add-In für Microsoft Excel
  Mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], masterlisten mit Verweisdaten an alle Benutzer in Ihrer Organisation, die Excel verwenden verteilt werden können. Mit Sicherheit wird festgelegt, welche Daten die Benutzer anzeigen und aktualisieren können.  
  
 Sie können gefilterte Listen der Daten von MDS in Excel laden, wo Sie damit so arbeiten können, wie Sie dies mit beliebigen anderen Daten tun würden. Wenn Sie fertig sind, können Sie die Daten in MDS veröffentlichen, wo sie zentral gespeichert werden.  
  
 Wenn Sie Administrator sind, verwenden Sie [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] , um Entitäten und Attribute zu erstellen und sie mit Daten zu laden. Dadurch ist es nicht mehr erforderlich, beliebige andere Tools zum Laden von Daten in die Modelle zu verwenden.  
  
 In [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]können Sie mithilfe von Data Quality Services (DQS) Daten vor dem Laden in MDS zuordnen. Dadurch werden doppelte Daten in MDS verhindert.  
  
> [!IMPORTANT]  
>  Sie können weiterhin verwenden die [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1-Version des Master Data Services Add-Ins für Excel nach dem Upgrade Master Data Services und Data Quality Services auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Frühere Versionen des Master Data Services-Add-Ins für Excel sind nach einem Upgrade auf SQL Server 2014 CTP2 jedoch nicht funktionsfähig. Sie können die [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1-Version des Master Data Services Add-Ins für Excel aus [hier](http://go.microsoft.com/fwlink/?LinkId=328664).  
  
## <a name="terms"></a>Begriffe  
 Wenn Sie mit dem Add-In arbeiten, stoßen Sie möglicherweise auf die folgenden Begriffe.  
  
-   Das *MDS repository* ist, wo alle Masterdaten gespeichert sind. Es ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank, die zum Speichern von MDS-Daten konfiguriert ist. Um mit Daten aus dem Repository zu arbeiten, laden Sie die Daten in Excel. Wenn Sie mit der Arbeit fertig sind, veröffentlichen Sie die Änderungen im Repository. Administratoren können dem Repository neue Entitäten und Attribute hinzufügen.  
  
-   *Von MDS verwaltete Daten* sind Daten, die im MDS-Repository gespeichert sind und die Sie in Excel laden, wo die Daten als markierte Zeilen angezeigt werden. Sie können Daten hinzufügen, die nicht von MDS verwaltet werden und die nicht davon betroffen sind, wenn Sie die von MDS verwalteten Daten aktualisieren.  
  
-   Ein *model* ist ein Container mit Daten. Versionen dieser Container können erstellt werden, und normalerweise ist die neueste Version die aktuellste. Weitere Informationen finden Sie unter [Modelle &#40;Master Data Services&#41;](../models-master-data-services.md).  
  
-   Eine *entity* ist eine Liste mit Daten. Sie können sich eine Entität als Tabelle in einer Datenbank vorstellen. Die Entität **Farbe** könnte z. B. eine Liste mit Farben enthalten. Weitere Informationen finden Sie unter [Entitäten &#40;Master Data Services&#41;](../entities-master-data-services.md).  
  
-   Ein *member* ist eine Zeile mit Daten. Jede Entität enthält Elemente. Ein Beispiel für ein Element ist **Blau**. Weitere Informationen finden Sie unter [Elemente &#40;Master Data Services&#41;](../members-master-data-services.md).  
  
-   Ein *attribute* ist eine Spalte mit Daten. Jedes Element verfügt über Attribute. Das Attrribut **Code** für das Element **Blau** ist z.B. **B**. Weitere Informationen zu Attributen finden Sie unter [Attribute &#40;Master Data Services&#41;](../attributes-master-data-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen Sie eine Verbindung zu einem [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Repository.|[Herstellen einer Verbindung mit einem MDS-Repository &#40;MDS-Add-In für Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Laden Sie von MDS verwaltete Daten in Excel.|[Laden von Daten aus MDS in Excel](export-data-to-excel-from-master-data-services.md)|  
|Speichern Sie eine Shortcutabfrage, die Sie zum Öffnen der gerade angezeigten, von MDS verwalteten Daten verwenden können.|[Speichern einer Shortcutabfragedatei &#40;MDS-Add-In für Excel&#41;](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Geben Sie Verknüpfungen für andere frei.|[Senden einer Shortcutabfragedatei &#40;MDS-Add-In für Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Zeigen Sie alle Änderungen an, die an einem Element vorgenommen wurden.|[Anzeigen aller Anmerkungen oder Transaktionen für ein Element &#40;MDS-Add-In für Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
|Ermitteln Sie vor dem Veröffentlichen von neuen Daten, ob doppelte Werte vorhanden sind.|[Abgleichen ähnlicher Daten &#40;MDS-Add-In für Excel&#41;](match-similar-data-mds-add-in-for-excel.md)|  
|Veröffentlichen Sie Daten eines Arbeitsblatts im MDS-Repository.|[Veröffentlichen von Daten aus Excel nach MDS &#40;MDS-Add-in für Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Erstellen Sie im Arbeitsblatt eine neue Entität mit Daten. (Nur Administratoren)|[Erstellen einer Entität &#40;MDS-Add-In für Excel&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|Erstellen Sie ein domänenbasiertes Attribut, das auch als eingeschränkte Liste bezeichnet wird. (Nur Administratoren)|[Erstellen eines domänenbasierten Attributs &#40;MDS-Add-In für Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Legen Sie Eigenschaften zum Laden und dem Veröffentlichen von Daten im Master Data Services-Add-In für Excel fest. (Nur Administratoren)|[Festlegen von Eigenschaften für das Master Data Services-Add-In für Microsoft Excel](setting-properties-for-master-data-services-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Verbindungen &#40;MDS-Add-In für Excel&#41;](connections-mds-add-in-for-excel.md)  
  
-   [Laden von Daten &#40;MDS-Add-in für Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Shortcutabfragedateien &#40;MDS-Add-In für Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Data Quality-Abgleich im MDS-Add-In für Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
-   [Veröffentlichen von Daten &#40;MDS-Add-in für Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [Erstellen eines Modells &#40;MDS-Add-In für Excel&#41;](building-a-model-mds-add-in-for-excel.md)  
  
-   [Sicherheit &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
  