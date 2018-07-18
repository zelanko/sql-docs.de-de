---
title: Zuweisen von DQS-Rollen an Benutzer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3b4e5c0dfa7b30977fb2ac27d4f4599fa4b4414c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224086"
---
# <a name="grant-dqs-roles-to-users"></a>Zuweisen von DQS-Rollen an Benutzer
  In diesem Thema wird beschrieben, wie SQL-Anmeldungen auf Grundlage eines Windows-Prinzipals erstellt werden und wie ihnen [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS)-Rollen für die DQS_MAIN-Datenbank gewährt werden.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   Sie müssen die Installation des [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] durch Ausführen der Datei DQSInstaller.exe abgeschlossen haben. Weitere Informationen finden Sie unter [Ausführen von DQSInstaller.exe zum Abschließen der Installation von Data Quality Server](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
-   Ihr Windows-Benutzerkonto muss Mitglied der entsprechenden festen Serverrolle (z. B. securityadmin, serveradmin, sysadmin) sein, um eine SQL-Anmeldung zu erstellen und ihr DQS-Rollen zuzuweisen.  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a>So erstellen Sie eine SQL-Anmeldung und gewähren DQS-Rollen  
  
1.  Starten Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
2.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die SQL Server-Instanz, und erweitern Sie dann **Sicherheit**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Sicherheit** , zeigen Sie auf **Neu**, und wählen Sie dann **Anmeldung**aus.  
  
4.  Geben Sie im Dialogfeld **Anmeldung – Neu** den Namen eines Windows-Benutzers im Feld **Anmeldename** ein, geben Sie für den Authentifizierungstyp **Windows-Authentifizierung**an, und klicken Sie auf **Suchen** , um den Benutzer zu überprüfen.  
  
5.  Klicken Sie nach der Überprüfung des Benutzers auf die Seite **Benutzerzuordnung** im linken Bereich.  
  
6.  Aktivieren Sie im rechten Bereich das Kontrollkästchen unter der Spalte **Zuordnen** für die **DQS_MAIN** -Datenbank, und aktivieren Sie dann das Kontrollkästchen **dqs_administrator**, **dqs_kb_editor**oder **dqs_kb_operator** im Bereich **Mitgliedschaft in Datenbankrolle für: DQS_MAIN** , je nachdem, welche Zugriffsebene für den Benutzer benötigt wird. Weitere Informationen zu den drei DQS-Rollen finden Sie unter [DQS Security](../dqs-security.md).  
  
7.  Klicken Sie im Dialogfeld **Anmeldung - Neu** auf **OK** , um die Änderungen zu übernehmen.  
  
    > [!NOTE]  
    >  Wenn Sie einem Benutzer die **dqs_administrator** -Rolle gewähren, übernehmen Sie die Änderungen, und überprüfen Sie dann erneut die Benutzerberechtigungen und ob die beiden anderen Kontrollkästchen für DQS-Rollen (**dq_kb_editor** und **dqs_kb_operator**) auch aktiviert sind.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Melden Sie sich mit dem soeben erstellten Windows-Benutzerkonto, dem Sie die DQS-Rolle gewährt haben, beim [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] an.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von Data Quality Services](install-data-quality-services.md)   
 [Erstellen eines Anmeldenamens](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  
