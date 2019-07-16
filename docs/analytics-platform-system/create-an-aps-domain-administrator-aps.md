---
title: Erstellen Sie ein Domänenadministrator - Analytics Platform System | Microsoft-Dokumentation
description: Einige Vorgänge erfordern, Analytics Platform System Domänenadministratorrechten an. Dies erklärt, wie weitere Appliance Domänenadministratoren zu erstellen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 51ed729cda33b5d68a4d115c71f712e2b81d1a65
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961094"
---
# <a name="create-an-aps-domain-administrator"></a>Erstellen eines APS-Domain-Administrators
Einige Vorgänge erfordern, Analytics Platform System Domänenadministratorrechten an. Dies erklärt, wie weitere Appliance Domänenadministratoren zu erstellen.  
  
## <a name="create-a-domain-administrator"></a>Erstellen Sie ein Domänenadministrator  
Damit ausreichende Berechtigungen zum Konfigurieren von allen APS-Knoten, des Benutzers ausführt der **APS-Konfigurations-Manager** (`dwconfig.exe`) muss ein Mitglied der **Domänen-Admins** Gruppe. Starten und Beenden der APS-Dienste, muss der Benutzer ein Mitglied der **PdwControlNodeAccess** Gruppe.  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>Gruppe der Domänenadministratoren einen Benutzer hinzu  
  
1.  Melden Sie sich bei dem aktiven Knoten der AD **(_Appliance\_Domäne_-AD01** oder  **_Appliance\_Domäne_-AD02**) verwenden ein vorhandenes Gerät Domänenadministratorkonto.  
  
2.  Klicken Sie im Startmenü auf **Ausführen**. In der **öffnen** geben **dsa.msc**. Klicken Sie auf **OK**.  
  
3.  In der **Active Directory-Benutzer und-Computer** Programm, mit der rechten Maustaste **Benutzer**, zeigen Sie auf **neu**, und klicken Sie dann auf **Benutzer**.  
  
4.  In der **neues Objekt – Benutzer** (Dialogfeld), führen Sie die Beschreibung des neuen Benutzers, und klicken Sie dann auf **Weiter**.  
  
    Führen Sie das Kennwort (Dialogfeld), und klicken Sie dann auf **Weiter**.  
  
    > [!WARNING]  
    > SQL Server PDW unterstützt nicht das Dollarzeichen ($) in der Administrator der Domäne oder lokaler Administratorkennwörter. Ein Kennwort mit einem Dollarzeichen ungültig wird, und verwendet werden, jedoch können Upgrade- und wartungsplanlizenzen Aktivitäten blockieren  
  
    Bestätigen Sie die neue benutzerbeschreibung aus, und klicken Sie dann auf **Fertig stellen**.  
  
5.  Doppelklicken Sie in der Liste der Benutzer auf den neuen Benutzer aus, um das Dialogfeld Eigenschaften für Benutzer zu öffnen.  
  
6.  Auf der **Mitglied von** auf **hinzufügen**.  
  
    Typ **Domänen-Admins; PdwControlNodeAccess** , und klicken Sie dann auf **Namen überprüfen**. Klicken Sie auf **OK**.  
  
    Dadurch wird den neuen Benutzer hinzugefügt. die **Domänen-Admins** Gruppe und die **PdwControlNodeAccess** Gruppe. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
[Starten Sie den Konfigurations-Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
  
