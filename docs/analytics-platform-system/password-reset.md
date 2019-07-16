---
title: Kennwortzurücksetzung - Analytics Platform System | Microsoft-Dokumentation
description: Der Seite "Kennwort zurücksetzen" können Sie zum Ändern des Kennworts für die Administratorkonten von Analytics Platform System verwendet.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5fb3bbb5adba5754c220c34503a22656f6da39c5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960461"
---
# <a name="password-reset---analytics-platform-system"></a>Zurücksetzen des Kennworts - Analytics Platform System
Die **Zurücksetzen des Kennworts** auf der Seite können Sie zum Ändern des Kennworts für die Administratorkonten von Analytics Platform System verwendet.  
  
> [!WARNING]  
> Verwenden Sie immer die **Configuration Manager** der Appliance für Domänenadministratorkennwort zu aktualisieren. Andere Methoden möglicherweise nicht alle Komponenten des Analytics Platform System aktualisiert und Appliance Zugriffsprobleme verursachen können.  
  
Sie erhalten die Kennwörter für Analytics Platform System, wenn das Gerät übermittelt wird. Immer ändern Sie die Kennwörter mit neuen Werten, wenn Sie die Verantwortung für Ihre Anwendung übernehmen. Es gibt drei Kennwörter aktualisieren. Die Kennwörter müssen nicht miteinander übereinstimmen.  
  
**F <*Xxxx*> \Administrator**  
Die **Administrator** von der Domäne der Anwendung.  
  
**. \Administrator**  
Die lokale **Administrator** Konto auf den Computern, auf denen die virtuellen Computer gehostet.  
  
> [!IMPORTANT]  
> Aktualisieren Sie für das Gerät 1 **Configuration Manager** ist nicht ordnungsgemäß ändern das Kennwort für die lokale Administratorkonten in der PDW VM des. Wenn dies erforderlich ist, wenden Sie sich an CSS, weitere Anweisungen zu erhalten.  
  
**sa**  
Die **sa** SQL Server-Anmeldung. **SA** ist ein Mitglied der **Sysadmin** festen Serverrolle und SQL Server-Administrator ist. Das Kennwort für die **sa** Anmeldung kann auch geändert werden, indem Sie mit der **ALTER LOGIN** Anweisung.  
  
## <a name="password-requirements"></a>Kennwortanforderungen  
Sowohl der System-Administratoranmeldeinformationen als auch die Anmeldeinformationen des Domänenadministrators an die und die Richtlinien zur kennwortsicherheit, für jeden Typ von Anmeldeinformationen. Wenn Sie die Anmeldeinformationen des Domänenadministrators zu ändern, wird das neue Kennwort in die Domäne aktualisiert bei Bedarf in der gesamten SQL Server PDW.  
  
> [!IMPORTANT]  
> SQL Server PDW unterstützt nicht das Dollarzeichen ( **$** ) in der Administrator der Domäne oder lokaler Administratorkennwörter. Die Zeichen **^ % &** dürfen in Kennwörtern, jedoch PowerShell als Sonderzeichen betrachtet. Wenn eines dieser Zeichen in Kennwörtern, für die vom Systemadministrator oder den SQL Server verwendet werden**sa** Konten (die **AdminPassword** und **PdwSAPassword** Parametern während der Setup) klicken Sie dann setup, einschließlich Installation, UPGRADE, "replaceNode" auf und PATCHEN, schlägt fehl. Um ein erfolgreiches Upgrade sicherzustellen, wenn der aktuelle Kennwörter nicht unterstützte Zeichen enthalten, ändern Sie diese Kennwörter, sodass sie vor dem Ausführen der Aktualisierung keine solche Zeichen enthalten. Nach Abschluss des Upgrades können Sie diese Kennwörter wieder auf ihre ursprünglichen Werte festlegen. Weitere Informationen zu kennwortanforderungen finden Sie unter [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md).  
  
## <a name="to-reset-a-password"></a>Zurücksetzen eines Kennworts  
  
1.  Herstellen einer Verbindung den Steuerelementknoten aus, und starten Sie mit der **Configuration Manager** (**dwconfig.exe**). Weitere Informationen finden Sie unter [Starten des Konfigurations-Managers &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Klicken Sie im linken Bereich die **Configuration Manager**, klicken Sie auf **Zurücksetzen des Kennworts**.  
  
3.  Wählen Sie den Administrator aus der **Konto** Dropdown-Menü, und geben Sie dann auf das neue Kennwort in die **Kennwort** und **Kennwort bestätigen** Felder. Klicken Sie auf **übernehmen** zum Speichern der Änderungen.  
  
    Auf diese Konten vorgenommene Änderungen wirken sich nicht auf alle aktuell aktiven Sitzungen, aber bei der nächsten Anmeldung für jeden Benutzer gelten.  
  
    ![SQL Server DWConfig, Kennwort](./media/password-reset/SQL_Server_PDW_DWConfig_TopPW.png "SQL_Server_PDW_DWConfig_TopPW")  
  
## <a name="see-also"></a>Siehe auch  
[Festlegen des Administratorkennworts für die Anmeldung bei AD-Knoten in der im Verzeichnisdienst-Wiederherstellungsmodus &#40;DSRM&#41; &#40;Analytics Platform System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md)  
[Starten Sie den Konfigurations-Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
  
