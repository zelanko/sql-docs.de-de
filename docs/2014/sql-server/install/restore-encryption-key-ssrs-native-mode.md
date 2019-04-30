---
title: Wiederherstellen von Verschlüsselungsschlüsseln (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.restoreencryptionkey.F1
ms.assetid: 11ce51e5-f5d4-40b6-88d8-9360fb50e66c
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9e85f9c17a28ba5c416bcab4853af9bdd823611f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63126926"
---
# <a name="restore-encryption-key-ssrs-native-mode"></a>Wiederherstellen von Verschlüsselungsschlüsseln (einheitlicher SSRS-Modus)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet einen Verschlüsselungsschlüssel, um sensible Daten zu sichern, die in der Berichtsserver-Datenbank gespeichert werden. Um einen ununterbrochenen Zugriff auf verschlüsselte Daten sicherzustellen, ist es wichtig, eine Sicherung des Verschlüsselungsschlüssels vorzunehmen für den Fall, dass Sie diesen später aufgrund von Änderungen im Dienstkonto oder im Rahmen einer geplanten Migration wiederherstellen müssen. Dieses Thema bietet eine Übersicht darüber, wie mithilfe des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Managers Schlüssel wiederhergestellt werden können.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Zum Wiederherstellen des Schlüssels müssen Sie zuvor eine Sicherungskopie des Schlüssels in eine kennwortgeschützte Datei gespeichert haben. Während der Wiederherstellung des Schlüssels ersetzt der Berichtsserver einen vorhandenen Schlüssel durch den Schlüssel in der kennwortgeschützten Datei. Der in dieser Datei gespeicherte Schlüssel muss mit dem Schlüssel identisch sein, der zum Entschlüsseln und Verschlüsseln von Daten verwendet wird.  
  
 Um zu überprüfen, ob Sie einen gültigen Schlüssel wiederhergestellt haben, zeigen Sie im Berichts-Manager Abonnements oder Berichte mit einer Datenquelle an, die gespeicherte Anmeldeinformationen verwendet. Wenn beim Öffnen einer Abonnementdefinitionsseite der Fehler "Der Berichtsserver kann nicht auf verschlüsselte Daten zugreifen" angezeigt wird, oder wenn Sie beim Öffnen eines Berichts, der zuvor gespeicherte Anmeldeinformationen für die Berichtsdatenquelle verwendet hat, zur Eingabe der Anmeldeinformationen aufgefordert werden, haben Sie einen ungültigen Schlüssel wiederhergestellt.  
  
 Wenn Sie einen ungültigen Schlüssel wiederherstellen, der sich von dem Schlüssel zum Verschlüsseln von Daten unterscheidet, können momentan in der Berichtsserver-Datenbank gespeicherte Daten nicht entschlüsselt werden. Falls Sie einen ungültigen Schlüssel wiederherstellen, sollten Sie unverzüglich eine Sicherungskopie des richtigen Schlüssels wiederherstellen, sofern verfügbar. Wenn Sie keine Sicherungskopie des Schlüssels, mit dem die Daten verschlüsselt wurden, vorliegen haben, müssen Sie alle verschlüsselten Daten löschen. Klicken Sie auf der Seite **Verschlüsselungsschlüssel** auf die Schaltfläche [Löschen](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md) , um diesen Schritt auszuführen. Nach dem Löschen des verschlüsselten Inhalts müssen Sie alle Abonnements manuell aktualisieren und alle gespeicherten Anmeldeinformationen, die für Berichte und datengesteuerte Abonnements auf dem Berichtsserver definiert wurden, erneut festlegen.  
  
## <a name="restore-encryption-key-dialog"></a>Verschlüsselungsschlüssel wiederherstellen (Dialogfeld)  
 Informationen zum Aufrufen der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 Klicken Sie im Navigationsbereich des **-Konfigurations-Managers auf** Verschlüsselungsschlüssel [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und anschließend auf **Wiederherstellen**, um das Dialogfeld Verschlüsselungsschlüssel wiederherstellen zu öffnen. Dieses Dialogfeld wird auch angezeigt, wenn Sie das Dienstkonto auf der Dienstkontoseite im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager aktualisieren. Weitere Informationen zu  
  
## <a name="options"></a>Optionen  
 **Dateispeicherort**  
 Wählen Sie die kennwortgeschützte Datei aus, die eine Kopie des symmetrischen Schlüssels enthält. Standardmäßig wird die Dateinamenerweiterung SNK verwendet.  
  
 **Kennwort**  
 Geben Sie das Kennwort zum Entsperren der Datei ein. Nur für Benutzer, die wissen, dass das Kennwort den Schlüssel wiederherstellen kann. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet eine Richtlinie für sichere Kennwörter. Kennwörter müssen aus mindestens 8 Zeichen bestehen und eine Kombination aus Buchstaben (in Groß- und Kleinschreibung) sowie Zahlen und mindestens ein Symbol enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Sichern und Wiederherstellen von Reporting Services-Verschlüsselungsschlüsseln](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Löschen und erneutes Erstellen von Verschlüsselungsschlüsseln &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Initialisieren eines Berichtsservers (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [SSRS-Verschlüsselungsschlüssel: Speichern verschlüsselter Berichtsserverdaten](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Verschlüsselungsschlüssel &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
