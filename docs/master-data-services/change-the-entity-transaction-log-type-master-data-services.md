---
title: Ändern des Transaktionsprotokolltyps von Entitäten
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 75250b32-3384-43c2-9b5c-1607cc3aa7b3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fde8e314462846088c7c673524d6e6d8d29ee631
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729665"
---
# <a name="change-the-entity-transaction-log-type-master-data-services"></a>Ändern des Transaktionsprotokolltyps von Entitäten (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Sie können den Transaktionsprotokolltyp einer Entität in "Attribut", "Element" oder "Keiner" ändern.  
  
|Transaktionsprotokolltyp|BESCHREIBUNG|  
|--------------------------|-----------------|  
|attribute|Entitätsänderungsprotokolle werden auf Attributebene gespeichert.<br /><br /> Das Transaktionsprotokoll wird gespeichert, wie dies für [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]der Fall ist.|  
|Mitglied|Entitätsänderungsprotokolle werden auf Zeilenebene gespeichert.<br /><br /> Jede Attributänderung löst eine neue Zeilenrevision aus.<br /><br /> Bei Verwendung des Transaktionsprotokolltyps mit Zeilen wird die Entität als langsam veränderliche Dimension vom Typ 4 gespeichert. Die Abonnementsichten vom Typ 2 und Typ 4 (Verlauf) werden unterstützt. Weitere Informationen finden Sie unter [Abonnementsichtformate &#40;Master Data Services&#41;](../master-data-services/subscription-view-formats-master-data-services.md).<br /><br /> Bietet eine bessere Leistung.|  
|Keine|Es werden keine Änderungsprotokolle gespeichert.<br /><br /> Bietet die beste Leistung.|  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich der Systemverwaltung verfügen. Weitere Informationen finden Sie unter [Berechtigungen für Funktionsbereiche &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Die Entität muss vorhanden sein. Weitere Informationen finden Sie unter [Erstellen einer Entität &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
 **So ändern Sie den Transaktions protokoltentyp**  
  
1.  Klicken Sie im Master Data Manager auf **Systemverwaltung**.  
  
2.  Wählen Sie auf der Seite **Modell verwalten** die Zeile für das Modell der Entität aus, die Sie bearbeiten möchten, und klicken Sie anschließend auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entität verwalten** die Zeile der Entität aus, die Sie aktualisieren möchten, und klicken Sie anschließend auf **Bearbeiten**.  
  
4.  Wählen Sie in der Dropdownliste des Transaktionsprotokolltyp aus.  
  
5.  Klicken Sie auf **Speichern**.  
  
  
