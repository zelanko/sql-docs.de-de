---
title: Erstellen eines Domänen Administrators
description: Einige Vorgänge erfordern Analytics-Platt Form System-Domänen Administrator Berechtigungen. Hier wird erläutert, wie zusätzliche Anwendungs Domänen Administratoren erstellt werden.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 1a0d50e485f0e8f48de11b2e5a3c27c9f9be047e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401234"
---
# <a name="create-an-aps-domain-administrator"></a>Erstellen eines APS-Domänen Administrators
Einige Vorgänge erfordern Analytics-Platt Form System-Domänen Administrator Berechtigungen. Hier wird erläutert, wie zusätzliche Anwendungs Domänen Administratoren erstellt werden.  
  
## <a name="create-a-domain-administrator"></a>Erstellen eines Domänen Administrators  
Damit alle APS-Knoten über ausreichende Berechtigungen verfügen, muss der Benutzer, der die APS`dwconfig.exe`- **Configuration Manager** () ausführen muss, Mitglied der Gruppe " **Domänen-Admins** " sein. Um die APS-Dienste zu starten und anzuhalten, muss der Benutzer Mitglied der Gruppe " **pdwcontrolnodebug Access** " sein.  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>So fügen Sie der Gruppe "Domänen-Admins" einen Benutzer hinzu  
  
1.  Melden Sie sich mit einem vorhandenen Anwendungs Domänen Administrator Konto beim aktiven AD-Knoten **(_Appliance\_Domain_-ad01** oder ** _Appliance\_Domain_-ad02**) an.  
  
2.  Klicken Sie im Startmenü auf **Ausführen**. Geben Sie **DSA. msc**in das Feld **Öffnen** ein. Klicken Sie auf **OK**.  
  
3.  Klicken Sie im Programm **Active Directory Benutzer und Computer** mit der rechten Maustaste auf **Benutzer**, zeigen Sie auf **neu**, und klicken Sie dann auf **Benutzer**.  
  
4.  Vervollständigen Sie im Dialogfeld **Neues Objekt-Benutzer** die Beschreibung des neuen Benutzers, und klicken Sie dann auf **weiter**.  
  
    Vervollständigen Sie das Dialogfeld Kennwort, und klicken Sie dann auf **weiter**.  
  
    > [!WARNING]  
    > Der SQL Server PDW unterstützt das Dollarzeichen ($) in den Domänen Administrator-oder lokalen Administrator Kennwörtern nicht. Ein Kennwort mit einem Dollarzeichen ist gültig und kann verwendet werden, kann aber Upgrade-und Wartungsaktivitäten blockieren.  
  
    Bestätigen Sie die neue Benutzer Beschreibung, und klicken Sie dann auf **Fertig**stellen.  
  
5.  Doppelklicken Sie in der Benutzerliste auf den neuen Benutzer, um das Dialogfeld Benutzereigenschaften zu öffnen.  
  
6.  Klicken Sie auf der Registerkarte **Mitglied von** auf **Hinzufügen**.  
  
    Geben Sie **Domain Admins ein. Pdwcontrolnodebug Access** und klicken Sie dann auf **Namen überprüfen**. Klicken Sie auf **OK**.  
  
    Dadurch wird der neue Benutzer der Gruppe " **Domänen-Admins** " und der Gruppe " **pdwcontrolnodeaccess** " hinzugefügt. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
[Starten Sie die Configuration Manager &#40;Analytics-Platt Form System&#41;](launch-the-configuration-manager.md)  
  
