---
title: Installieren von SSMA-Komponenten auf SQL Server (mysqlto SQL) | Microsoft-Dokumentation
description: Installieren Sie Komponenten auf dem Server, auf dem SQL Server ausgeführt wird, um die Konvertierung von MySQL-Datenbanken mit SSMA einschließlich des SSMA-Erweiterungspakets und der MySQL-Anbieter
ms.prod: sql
ms.custom: ''
ms.date: 07/14/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- SSMA extension pack, Installation
ms.assetid: 6772d0c5-258f-4d7b-afb0-b5f810e71af1
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: a38808c64209edb094c986e63305707a0a834edb
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823668"
---
# <a name="installing-ssma-components-on-sql-server-mysqltosql"></a>Installieren von SSMA-Komponenten auf SQL Server (mysqlto SQL)

Zusätzlich zur Installation von SSMA müssen Sie auch Komponenten auf dem Computer installieren, auf dem ausgeführt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Zu diesen Komponenten gehören das SSMA-Erweiterungspaket, das die Datenmigration unterstützt, und MySQL-Anbieter, um die Server-zu-Server-Konnektivität zu ermöglichen.

## <a name="ssma-for-mysql-extension-pack"></a>SSMA für MySQL-Erweiterungspaket

Das SSMA-Erweiterungspaket fügt der angegebenen-Instanz eine Datenbank, **sysdb**, hinzu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Diese Datenbank enthält die Tabellen und gespeicherten Prozeduren, die zum Migrieren von Daten erforderlich sind.

Beim Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden von SSMA außerdem- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agentaufträge erstellt, wenn die serverseitige Daten Migrations-Engine zum Migrieren der Daten verwendet wird.

### <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor der Installation der SSMA für MySQL-Serverkomponenten unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sicher, dass der Computer die folgenden Anforderungen erfüllt:

- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder eine höhere Version.
- Die [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4.7.2 oder eine spätere Version. Sie können Sie über das [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882)abrufen.
- Den MySQL-Client Anbieter und die Konnektivität mit der MySQL-Datenbank, die Sie migrieren möchten. Sie können Anbieter aus dem MySQL-Produkt Medium oder der MySQL-Website installieren.
- Der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser-Dienst muss während der Installation ausgeführt werden. Diese wird verwendet, um eine Liste der Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Setup-Assistenten aufzufüllen. Sie können den- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Dienst nach der Installation deaktivieren.  

  > [!NOTE]
  > Wenn der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser-Dienst ausgeführt wird, im Setup aber immer noch keine Liste der Instanzen angezeigt wird, müssen Sie die Blockierung des UDP-Ports 1434 deaktivieren. Mit der Windows-Firewall können Sie den Port vorübergehend entsperren, oder Sie können die Windows-Firewall temporär deaktivieren. Möglicherweise müssen Sie die Antivirussoftware auch vorübergehend deaktivieren. Stellen Sie sicher, dass Sie nach der Installation Firewalls und Antivirensoftware aktivieren.

### <a name="installing-the-extension-pack"></a>Installieren des Erweiterungspakets

Sie können das Erweiterungspaket jederzeit installieren, bevor Sie Daten zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

> [!IMPORTANT]
> Um das Erweiterungspaket zu installieren, müssen Sie Mitglied der **sysadmin** -Server Rolle auf der-Instanz sein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

So installieren Sie das Erweiterungspaket:

1. Kopieren Sie SSMA für **SSMAforMySQLExtensionPack_*n*. msi**, wobei *n* die Buildnummer ist, auf den Computer, auf dem ausgeführt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
2. Doppelklicken Sie auf **SSMAforMySQLExtensionPack_*n*. msi**.
3. Klicken Sie im Dialogfeld **Willkommen** auf **weiter**.
4. Lesen Sie im Dialogfeld **Endbenutzer-Lizenzvertrag** den Lizenzvertrag. Wenn Sie zustimmen, aktivieren Sie die Option **Ich akzeptiere die Vereinbarung** , und klicken Sie dann auf **weiter**.
5. Klicken Sie im Dialogfeld Setuptyp **auswählen** auf **typisch**.
6. Klicken Sie im Dialogfeld **Installations bereit** auf **Installieren**.
7. Klicken Sie im Dialogfeld der **erste Schritt der Installation** auf **weiter**.

   Ein neues Dialogfeld wird angezeigt, in dem Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Extension Pack-Installation auswählen.
  
8. Wählen Sie die Instanz von aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , in der Sie MySQL-Schemas migrieren möchten, und klicken Sie dann auf **weiter**.
  
   Die Standard Instanz hat denselben Namen wie der Computer. Auf benannte Instanzen folgt ein umgekehrter Schrägstrich und der Instanzname.

9. Wählen Sie auf der Seite Verbindung die Authentifizierungsmethode aus, und klicken Sie dann auf **weiter**.
  
    Die Windows-Authentifizierung verwendet Ihre Windows-Anmelde Informationen, um sich bei der Instanz von anzumelden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Wenn Sie Server Authentifizierung auswählen, müssen Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Namen und ein Kennwort eingeben.

10. Im nächsten Schritt müssen Sie das Kennwort für einen Hauptschlüssel festlegen, der zum Verschlüsseln vertraulicher Daten verwendet wird, die während der serverseitigen Datenmigration in der Erweiterungspaket-Datenbank gespeichert werden. Geben **Sie ein**sicheres Kennwort ein, und klicken Sie auf

11. Wählen Sie im nächsten Dialogfeld die Option **Utilities Database *n* installieren aus, und installieren Sie Extension Pack-Bibliotheken**, wobei *n* die Versionsnummer ist, und klicken Sie dann auf **weiter**.

    Die **sysdb** -Datenbank wird mit den Tabellen und gespeicherten Prozeduren erstellt, die für die Datenmigration erforderlich sind (mithilfe der serverseitigen Daten Migrations-Engine), die in dieser Datenbank erstellt werden.

12. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Wählen Sie **Ja**aus, und klicken Sie dann auf **weiter**, um die Hilfsprogramme für eine andere Instanz von zu installieren. Oder klicken Sie auf **Nein**, um den Assistenten zu beenden.

## <a name="see-also"></a>Weitere Informationen

- [Installieren von SSMA für den MySQL-Client](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)
- [Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)
