---
title: Verschlüsselungsschlüssel (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.encryptionkeypanel.F1
ms.assetid: cc7e6f84-80e1-4b5e-9409-d0e074edd147
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: aa9460222d756c76e1ed6489688315ea8b7b0f18
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48144230"
---
# <a name="encryption-keys-ssrs-native-mode"></a>Verschlüsselungsschlüssel (einheitlicher SSRS-Modus)
  Verwenden Sie die Seite "Verschlüsselungsschlüssel", um den symmetrischen Schlüssel zu verwalten, der zum Ver- und Entschlüsseln von Daten auf einem Berichtsserver verwendet wird. Die Verwaltung der Verschlüsselungsschlüssel ist ein wichtiger Teil der Berichtsserverkonfiguration. Der symmetrische Schlüssel wird automatisch beim Erstellen der Berichtsserver-Datenbank erstellt und angewendet. Erstellen Sie eine Sicherungskopie des symmetrischen Schlüssels, sodass Routinewartungsvorgänge durchgeführt werden können. Für die folgenden Wartungsaufgaben ist es erforderlich, dass Sie über eine gültige Kopie des symmetrischen Schlüssels verfügen:  
  
-   Ändern des Dienstkontos für den Berichtsserver-Dienst.  
  
-   Migration einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation zu einem anderen Computer.  
  
-   Konfigurieren einer neuen Berichtsserverinstanz, um eine bereits vorhandene Berichtsserver-Datenbank gemeinsam zu nutzen oder zu verwenden.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
> [!IMPORTANT]  
>  Aus Sicherheitsgründen empfiehlt es sich, den Reporting Services-Verschlüsselungsschlüssel in regelmäßigen Abständen zu ändern. Ein guter Zeitpunkt, um den Schlüssel zu ändern, liegt direkt im Anschluss an ein größeres Versionsupgrade von Reporting Services. Indem der Schlüssel nach einem Upgrade geändert wird, lassen sich zusätzliche Dienstunterbrechungen, die durch eine Änderung des Reporting Services-Verschlüsselungsschlüssels außerhalb des Upgradezyklus verursacht würden, minimieren.  
  
 Das Wiederherstellen des symmetrischen Schlüssels ist notwendig, wenn Sie das Benutzerkonto des Berichtsserver-Diensts aktualisiert haben (und ein anderes Tool als der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager zum Ändern des Kontos verwendet wurde) oder wenn Sie eine Berichtsserverinstallation zu einem neuen Server migrieren.  
  
 Um den symmetrischen Schlüssel vor unbefugtem Zugriff zu schützen, wird der symmetrische Schlüssel mithilfe des privaten Schlüssels des Berichtsserver-Diensts verschlüsselt. Nur der Berichtsserver-Dienst kann die Sperre des symmetrischen Schlüssels aufheben und ihn zum Speichern sensibler Daten in der Berichtsserver-Datenbank verwenden. Wenn Sie die Identität des Berichtsserver-Diensts ändern oder den Berichtsserver zu einem neuen Computer migrieren, kann der private Schlüssel des Berichtsserver-Diensts die Sperre des symmetrischen Schlüssels nicht mehr aufheben. Für den Zugriff auf den symmetrischen Schlüssel verschlüsseln Sie den symmetrischen Schlüssel unter Verwendung des privaten Schlüssels der neuen Identität des Berichtsserver-Diensts erneut. Die Wiederherstellung des symmetrischen Schlüssels ist das Verfahren, in dem die erneute Verschlüsselung erfolgt.  
  
 Sie sollten einen symmetrischen Schlüssel nur dann wiederherstellen, wenn es derselbe Schlüssel ist, der momentan zum Verschlüsseln und Entschlüsseln von Daten in der Berichtsserver-Datenbank verwendet wird. Wenn Sie einen symmetrischen Schlüssel wiederherstellen, der ungültig ist, sind Sie nicht mehr in der Lage, auf sensible Daten zuzugreifen. In diesem Fall müssen Sie den Schlüssel löschen und erneut erstellen.  
  
> [!IMPORTANT]  
>  Das Löschen und Neuerstellen des symmetrischen Schlüssels kann nicht umgekehrt oder rückgängig gemacht werden. Das Löschen oder Neuerstellen des Schlüssels kann sich erheblich auf die aktuelle Installation auswirken. Wenn Sie den Schlüssel löschen, werden alle vorhandenen, durch den symmetrischen Schlüssel verschlüsselten Daten ebenfalls gelöscht. Zu den gelöschten Daten zählen Verbindungszeichenfolgen zu externen Berichtsdatenquellen, gespeicherte Verbindungszeichenfolgen und einige Abonnementinformationen.  
  
 Um diese Seite zu öffnen, starten die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager, und klicken Sie auf den Link im Navigationsbereich. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Tastatur  
 **Sicherung**  
 Kopiert den symmetrischen Schlüssel in eine von Ihnen angegebene Datei. Der symmetrische Schlüssel wird nie als Nur-Text-Datei gespeichert. Sie müssen ein Kennwort eingeben, um die Datei zu schützen.  
  
 **Restore**  
 Wendet eine zuvor gespeicherte Kopie des symmetrischen Schlüssels auf die Berichtsserver-Datenbank an. Sie müssen ein Kennwort angeben, um die Dateisperre aufzuheben.  
  
 Die vorherige Kopie des symmetrischen Schlüssels für die Berichtsserverinstanz, mit der Sie gerade verbunden sind, wird von der wiederhergestellten Version überschrieben. Nachdem Sie den symmetrischen Schlüssel wiederhergestellt haben, müssen Sie alle Berichtsserver initialisieren, die die Berichtsserver-Datenbank verwenden. Weitere Informationen zur Initialisierung von Berichtsservern finden Sie unter [Initialisieren eines Berichtsservers &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md).  
  
 **Änderung**  
 Erstellt den symmetrischen Schlüssel neu und verschlüsselt alle verschlüsselten Werte in der Berichtsserver-Datenbank neu. Beenden Sie den Berichtsserver-Dienst, bevor Sie den symmetrischen Schlüssel neu erstellen.  
  
 Im Falle einer Bereitstellung für horizontales Skalieren werden alle Kopien des symmetrischen Schlüssels durch aktuellere Versionen ersetzt. Bevor Sie den symmetrischen Schlüssel ändern, müssen Sie die Liste mit den Servern prüfen, die der Bereitstellung für horizontales Skalieren hinzugefügt werden, um zu verifizieren, ob nur gültige Berichtsserverinstanzen Zugriff auf den neuen Schlüssel erhalten. Die Server, die Teil einer Bereitstellung für horizontales Skalieren sind, sind auf der Seite **Bereitstellung für horizontales Skalieren** aufgeführt. Beenden Sie den Dienst auf jedem Berichtsserver, bevor Sie den Schlüssel neu erstellen.  
  
 Beachten Sie, dass die erneute Generierung des symmetrischen Schlüssels bei vielen Datenquellen und Abonnements ein langer Prozess sein kann.  
  
 **Delete**  
 Löscht den symmetrischen Schlüssel und den gesamten verschlüsselten Inhalt, einschließlich Verbindungszeichenfolgen und gespeicherten Anmeldeinformationen. Sie sollten den symmetrischen Schlüssel nur dann löschen, wenn Sie ihn nicht wiederherstellen können.  
  
 Sobald Sie den symmetrischen Schlüssel gelöscht haben, müssen Sie die fehlenden Verbindungszeichenfolgen und gespeicherten Anmeldeinformationen in den Berichten sowie die freigegebenen Datenquellen, die diese Werte nicht mehr enthalten, erneut eingeben. Sie müssen auch alle Abonnements aktualisieren, die Übermittlungserweiterungen verwenden, die verschlüsselte Daten speichern. Dies umfasst die Dateifreigabe-Übermittlungserweiterung sowie alle Drittanbieter-Übermittlungserweiterungen, die einen verschlüsselten Wert verwenden.  
  
 Es gibt keinen automatischen Vorgang zum Aktualisieren dieser Informationen. Jeder Bericht, jedes Abonnement und jede freigegebene Datenquelle, die gespeicherte Anmeldeinformationen und Verbindungszeichenfolgen verwendet, muss aktualisiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Sichern und Wiederherstellen von Reporting Services-Verschlüsselungsschlüsseln](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Löschen und erneutes Erstellen von Verschlüsselungsschlüsseln &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Initialisieren eines Berichtsservers (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Speichern verschlüsselter Berichtsserverdaten &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  
