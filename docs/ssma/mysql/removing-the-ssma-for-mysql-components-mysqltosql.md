---
title: Entfernen von SSMA für MySQL (MySQLToSql))-Komponenten | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Uninstalling, Extension pack
- Uninstalling, SSMA for MySQL client
ms.assetid: 87cdbd49-a0c9-4b00-8a93-34188b18d11a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ad23c4add9b6e7ea9999a434261a95282f129935
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47604849"
---
# <a name="removing-the-ssma-for-mysql-components-mysqltosql"></a>Entfernen der SSMA-Komponenten für MySQL (MySqlToSql)
Nach Abschluss des Migrieren von Datenbanken aus MySQL in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], empfiehlt es sich um SSMA-Komponenten zu deinstallieren. Sie können die Clientkomponenten jederzeit deinstallieren. Allerdings bei der Deinstallation das Erweiterungspaket aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , klicken Sie dann SSMA wird Migration von Daten aus MySQL in die Zieldatenbank (SQL Server/SQL Azure), verwenden die Server-Seite-Migration-Engine nicht mehr unterstützt.  
  
## <a name="uninstalling-the-ssma-for-mysql-client"></a>Deinstallieren von SSMA für MySQL-Client  
Sie können mit SSMA Deinstallieren **Software**.  
  
**So deinstallieren Sie SSMA**  
  
1.  Öffnen Sie in der Systemsteuerung **Software**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für MySQL**, und klicken Sie dann auf **entfernen**.  
  
3.  Um zu bestätigen, dass Sie SSMA deinstallieren möchten, klicken Sie auf **Ja**.  
  
## <a name="uninstalling-the-extension-pack"></a>Deinstallieren der Erweiterung Packs  
Sie können mit dem Erweiterungspaket entfernen **Software**.  
  
**So deinstallieren Sie die Erweiterung pack**  
  
1.  Öffnen Sie in der Systemsteuerung **Software**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für MySQL-Erweiterungspaket**, und klicken Sie dann auf **entfernen**.  
  
3.  Um zu bestätigen, dass Sie das Pack für die Erweiterung deinstallieren möchten, klicken Sie auf **Ja**.  
  
4.  Klicken Sie auf die Instanzen mit Hilfsprogrammen Datenbankskripts-Seite, wählen Sie eine Instanz, und klicken Sie dann auf **Weiter**.  
  
5.  Klicken Sie auf der Seite Verbindungsparameter, wählen Sie die Authentifizierungsmethode aus, und klicken Sie dann auf **Weiter**.  
  
    Windows-Authentifizierung wird Ihre Windows-Anmeldeinformationen verwenden, um zu versuchen, melden Sie sich mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bei Auswahl von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung, geben Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldename und Kennwort.  
  
6.  Klicken Sie auf der Seite abgeschlossen auf **OK**.  
  
7.  Klicken Sie auf der Seite zum Fertigstellen auf **beenden**.  
  
Nachdem die Deinstallation abgeschlossen ist, können Sie bestätigen, die Objekte der **sysdb.ssma_MySQL** Schema und möglicherweise die gesamte **Sysdb** Datenbank, mit mehr [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Jedoch wenn Sie andere SSMA-Produkte verwenden, sie auch verwenden, die **Sysdb** Datenbank. Wenn die Datenbank vorhanden ist, und Sie Sie sicher sind, dass keine anderen Datenbanken auf die Objekte in dieser Datenbank verweisen, können Sie die Datenbank trennen.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für MySQL-Client &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Installing SSMA Components on SQL Server (Installieren von SSMA-Komponenten auf SQL Server)](installing-ssma-components-on-sql-server-mysqltosql.md)  
  
