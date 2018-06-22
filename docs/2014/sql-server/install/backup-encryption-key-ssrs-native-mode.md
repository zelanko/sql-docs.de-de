---
title: Sichern von Verschlüsselungsschlüsseln (SSRS-Modus) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.backupencryptionkey.F1
ms.assetid: eb8c82be-323b-4d86-ab10-c1bf69a4abe3
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: a59510ae92160286983f4fa225fad8e3a4cb6af0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050247"
---
# <a name="backup-encryption-key-ssrs-native-mode"></a>Sichern von Verschlüsselungsschlüsseln (einheitlicher SSRS-Modus)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet einen Verschlüsselungsschlüssel Sichern von sensiblen Daten, die in der Berichtsserver-Datenbank gespeichert ist. Mit dem gesicherten Verschlüsselungsschlüssel wird der Zugriff auf verschlüsselte Verbindungszeichenfolgen und Anmeldeinformationen sichergestellt. Sie müssen über eine Sicherungskopie dieses Schlüssels verfügen, wenn Sie die Berichtsserver-Datenbank auf einen anderen Computer verschieben möchten oder wenn Sie den Benutzernamen oder das Kennwort für das Berichtsserver-Dienstkonto ändern möchten. Beide Vorgänge erfordern eine Wiederherstellung des Schlüssels anhand einer zuvor erstellten Sicherungskopie.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Um das Dialogfeld Sicherungsverschlüsselungsschlüssel zu öffnen, klicken Sie auf **Verschlüsselungsschlüssel** im Navigationsbereich von der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager, und klicken Sie dann auf **Sicherung**. Dieses Dialogfeld wird auch angezeigt, bei der Aktualisierung des Dienstkontos mithilfe der Seite "Dienstkonto" in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Weitere Informationen zu den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Tastatur  
 **Dateispeicherort**  
 Geben Sie einen Dateinamen und Speicherort für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] für den symmetrischen Schlüssel. Der symmetrische Schlüssel wird nie als Nur-Text-Datei gespeichert. Sie müssen ein Kennwort eingeben, um die Datei zu schützen.  
  
 **Kennwort**  
 Geben Sie ein Kennwort ein, das die Datei vor nicht autorisiertem Zugriff schützt. Benutzer, denen das Kennwort nicht bekannt ist, können den in der Datei enthaltenen Schlüssel nicht wiederherstellen. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Erzwingt eine Richtlinie für sichere Kennwörter. Kennwörter müssen aus mindestens 8 Zeichen bestehen und eine Kombination aus Buchstaben (in Groß- und Kleinschreibung) sowie Zahlen und mindestens ein Symbol enthalten.  
  
 **Kennwort bestätigen**  
 Geben Sie das Kennwort erneut ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurationsmanager-F1-Hilfethemen &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Sichern und Wiederherstellen von Reporting Services-Verschlüsselungsschlüsseln](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Löschen und erneutes Erstellen von Verschlüsselungsschlüsseln &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Initialisieren eines Berichtsservers (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [SSRS-Verschlüsselungsschlüssel: Speichern verschlüsselter Berichtsserverdaten](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Verschlüsselungsschlüssel &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  