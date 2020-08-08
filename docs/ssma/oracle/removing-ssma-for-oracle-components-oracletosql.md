---
title: Entfernen von SSMA für Oracle-Komponenten (oracledesql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Uninstalling the Extension Pack
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 4fbac66cfd7cf549a6321534901ca8a33900f986
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87933151"
---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>Entfernen von SSMA-Komponenten für Oracle (OracleToSQL)
Wenn Sie die Migration von Datenbanken von Oracle zu abgeschlossen haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie die SSMA-Komponenten deinstallieren. Sie können die Client Komponenten jederzeit deinstallieren. Sie sollten das Erweiterungspaket jedoch nicht von deinstallieren, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es sei denn, die migrierten Datenbanken verwenden keine Funktionen mehr im **ssma_oracle** Schema der **sysdb** -Datenbank.  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>Deinstallieren von SSMA für Oracle Client  
Sie können SSMA **mithilfe der**Option Software deinstallieren.  
  
**So deinstallieren Sie SSMA**  
  
1.  Öffnen Sie in der Systemsteuerung **Programme hinzufügen/entfernen**.  
  
2.  Wählen Sie ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für Oracle aus**, und klicken Sie dann auf **Entfernen**.  
  
3.  Um zu bestätigen, dass Sie SSMA deinstallieren möchten, klicken Sie auf **Ja**.  
  
## <a name="uninstalling-the-extension-pack"></a>Deinstallieren des Erweiterungspakets  
Wenn Sie sicher sind, dass die migrierten Datenbanken keine Objekte im **sysdb. ssma_oracle** -Schema verwenden, können Sie das Erweiterungspaket **mithilfe der**Option "Software" entfernen.  
  
**So deinstallieren Sie das Erweiterungspaket**  
  
1.  Öffnen Sie in der Systemsteuerung **Programme hinzufügen/entfernen**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für das Oracle-Erweiterungspaket aus**, und klicken Sie dann auf **Entfernen**.  
  
3.  Um zu bestätigen, dass Sie das Erweiterungspaket deinstallieren möchten, klicken Sie auf **Ja**.  
  
4.  Wählen Sie auf der Seite Instanzen mit Dienstprogrammen Daten Bank Skripts eine Instanz aus, und klicken Sie dann auf **weiter**.  
  
5.  Wählen Sie auf der Seite Verbindungsparameter die Authentifizierungsmethode aus, und klicken Sie dann auf **weiter**.  
  
    Die Windows-Authentifizierung verwendet Ihre Windows-Anmelde Informationen, um sich bei der Instanz von anzumelden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung auswählen, müssen Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Namen und ein Kennwort eingeben.  
  
6.  Klicken Sie auf der Seite Vorgang abgeschlossen auf **OK**.  
  
7.  Klicken Sie auf der Seite Fertigstellen **auf beenden.**  
  
Nach der Deinstallation können Sie überprüfen, ob Objekte im **sysdb. ssma_oracle** -Schema und möglicherweise die gesamte **sysdb** -Datenbank mithilfe von entfernt wurden [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Wenn Sie jedoch andere SSMA-Produkte verwenden, verwenden Sie auch die **sysdb** -Datenbank. Wenn die Datenbank vorhanden ist und Sie sicher sind, dass keine anderen Datenbanken auf Objekte in dieser Datenbank verweisen, können Sie die Datenbank trennen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für Oracle Client &#40;oracleto SQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Installieren von SSMA-Komponenten auf SQL Server &#40;oracledesql-&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  
