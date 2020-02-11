---
title: Entfernen der SSMA für MySQL-Komponenten (mysqldesql) | Microsoft-Dokumentation
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
ms.openlocfilehash: 3a5d6d1234cc294cc8e8cdd163ce8a9bd6ac3e3f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67929386"
---
# <a name="removing-the-ssma-for-mysql-components-mysqltosql"></a>Entfernen der SSMA-Komponenten für MySQL (MySqlToSql)
Wenn Sie die Migration von Datenbanken von MySQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu abgeschlossen haben, können Sie die SSMA-Komponenten deinstallieren. Sie können die Client Komponenten jederzeit deinstallieren. Wenn Sie jedoch das Erweiterungspaket von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deinstallieren, unterstützt SSMA nicht mehr die Migration von Daten aus MySQL in die Zieldatenbank (SQL Server/SQL Azure) mithilfe der Server seitigen Daten Migrations-Engine.  
  
## <a name="uninstalling-the-ssma-for-mysql-client"></a>Deinstallieren des SSMA für MySQL-Clients  
Sie können SSMA **mithilfe der**Option Software deinstallieren.  
  
**So deinstallieren Sie SSMA**  
  
1.  Öffnen Sie in der Systemsteuerung das Modul **Software**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für MySQL aus**, und klicken Sie dann auf **Entfernen**.  
  
3.  Um zu bestätigen, dass Sie SSMA deinstallieren möchten, klicken Sie auf **Ja**.  
  
## <a name="uninstalling-the-extension-pack"></a>Deinstallieren des Erweiterungspakets  
Sie können das Erweiterungs **Paket mithilfe der**Option "Software" entfernen.  
  
**So deinstallieren Sie das Erweiterungspaket**  
  
1.  Öffnen Sie in der Systemsteuerung das Modul **Software**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für das MySQL-Erweiterungspaket aus**, und klicken Sie dann auf **Entfernen**.  
  
3.  Um zu bestätigen, dass Sie das Erweiterungspaket deinstallieren möchten, klicken Sie auf **Ja**.  
  
4.  Wählen Sie auf der Seite Instanzen mit Dienstprogrammen Daten Bank Skripts eine Instanz aus, und klicken Sie dann auf **weiter**.  
  
5.  Wählen Sie auf der Seite Verbindungsparameter die Authentifizierungsmethode aus, und klicken Sie dann auf **weiter**.  
  
    Die Windows-Authentifizierung verwendet Ihre Windows-Anmelde Informationen, um sich bei der Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von anzumelden. Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung auswählen, müssen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Anmelde Namen und ein Kennwort eingeben.  
  
6.  Klicken Sie auf der Seite Vorgang abgeschlossen auf **OK**.  
  
7.  Klicken Sie auf der Seite Fertigstellen **auf beenden.**  
  
Nachdem die Installation abgeschlossen ist, können Sie überprüfen, ob Objekte im **sysdb. ssma_MySQL** -Schema und möglicherweise die gesamte **sysdb** -Datenbank mithilfe [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]von entfernt wurden. Wenn Sie jedoch andere SSMA-Produkte verwenden, verwenden Sie auch die **sysdb** -Datenbank. Wenn die Datenbank vorhanden ist und Sie sicher sind, dass keine anderen Datenbanken auf die Objekte in dieser Datenbank verweisen, können Sie die Datenbank trennen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für MySQL-Client &#40;mysqlto SQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Installieren von SSMA-Komponenten für SQL Server](installing-ssma-components-on-sql-server-mysqltosql.md)  
  
