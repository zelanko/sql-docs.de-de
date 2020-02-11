---
title: Zurücksetzen von Kennwörtern
description: Auf der Seite Kenn Wort Zurücksetzung können Sie das Kennwort für die Administrator Konten ändern, die von Analytics Platform System verwendet werden.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 952dbda04b4f7132406e3a6de4479afea1be92e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400907"
---
# <a name="password-reset---analytics-platform-system"></a>Kenn Wort Zurücksetzung-Analytics Platform System
Auf der Seite Kenn **Wort** Zurücksetzung können Sie das Kennwort für die Administrator Konten ändern, die von Analytics Platform System verwendet werden.  
  
> [!WARNING]  
> Verwenden Sie immer die **Configuration Manager** , um das Kennwort des Anwendungs Domänen Administrators zu aktualisieren. Bei anderen Methoden werden möglicherweise nicht alle Komponenten von Analytics Platform System aktualisiert, und es kann zu Problemen beim Gerätezugriff kommen.  
  
Sie erhalten die Analytics-Platt Form System Kennwörter, wenn das Gerät übermittelt wird. Ändern Sie die Kenn Wörter immer in neue Werte, wenn Sie die Verantwortung für Ihre Appliance übernehmen. Es sind drei Kenn Wörter zum Aktualisieren vorhanden. Die Kenn Wörter müssen nicht identisch sein.  
  
**F<*xxxx*> \administrator**  
Der **Administrator** der Appliance-Domäne.  
  
**.\Administrator**  
Das lokale **Administrator** Konto auf den Computern, auf denen die virtuellen Maschinen gehostet werden.  
  
> [!IMPORTANT]  
> Bei Appliance Update 1 ändert **Configuration Manager** nicht ordnungsgemäß das Kennwort der lokalen Administrator Konten in der PDW-VM. Wenn dies erforderlich ist, wenden Sie sich an CSS.  
  
**SAS**  
Der **sa** -Anmelde Name in SQL Server. **sa** ist ein Mitglied der festen Server Rolle **sysadmin** und ist ein SQL Server Administrator. Das Kennwort für die **sa** -Anmeldung kann auch mit der **Alter Login** -Anweisung geändert werden.  
  
## <a name="password-requirements"></a>Kenn Wort Anforderungen  
Die Anmelde Informationen des Domänen Administrators und die Systemadministrator-Anmelde Informationen entsprechen den Richtlinien für die Kenn Wort Sicherheit für jeden Anmelde Informationstyp. Wenn Sie die Anmelde Informationen des Domänen Administrators ändern, wird das neue Kennwort in der gesamten SQL Server PDW in die Domäne aktualisiert.  
  
> [!IMPORTANT]  
> SQL Server PDW unterstützt das Dollarzeichen (**$**) in den Domänen Administrator-oder lokalen Administrator Kennwörtern nicht. Die Zeichen **^% &** sind in Kenn Wörtern zulässig, PowerShell berücksichtigt diese jedoch als Sonderzeichen. Wenn keines dieser Zeichen in Kenn Wörtern für die Systemadministrator-oder SQL Server**sa** -Konten (die Parameter **AdminPassword** und **pdwsapassword** während des Setups) verwendet wird, tritt beim Setup ein Fehler auf. Um ein erfolgreiches Upgrade sicherzustellen, wenn aktuelle Kenn Wörter nicht unterstützte Zeichen enthalten, ändern Sie diese Kenn Wörter so, dass Sie vor dem Ausführen des Upgrades keine solchen Zeichen enthalten. Nachdem das Upgrade abgeschlossen ist, können Sie diese Kenn Wörter auf ihre ursprünglichen Werte zurücksetzen. Weitere Informationen zu Kenn Wort Anforderungen finden Sie unter [Alter Login](../t-sql/statements/alter-login-transact-sql.md).  
  
## <a name="to-reset-a-password"></a>Zurücksetzen eines Kennworts  
  
1.  Stellen Sie eine Verbindung mit dem Steuer Knoten her, und starten Sie den **Configuration Manager** (**dwconfig. exe**). Weitere Informationen finden Sie unter [Start the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Klicken Sie im linken Bereich der **Configuration Manager**auf Kenn **Wort**Zurücksetzung.  
  
3.  Wählen Sie im Dropdown Menü **Konto** den Typ Administrator aus, und geben Sie dann das neue Kennwort in die Felder **Kennwort** und **Kennwort bestätigen** ein. Klicken **Sie auf über** nehmen, um die Änderungen zu speichern.  
  
    Änderungen, die Sie an diesen Konten vornehmen, wirken sich nicht auf derzeit aktive Sitzungen aus, werden aber beim nächsten Anmeldeversuch für jeden Benutzer angewendet.  
  
    ![SQL Server DWConfig, Kennwort](./media/password-reset/SQL_Server_PDW_DWConfig_TopPW.png "SQL_Server_PDW_DWConfig_TopPW")  
  
## <a name="see-also"></a>Weitere Informationen  
[Legen Sie das Administrator Kennwort für die Anmeldung bei AD-Knoten im Verzeichnisdienst-Wiederherstellungs Modus &#40;DSRM&#41; &#40;Analytics Platform System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md)  
[Starten Sie die Configuration Manager &#40;Analytics-Platt Form System&#41;](launch-the-configuration-manager.md)  
  
