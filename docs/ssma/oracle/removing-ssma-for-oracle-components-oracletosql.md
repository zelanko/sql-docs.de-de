---
title: Removing SSMA for Oracle Components (OracleToSQL) entfernen | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Uninstalling the Extension Pack
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: da54f9fc21b74be790ac86c9690738b71fd3e1c7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62628545"
---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>Entfernen von SSMA-Komponenten für Oracle (OracleToSQL)
Nach Abschluss des Migrieren von Datenbanken aus Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], empfiehlt es sich um SSMA-Komponenten zu deinstallieren. Sie können die Clientkomponenten jederzeit deinstallieren. Allerdings sollten Sie nicht das Erweiterungspaket aus Deinstallieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es sei denn, Ihre migrierten Datenbanken nicht mehr Funktionen in der **Ssma_oracle** Schema der **Sysdb** Datenbank.  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>Deinstallieren von SSMA für Oracle-Client  
Sie können mit SSMA Deinstallieren **Software**.  
  
**So deinstallieren Sie SSMA**  
  
1.  Öffnen Sie in der Systemsteuerung **Software**.  
  
2.  Wählen Sie  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für Oracle**, und klicken Sie dann auf **entfernen**.  
  
3.  Um zu bestätigen, dass Sie SSMA deinstallieren möchten, klicken Sie auf **Ja**.  
  
## <a name="uninstalling-the-extension-pack"></a>Deinstallieren der Erweiterung Packs  
Möchten Sie sicher, dass Ihre migrierten Datenbanken verwenden Sie nicht Objekte in der **sysdb.ssma_oracle** Schema, Sie können mit dem Erweiterungspaket entfernen **Programme hinzufügen oder entfernen Sie**.  
  
**So deinstallieren Sie die Erweiterung pack**  
  
1.  Öffnen Sie in der Systemsteuerung **Software**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für Oracle-Erweiterungspaket**, und klicken Sie dann auf **entfernen**.  
  
3.  Um zu bestätigen, dass Sie das Pack für die Erweiterung deinstallieren möchten, klicken Sie auf **Ja**.  
  
4.  Klicken Sie auf die Instanzen mit Hilfsprogrammen Datenbankskripts-Seite, wählen Sie eine Instanz, und klicken Sie dann auf **Weiter**.  
  
5.  Klicken Sie auf der Seite Verbindungsparameter, wählen Sie die Authentifizierungsmethode aus, und klicken Sie dann auf **Weiter**.  
  
    Windows-Authentifizierung wird Ihre Windows-Anmeldeinformationen verwenden, um zu versuchen, melden Sie sich mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bei Auswahl von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung, geben Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldename und Kennwort.  
  
6.  Klicken Sie auf der Seite abgeschlossen auf **OK**.  
  
7.  Klicken Sie auf der Seite zum Fertigstellen auf **beenden**.  
  
Nach der Deinstallation ist, können Sie bestätigen, die Objekte der **sysdb.ssma_oracle** Schema und möglicherweise die gesamte **Sysdb** Datenbank, mit mehr [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Jedoch wenn Sie andere SSMA-Produkte verwenden, sie auch verwenden, die **Sysdb** Datenbank. Wenn die Datenbank vorhanden ist, und Sie Sie sicher sind, dass keine anderen Datenbanken Objekte in dieser Datenbank zu verweisen, können Sie die Datenbank trennen.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für Oracle-Client &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Installieren von SSMA-Komponenten auf SQLServer &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  
