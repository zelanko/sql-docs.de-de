---
title: Exportieren und Importieren von DQS-Wissensdatenbanken mit dqsinstaller. exe
description: Erfahren Sie, wie Sie dqsinstaller. exe zum Exportieren und Importieren von DQS-Wissensdatenbanken für SQL Server Data Quality Services (DQS) verwenden.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8234c63b-a018-4e55-8184-9a6bdf03274d
author: swinarko
ms.author: sawinark
ms.openlocfilehash: ae87b9daebdef6b81c4d96abc253820cf7cb8228
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75558143"
---
# <a name="export-and-import-dqs-knowledge-bases-using-dqsinstallerexe"></a>Export und Importieren von DQS-Wissensdatenbanken mit DQSInstaller.exe

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Bei einer vorhandenen DQS-Installation können Sie alle Wissensdatenbanken auf dem [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] gleichzeitig in eine DQS-Sicherungsdatei (DQSB) exportieren und dann später die DQSB-Datei verwenden, um alle Wissensdatenbanken gleichzeitig auf einen anderen [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] zu importieren, indem Sie die Datei DQSInstaller.exe an der Eingabeaufforderung ausführen. Weitere Informationen zum Ausführen von DQSInstaller.exe von der Eingabeaufforderung finden Sie unter [Ausführen von „DQSInstaller.exe“ über Befehlszeile](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt) in [Ausführen von DQSInstaller.exe zum Abschließen der Installation von Data Quality Server](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
 Diese Funktion ermöglicht es Ihnen, sofort eine Sicherung *aller* Wissensdatenbanken in [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] durchzuführen, ohne jede Wissensdatenbank einzeln mithilfe des [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]in eine DQS-Datei exportieren zu müssen. Auf ähnliche Weise können Sie *alle* Wissensdatenbanken gleichzeitig aus der Sicherungsdatei in einen anderen [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] importieren, ohne jede Wissensdatenbank einzeln aus einer DQS-Datei mithilfe des [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]importieren zu müssen. Dies ist besonders nützlich beim Sichern und Wiederherstellen der Wissensdatenbanken, wenn Sie [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] auf einem Computer deinstallieren und dann auf einem anderen Computer neu installieren. Sie können ganz einfach alle Wissensdatenbanken in einer vorhandenen Installation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] in eine DQS-Sicherungsdatei (.dqsb) exportieren und dann alle Wissensdatenbanken aus der Sicherungsdatei importieren, nachdem Sie [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] auf einem anderen Computer installiert haben.  
  
##  <a name="export"></a>Exportieren von Wissensdatenbanken in eine dqsb-Datei  
 Sie können jederzeit alle Wissensdatenbanken aus dem vorhandenen [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] oder beim Deinstallieren von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]exportieren.  
  
-   Um alle Wissensdatenbanken aus einem [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] in eine DQS-Sicherungsdatei (.dqsb) zu exportieren, führen Sie DQSInstaller.exe mit dem `exportkbs` -Parameter von der Eingabeaufforderung, zusammen mit dem vollständigen Pfad und dem Dateinamen, wohin Sie die Wissensdatenbanken exportieren möchten, aus. Beispiel: Um alle Wissensdatenbanken in die Datei DQSBackup.dqsb auf Laufwerk C: zu exportieren:  
  
    ```  
    dqsinstaller.exe -exportkbs c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  Wenn der angegebene Dateiname bereits am festgelegten Speicherort vorhanden ist, werden Sie vom Installationsprogramm gefragt, ob die Datei überschrieben werden soll.  
  
-   Um alle Wissensdatenbanken bei der Deinstallation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]in eine DQS-Sicherungsdatei zu exportieren, führen Sie DQSInstaller.exe mit dem `uninstall` -Parameter von der Eingabeaufforderung, zusammen mit dem vollständigen Pfad und dem Dateinamen, wohin Sie die Wissensdatenbanken exportieren möchten, aus. Beispiel: Um alle Wissensdatenbanken in die Datei DQSBackup.dqsb auf Laufwerk C: zu exportieren und dann [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]zu deinstallieren:  
  
    ```  
    dqsinstaller.exe -uninstall c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  Wenn Sie beim Deinstallieren von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] von der Eingabeaufforderung unter Verwendung des `uninstall` -Parameters nicht den vollständigen Pfad und den Dateinamen der DQS-Sicherungsdatei angeben, wird eine Meldung mit den Hinweis angezeigt, dass alle Wissensdatenbanken gelöscht werden, und ermöglicht Ihnen auszuwählen, ob der Deinstallationsvorgang fortgesetzt werden soll.  
  
##  <a name="import"></a>Importieren von Wissensdatenbanken aus einer dqsb-Datei  
 Sie können alle Wissensdatenbanken aus einer DQS-Sicherungsdatei (DQSB-Format) importieren, nachdem Sie die [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] -Installation abgeschlossen haben. Um Wissensdatenbanken zu importieren, benötigen Sie eine gültige DQS-Sicherungsdatei (.dqsb).  
  
 Führen Sie DQSInstaller.exe mit dem `importkbs` -Parameter von der Eingabeaufforderung, zusammen mit dem vollständigen Pfad und dem Dateinamen, von wo Sie die Wissensdatenbanken importieren möchten, aus. Beispiel: Um alle Wissensdatenbanken aus der Datei DQSBackup.dqsb auf Laufwerk C: zu importieren:  
  
```  
dqsinstaller.exe -importkbs c:\DQSBackup.dqsb  
```  
  
 Wenn auf dem [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] Wissensdatenbanken mit dem gleichen Namen wie den zu importierenden vorhanden sind, wird an die Namen der importierten Wissensdatenbanken ein Unterstrich (_) angefügt, gefolgt von einem ganzzahligen Wert, beginnend mit 1. Wenn die Domäne „Firmenname“ z. B. doppelt vorkommt, ist der importierte Domänenname „Firmenname_1“.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von "dqsinstaller. exe" zum Abschluss der Installation von Data Quality Server](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)   
 [Installieren von Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Exportieren einer Wissensdatenbank in eine DQS-Datei](../../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)   
 [Importieren einer Wissensdatenbank aus einer DQS-Datei](../../data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)  
  
  
