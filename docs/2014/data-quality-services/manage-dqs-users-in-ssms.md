---
title: Verwalten von DQS-Benutzern in SSMS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d8d7e0c31b1e022445006598f791716d765b98c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62792389"
---
# <a name="manage-dqs-users-in-ssms"></a>Verwalten von DQS-Benutzern in SSMS
  In diesem Thema wird beschrieben, wie mit SQL Server Management Studio zusätzliche Benutzer in der SQL Server-Instanz erstellt werden und wie ihnen entsprechende [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS)-Rollen für die DQS_MAIN-Datenbank gewährt werden.  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Ihr Windows-Benutzerkonto muss Mitglied der entsprechenden festen Serverrolle (z. B. securityadmin, serveradmin oder sysadmin) sein, um eine SQL-Anmeldung zu erstellen und ihr entsprechende DQS-Rollen zuzuweisen.  
  
##  <a name="GrantRoles"></a> Erstellen Sie eine SQL-Anmeldung und gewähren DQS-Rolle  
  
1.  Starten Sie Microsoft SQL Server Management Studio.  
  
2.  Erweitern Sie in Microsoft SQL Server Management Studio die SQL Server-Instanz, und erweitern Sie **Sicherheit**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Sicherheit** , zeigen Sie auf **Neu**, und wählen Sie dann **Anmeldung**aus.  
  
4.  Geben Sie im Dialogfeld **Anmeldung – Neu** den Namen eines Windows-Benutzers im Feld **Anmeldename** ein, geben Sie für den Authentifizierungstyp **Windows-Authentifizierung** an, und klicken Sie auf **Suchen**, um den Benutzer zu überprüfen.  
  
    > [!NOTE]  
    >  DQS unterstützt nur die Windows-Authentifizierung. Die SQL Server-Authentifizierung wird nicht unterstützt.  
  
5.  Klicken Sie nach der Überprüfung des Benutzers auf die Seite **Benutzerzuordnung** im linken Bereich.  
  
6.  Aktivieren Sie im rechten Bereich das Kontrollkästchen unter der Spalte **Map** (Zuordnung) für die **DQS_MAIN**-Datenbank, und aktivieren Sie dann das Kontrollkästchen **dqs_administrator**, **dqs_kb_editor** oder **dqs_kb_operator** im Bereich **Mitgliedschaft in Datenbankrolle für: DQS_MAIN**, je nachdem, welche Zugriffsebene für den Benutzer benötigt wird.  
  
7.  Klicken Sie im Dialogfeld **Anmeldung – Neu** auf **OK**, um die Änderungen zu übernehmen.  
  
    > [!NOTE]  
    >  Wenn Sie einem Benutzer die **dqs_administrator** -Rolle gewähren, übernehmen Sie die Änderungen, und überprüfen Sie dann erneut die Benutzerberechtigungen und ob die beiden anderen Kontrollkästchen für DQS-Rollen (**dq_kb_editor** und **dqs_kb_operator**) auch aktiviert sind.  
  
  
