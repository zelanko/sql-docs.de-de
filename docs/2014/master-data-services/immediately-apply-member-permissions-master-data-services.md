---
title: Sofortiges Anwenden von Elementberechtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], applying permissions immediately
- permissions [Master Data Services], applying member permissions immediately
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 913c57bd4023f0db5a0b3db37d3176a083cd7951
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37331890"
---
# <a name="immediately-apply-member-permissions-master-data-services"></a>Sofortiges Anwenden von Elementberechtigungen (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie sofort Elementberechtigungen anwenden, statt zu warten, bis die Elementsicherheit in regelmäßigen Abständen angewendet wird.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, die gespeicherte Prozedur mdm.udpSecurityMemberProcessRebuildModel in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Datenbank auszuführen. Weitere Informationen finden Sie unter [Sicherheit von Datenbankobjekten &#40;Master Data Services&#41;](database-object-security-master-data-services.md).  
  
### <a name="to-immediately-apply-hierarchy-member-permissions"></a>So wenden Sie Hierarchieelementberechtigungen sofort an  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung mit der [!INCLUDE[ssDE](../includes/ssde-md.md)] -Instanz für die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank her.  
  
2.  Erstellen Sie eine neue Abfrage.  
  
3.  Geben Sie den folgenden Text ein, und ersetzen Sie *Datenbank* durch den Namen Ihrer Datenbank und *Name des Modells* durch den Namen des Modells.  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  Führen Sie die Abfrage aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Zuweisen von Berechtigungen für Hierarchieelemente &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Berechtigungen für Hierarchieelemente &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
