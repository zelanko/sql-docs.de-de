---
title: Ändern des System Administrator Kontos (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 911bd20c7d232bca52fdf9dca294bd7a4924d984
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054140"
---
# <a name="change-the-system-administrator-account-master-data-services"></a>Ändern Systemadministratorkontos (Master Data Services)
  Sie können das Benutzerkonto ändern, das als [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Systemadministrator festgelegt ist.  
  
> [!WARNING]  
>  Wenn Sie diese Prozedur ausführen, wird das Benutzerkonto des vorherigen Systemadministrators gelöscht.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen der Liste Benutzer in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] den Benutzernamen des neuen Administrators hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen eines Benutzer &#40;Master Data Services&#41;](add-a-user-master-data-services.md).  
  
-   Sie müssen berechtigt sein, die Tabelle mdm.tblUser anzuzeigen und die gespeicherte Prozedur mdm.udpSecurityMemberProcessRebuildModel in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Datenbank auszuführen. Weitere Informationen finden Sie unter [Sicherheit von Datenbankobjekten &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-change-the-administrator-account"></a>So ändern Sie das Administratorkonto  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung mit der [!INCLUDE[ssDE](../includes/ssde-md.md)] -Instanz für die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank her.  
  
2.  Suchen Sie in MDM. tbluser den Benutzer, der als neuer Administrator verwendet werden soll, und kopieren Sie `SID` den Wert in der Spalte.  
  
3.  Erstellen Sie eine neue Abfrage.  
  
4.  Geben Sie den folgenden Text ein, und ersetzen Sie dabei *Domain \ user_name* durch den Benutzernamen und die *sid* des neuen Administrators durch den Wert, den Sie in Schritt 2 kopiert haben.  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  Führen Sie die Abfrage aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Administratoren &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
