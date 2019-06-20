---
title: Removing SSMA for Sybase Components (SybaseToSQL) entfernen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: aec09593-17d9-4ec2-ac56-3cd8851406fd
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b3cebc9bb82778390716212fd3b5ae1bf800d3d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62667932"
---
# <a name="removing-ssma-for-sybase-components-sybasetosql"></a>Entfernen von SSMA-Komponenten für Sybase (SybaseToSQL)
Nach Abschluss des Migrieren von Datenbanken von Sybase Adaptive Server Enterprise (ASE) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], empfiehlt es sich um SSMA-Komponenten zu deinstallieren. Können Sie die Client-Komponenten zu einem beliebigen Zeitpunkt deinstallieren, aber Sie sollten nicht deinstallieren, das Erweiterungspaket aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wenn Sie sicher sind, verwenden Sie die migrierten Datenbanken nicht mehr Funktionen in der **Ssma_syb** Schema der **Sysdb** Datenbank.  
  
## <a name="uninstalling-the-ssma-for-sybase-client"></a>Deinstallieren von SSMA für Sybase-Client  
Sie können mit SSMA Deinstallieren **Software**.  
  
**So deinstallieren Sie SSMA**  
  
1.  Öffnen Sie in der Systemsteuerung **Software**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für Sybase**, und klicken Sie dann auf **entfernen**.  
  
3.  Um zu bestätigen, dass Sie SSMA deinstallieren möchten, klicken Sie auf **Ja**.  
  
## <a name="uninstalling-the-extension-pack"></a>Deinstallieren der Erweiterung Packs  
Möchten Sie sicher, dass Ihre migrierten Datenbanken verwenden Sie nicht Objekte in der **sysdb.ssma_syb** Schema, Sie können mit dem Erweiterungspaket entfernen **Programme hinzufügen oder entfernen Sie**.  
  
So deinstallieren Sie die Erweiterung pack  
  
1.  Öffnen Sie in der Systemsteuerung **Software**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für Sybase-Erweiterungspaket**, und klicken Sie dann auf **entfernen**.  
  
3.  Um zu bestätigen, dass Sie das Pack für die Erweiterung deinstallieren möchten, klicken Sie auf **Ja**.  
  
4.  Klicken Sie auf die Instanzen mit Hilfsprogrammen Datenbankskripts-Seite, auf **Weiter**.  
  
5.  Klicken Sie auf der Seite Verbindungsparameter, wählen Sie die Authentifizierungsmethode aus, und klicken Sie dann auf **Weiter**.  
  
    Windows-Authentifizierung wird Ihre Windows-Anmeldeinformationen verwenden, um zu versuchen, melden Sie sich mit der Instanz von SQL Server. Wenn Sie SQL Server-Authentifizierung auswählen, müssen Sie einen SQL-Anmeldenamen und ein Kennwort eingeben.  
  
6.  Klicken Sie auf der Seite abgeschlossen auf **OK**.  
  
7.  Klicken Sie auf der Seite zum Fertigstellen auf **beenden**.  
  
Nach der Deinstallation können Sie bestätigen, dass die **sysdb.ssma_syb** Schema und möglicherweise die gesamte **Sysdb** Datenbank, mit mehr [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Jedoch wenn Sie andere SSMA-Produkte verwenden, sie auch verwenden, die **Sysdb** Datenbank. Wenn die Datenbank vorhanden ist, und Sie Sie sicher sind, dass keine anderen Datenbanken Objekte in dieser Datenbank zu verweisen, können Sie die Datenbank trennen.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für Sybase Client &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Installieren von SSMA-Komponenten auf SQLServer &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
  
