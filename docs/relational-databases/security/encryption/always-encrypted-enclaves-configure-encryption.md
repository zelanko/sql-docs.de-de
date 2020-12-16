---
description: Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves
title: Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/10/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15'
ms.openlocfilehash: de9860fdf161d9ed43a1ae2c63e1210dd2079e42
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97477711"
---
# <a name="configure-column-encryption-in-place-using-always-encrypted-with-secure-enclaves"></a>Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves 
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

[Always Encrypted mit Secure Enclaves](always-encrypted-enclaves.md) unterstützt direkte kryptografische Vorgänge für Datenbankspalten. Dies geschieht innerhalb einer Secure Enclave in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Durch die direkte Verschlüsselung ist es nicht mehr erforderlich, die Daten für solche Vorgänge aus der Datenbank zu verschieben, wodurch die Kryptografievorgänge schneller und zuverlässiger werden. 

> [!NOTE]
> Trotz der Leistungsvorteile der direkten Verschlüsselung können kryptografische Vorgänge für große Tabellen eine lange Zeit in Anspruch nehmen und beträchtliche Ressourcen beanspruchen. Dadurch wird möglicherweise die Leistung und Verfügbarkeit Ihrer Anwendungen beeinträchtigt.

Durch die direkte Verschlüsselung ist es auch möglich, kryptografische Vorgänge mithilfe der Anweisung [ALTER TABLE ALTER COLUMN (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) auszulösen. Dies ist ohne Enclave nicht möglich.

## <a name="prerequisites"></a>Voraussetzungen
Die unterstützten kryptografischen Vorgänge und die Anforderungen für Spaltenverschlüsselungsschlüssel, die für die Vorgänge verwendet werden, lauten wie folgt:
- Verschlüsseln einer Klartextspalte. Der Spaltenverschlüsselungsschlüssel, der zum Verschlüsseln der Spalte verwendet wird, muss Enclave-fähig sein.
- Erneutes Verschlüsseln einer verschlüsselten Spalte mit einem neuen Verschlüsselungstyp und/oder einem neuen Spaltenverschlüsselungsschlüssel. Sowohl der aktuelle als auch der neue Spaltenverschlüsselungsschlüssel (sofern Letzterer sich vom aktuellen Schlüssel unterscheidet) müssen Enclave-fähig sein.
- Entschlüsseln einer verschlüsselten Spalte: der Spaltenverschlüsselungsschlüssel, der die Spalte schützt, muss Enclave-fähig sein.

Informationen dazu, wie Sie sicherstellen können, dass Ihre Spaltenverschlüsselungsschlüssel Enclave-fähig sind, finden Sie unter [Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-manage-keys.md).

Die direkte Verschlüsselung erfordert auch eine SQL Server-Instanz, die über eine ordnungsgemäß initialisierte Secure Enclave verfügt. Weitere Informationen finden Sie unter [Konfigurieren des Enclave-Typs für die Always Encrypted-Serverkonfigurationsoption](../../../database-engine/configure-windows/configure-column-encryption-enclave-type.md).

Ein Benutzer oder eine Anwendung, der oder die kryptografische Vorgänge auslöst, muss über Berechtigungen zum Vornehmen von Schemaänderungen für die Tabelle verfügen, die die betroffenen Spalten enthält. Zusätzlich muss der Benutzer oder die Anwendung auch Zugriff auf Spaltenhauptschlüssel haben, die an den Vorgängen beteiligt sind, sowie auf die relevanten Schlüsselmetadaten in der Datenbank.

Sie können die direkte Verschlüsselung nur mithilfe der Anweisung [ALTER TABLE ALTER COLUMN (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) von SQL Server Management Studio oder Ihrer benutzerdefinierten Anwendung auslösen. Weitere Informationen finden Sie unter [Direkte Konfiguration der Spaltenverschlüsselung mit Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md).

> [!NOTE]
> Zurzeit unterstützen der [Always Encrypted-Assistent](always-encrypted-wizard.md) und das [Set-SqlColumnEncryption](/powershell/module/sqlserver/set-sqlcolumnencryption)-Cmdlet keine direkte Verschlüsselung und laden die Daten für kryptografische Vorgänge immer herunter, auch wenn Ihre Konfiguration die oben genannten Anforderungen erfüllt. 

## <a name="next-steps"></a>Nächste Schritte
- [Direkte Konfiguration der Spaltenverschlüsselung mit Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md)
- [Erstellen und Verwenden von Indizes in Spalten mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-create-use-indexes.md)
- [Entwickeln von Anwendungen mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-client-development.md)