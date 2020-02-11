---
title: Entfernen von SSMA für Sybase-Komponenten (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: aec09593-17d9-4ec2-ac56-3cd8851406fd
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0c76b6b2e4e5295bf7db2d7857a73223fc6f8c7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028641"
---
# <a name="removing-ssma-for-sybase-components-sybasetosql"></a>Entfernen von SSMA-Komponenten für Sybase (SybaseToSQL)
Wenn Sie die Migration von Datenbanken von Sybase Adaptive Server Enterprise (ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) zu abgeschlossen haben, können Sie SSMA-Komponenten deinstallieren. Sie können die Client Komponenten jederzeit deinstallieren. Sie sollten das Erweiterungspaket jedoch nicht von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deinstallieren, es sei denn, Sie sind sicher, dass die migrierten Datenbanken nicht mehr Funktionen im **ssma_syb** Schema der **sysdb** -Datenbank verwenden.  
  
## <a name="uninstalling-the-ssma-for-sybase-client"></a>Deinstallieren von SSMA für den Sybase-Client  
Sie können SSMA **mithilfe der**Option Software deinstallieren.  
  
**So deinstallieren Sie SSMA**  
  
1.  Öffnen Sie in der Systemsteuerung das Modul **Software**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für Sybase aus**, und klicken Sie dann auf **Entfernen**.  
  
3.  Um zu bestätigen, dass Sie SSMA deinstallieren möchten, klicken Sie auf **Ja**.  
  
## <a name="uninstalling-the-extension-pack"></a>Deinstallieren des Erweiterungspakets  
Wenn Sie sicher sind, dass die migrierten Datenbanken keine Objekte im **sysdb. ssma_syb** -Schema verwenden, können Sie das Erweiterungspaket **mithilfe der**Option "Software" entfernen.  
  
So deinstallieren Sie das Erweiterungspaket  
  
1.  Öffnen Sie in der Systemsteuerung das Modul **Software**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für das Sybase-Erweiterungspaket aus**, und klicken Sie dann auf **Entfernen**.  
  
3.  Um zu bestätigen, dass Sie das Erweiterungspaket deinstallieren möchten, klicken Sie auf **Ja**.  
  
4.  Klicken Sie auf der Seite Instanzen mit Daten Bank Skripts auf **weiter**.  
  
5.  Wählen Sie auf der Seite Verbindungsparameter die Authentifizierungsmethode aus, und klicken Sie dann auf **weiter**.  
  
    Die Windows-Authentifizierung verwendet Ihre Windows-Anmelde Informationen, um sich bei der Instanz von SQL Server anzumelden. Wenn Sie SQL Server Authentifizierung auswählen, müssen Sie einen SQL Server Anmelde Namen und ein Kennwort eingeben.  
  
6.  Klicken Sie auf der Seite Vorgang abgeschlossen auf **OK**.  
  
7.  Klicken Sie auf der Seite Fertigstellen **auf beenden.**  
  
Nachdem Sie deinstalliert haben, können Sie überprüfen, ob das **sysdb. ssma_syb** -Schema und möglicherweise die gesamte **sysdb** -Datenbank [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]mithilfe von entfernt wurde. Wenn Sie jedoch andere SSMA-Produkte verwenden, verwenden Sie auch die **sysdb** -Datenbank. Wenn die Datenbank vorhanden ist und Sie sicher sind, dass keine anderen Datenbanken auf Objekte in dieser Datenbank verweisen, können Sie die Datenbank trennen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für den Sybase-Client &#40;sybasedesql&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Installieren von SSMA-Komponenten auf SQL Server &#40;sybasedesql-&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
  
