---
description: Entfernen der SSMA-Komponenten für MySQL (MySqlToSql)
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 3a7932d79c414fb79dfc29074c1b8a5888c85827
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418506"
---
# <a name="removing-the-ssma-for-mysql-components-mysqltosql"></a>Entfernen der SSMA-Komponenten für MySQL (MySqlToSql)
Wenn Sie die Migration von Datenbanken von MySQL zu abgeschlossen haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie die SSMA-Komponenten deinstallieren. Sie können die Client Komponenten jederzeit deinstallieren. Wenn Sie jedoch das Erweiterungspaket von deinstallieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , unterstützt SSMA nicht mehr die Migration von Daten aus MySQL in die Zieldatenbank (SQL Server/SQL Azure) mithilfe der Server seitigen Daten Migrations-Engine.  
  
## <a name="uninstalling-the-ssma-for-mysql-client"></a>Deinstallieren des SSMA für MySQL-Clients  
Sie können SSMA **mithilfe der**Option Software deinstallieren.  
  
**So deinstallieren Sie SSMA**  
  
1.  Öffnen Sie in der Systemsteuerung **Programme hinzufügen/entfernen**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für MySQL aus**, und klicken Sie dann auf **Entfernen**.  
  
3.  Um zu bestätigen, dass Sie SSMA deinstallieren möchten, klicken Sie auf **Ja**.  
  
## <a name="uninstalling-the-extension-pack"></a>Deinstallieren des Erweiterungspakets  
Sie können das Erweiterungs **Paket mithilfe der**Option "Software" entfernen.  
  
**So deinstallieren Sie das Erweiterungspaket**  
  
1.  Öffnen Sie in der Systemsteuerung **Programme hinzufügen/entfernen**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für das MySQL-Erweiterungspaket aus**, und klicken Sie dann auf **Entfernen**.  
  
3.  Um zu bestätigen, dass Sie das Erweiterungspaket deinstallieren möchten, klicken Sie auf **Ja**.  
  
4.  Wählen Sie auf der Seite Instanzen mit Dienstprogrammen Daten Bank Skripts eine Instanz aus, und klicken Sie dann auf **weiter**.  
  
5.  Wählen Sie auf der Seite Verbindungsparameter die Authentifizierungsmethode aus, und klicken Sie dann auf **weiter**.  
  
    Die Windows-Authentifizierung verwendet Ihre Windows-Anmelde Informationen, um sich bei der Instanz von anzumelden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung auswählen, müssen Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Namen und ein Kennwort eingeben.  
  
6.  Klicken Sie auf der Seite Vorgang abgeschlossen auf **OK**.  
  
7.  Klicken Sie auf der Seite Fertigstellen **auf beenden.**  
  
Nachdem die Installation abgeschlossen ist, können Sie überprüfen, ob Objekte im **sysdb. ssma_MySQL** -Schema und möglicherweise die gesamte **sysdb** -Datenbank mithilfe von entfernt wurden [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Wenn Sie jedoch andere SSMA-Produkte verwenden, verwenden Sie auch die **sysdb** -Datenbank. Wenn die Datenbank vorhanden ist und Sie sicher sind, dass keine anderen Datenbanken auf die Objekte in dieser Datenbank verweisen, können Sie die Datenbank trennen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für MySQL-Client &#40;mysqlto SQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Installieren von SSMA-Komponenten für SQL Server](installing-ssma-components-on-sql-server-mysqltosql.md)  
  
