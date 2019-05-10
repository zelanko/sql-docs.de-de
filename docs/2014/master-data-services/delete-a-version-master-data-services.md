---
title: Löschen einer Version (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], deleting
- deleting versions [Master Data Services]
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 1e9f8d65e1a835af954952a64322f21a484a16f3
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65483339"
---
# <a name="delete-a-version-master-data-services"></a>Löschen einer Version (Master Data Services)
  Löschen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eine Version, wenn Sie sicher sind, dass Sie die der Version zugeordneten Masterdaten nicht mehr benötigen. Nachdem Sie eine Version gelöscht haben, können Sie die zugeordneten Masterdaten nicht abrufen.  
  
> [!WARNING]  
>  Wenn ein Modell nur über eine Version verfügt, und Sie diese löschen, wird das Modell unbrauchbar.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen berechtigt sein, die mdm.viw_SYSTEM_SCHEMA_VERSION-Sicht anzuzeigen und die gespeicherte Prozedur mds.udpVersionDelete in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Datenbank auszuführen. Weitere Informationen finden Sie unter [Sicherheit von Datenbankobjekten &#40;Master Data Services&#41;](database-object-security-master-data-services.md).  
  
### <a name="to-delete-a-version"></a>So löschen Sie eine Version  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung mit der [!INCLUDE[ssDE](../includes/ssde-md.md)] -Instanz für die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank her.  
  
2.  Öffnen Sie die mdm.viw_SYSTEM_SCHEMA_VERSION-Sicht.  
  
3.  Suchen Sie die Version des Modells, die Sie löschen möchten, und kopieren Sie den Wert im Feld **ID** .  
  
4.  Erstellen Sie eine neue Abfrage.  
  
5.  Geben Sie den folgenden Text ein, indem Sie *version_ID* durch den in Schritt 2 kopierten Wert ersetzen.  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  Führen Sie die Abfrage aus.  
  
    > [!NOTE]  
    >  Es kann einige Minuten dauern, bis die Änderung in der Webanwendung angezeigt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Versionen &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Kopieren einer Version &#40;Master Data Services&#41;](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
  
