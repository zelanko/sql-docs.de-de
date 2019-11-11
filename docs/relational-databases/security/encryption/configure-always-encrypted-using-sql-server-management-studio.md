---
title: Konfigurieren von Always Encrypted mithilfe von SQL Server Management Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/31/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Always Encrypted, configure with SSMS
ms.assetid: 29816a41-f105-4414-8be1-070675d62e84
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6ff7ef354fdf3118f68c22bf2ad927070bf8e4b6
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73594421"
---
# <a name="configure-always-encrypted-using-sql-server-management-studio"></a>Konfigurieren von Always Encrypted mithilfe von SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Dieser Artikel beschreibt die Aufgaben, die bei der Konfiguration von Always Encrypted und der Verwaltung von Datenbanken anfallen, die Always Encrypted mit [SQL Server Management Studio (SSMS)](../../../ssms/download-sql-server-management-studio-ssms.md)verwenden.

## <a name="security-considerations-when-using-ssms-to-configure-always-encrypted"></a>Sicherheitsüberlegungen bei der Verwendung von SSMS zum Konfigurieren von Always Encrypted

Wenn Sie SSMS zur Konfiguration von Always Encrypted verwenden, verwaltet SSMS beide Always Encrypted-Schlüssel und sensible Daten. Beide Schlüssel und die Daten werden daher in SSMS als Klartext angezeigt. Es ist daher wichtig, dass Sie SSMS auf einem sicheren Computer ausführen. Wenn Ihre Datenbank in SQL Server gehostet wird, sollten Sie sicherstellen, dass SSMS auf einem anderen Computer als dem Computer ausgeführt wird, der Ihre SQL Server-Instanz hostet. Der primäre Zweck von Always Encrypted ist, sicherzustellen, dass verschlüsselte sensible Daten sicher sind, selbst wenn das Datenbanksystem kompromittiert wird. Daher kann das Ausführen eines PowerShell-Skripts, das Schlüssel und/oder sensible Daten auf dem SQL Server-Computer verarbeitet, die Vorteile der Funktion einschränken oder zunichte machen. Weitere Empfehlungen finden Sie unter [Security Considerations for Key Management](overview-of-key-management-for-always-encrypted.md#security-considerations-for-key-management)(Überlegungen zur Verwaltung von Schlüsseln).

SSMS unterstützt keine Rollentrennung zwischen Personen, die die Datenbank verwalten (Datenbankadministratoren; DBAs), und denjenigen, die kryptografische Schlüssel verwalten und Zugriff auf Klartextdaten haben (Sicherheitsadministratoren und/oder Anwendungsadministratoren). Wenn Ihre Organisation auf Rollentrennung besteht, sollten Sie PowerShell verwenden, um Always Encrypted zu konfigurieren. Weitere Informationen finden Sie unter [Übersicht über die Schlüsselverwaltung für Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md) und [Konfigurieren von Always Encrypted mithilfe von PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md). 

## <a name="always-encrypted-tasks-using-ssms"></a>Always Encrypted-Aufgaben mit SSMS

- [Bereitstellen von Always Encrypted-Schlüsseln mithilfe von SQL Server Management Studio](configure-always-encrypted-keys-using-ssms.md)
- [Rotieren von Always Encrypted-Schlüsseln mithilfe von SQL Server Management Studio](rotate-always-encrypted-keys-using-ssms.md)
- [Konfigurieren der Spaltenverschlüsselung mit dem Always Encrypted-Assistenten](always-encrypted-wizard.md)
- [Konfigurieren der Spaltenverschlüsselung unter Verwendung von Always Encrypted mit einem DAC-Paket](configure-always-encrypted-using-dacpac.md)
- [Abfragen von Spalten mit Always Encrypted und SQL Server Management Studio](always-encrypted-query-columns-ssms.md)
- [Exportieren und Importieren von Datenbanken mit Always Encrypted](always-encrypted-migrate-using-bacpac.md)
- [Sichern und Wiederherstellen von Datenbanken mit Always Encrypted](always-encrypted-migrate-using-backup-restore.md)
- [Migrieren von Daten zu oder aus Spalten mithilfe von Always Encrypted mit dem SQL Server-Import/Export-Assistenten](always-encrypted-migrate-using-import-export-wizard.md)

## <a name="see-also"></a>Weitere Informationen
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Übersicht über die Schlüsselverwaltung für Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Konfigurieren von Always Encrypted mithilfe von PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)
- [Entwickeln von Anwendungen mit Always Encrypted](always-encrypted-client-development.md)
