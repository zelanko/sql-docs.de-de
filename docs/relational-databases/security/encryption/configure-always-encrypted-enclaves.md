---
title: Konfigurieren und Verwenden von Always Encrypted mit Secure Enclaves | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 568944db62ca94048c45450500d3060daa957680
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "74317933"
---
# <a name="configure-and-use-always-encrypted-with-secure-enclaves"></a>Konfigurieren und Verwenden von Always Encrypted mit Secure Enclaves 

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Always Encrypted mit Secure Enclaves](always-encrypted-enclaves.md) erweitert das vorhandene [Always Encrypted](always-encrypted-database-engine.md)-Feature um umfangreichere Funktionalitäten für sensible Daten und schützt gleichzeitig die vertraulichen Daten. Dieser Artikel führt allgemeine Aufgaben beim Konfigurieren und Verwenden des Features auf.

Ein Tutorial für den schnellen Einstieg mit Always Encrypted mit Secure Enclaves finden Sie unter [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).

## <a name="set-up-your-environment-to-support-enclaves-and-attestation"></a>Einrichten Ihrer Umgebung zur Unterstützung von Enclaves und Nachweis
Details finden Sie in den folgenden Artikeln:
- [Planen des Nachweises des Host-Überwachungsdiensts](./always-encrypted-enclaves-host-guardian-service-plan.md)
- [Bereitstellen des Host-Überwachungsdiensts für [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]](./always-encrypted-enclaves-host-guardian-service-deploy.md)
- [Registrieren Ihres Computers mit dem Host-Überwachungsdienst](./always-encrypted-enclaves-host-guardian-service-register.md)

## <a name="manage-keys-for-always-encrypted-with-secure-enclaves"></a>Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves
Weitere Informationen finden Sie in den folgenden Artikeln:
- [Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves – Übersicht](always-encrypted-enclaves-manage-keys.md)
- [Bereitstellen Enclave-fähiger Schlüssel](always-encrypted-enclaves-provision-keys.md)
- [Rotieren Enclave-fähiger Schlüssel](always-encrypted-enclaves-rotate-keys.md)

## <a name="configure-columns-with-always-encrypted-with-secure-enclaves"></a>Konfigurieren von Spalten mit Always Encrypted mit Secure Enclaves
Weitere Informationen finden Sie in den folgenden Artikeln:
- [Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves – Übersicht](always-encrypted-enclaves-configure-encryption.md)
- [Direkte Konfiguration der Spaltenverschlüsselung mit Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md)
- [Aktivieren von Always Encrypted mit Secure Enclaves für vorhandene verschlüsselte Spalten](always-encrypted-enclaves-enable-for-encrypted-columns.md)

> [!NOTE]
> Ein ausführliches Tutorial zum Einrichten Ihrer Testumgebung mit anschließendem Testen der Funktionalität von Always Encrypted mit Secure Enclaves in SSMS finden Sie unter [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).

## <a name="query-columns-using-always-encrypted-with-secure-enclaves"></a>Abfragen von Spalten mit Always Encrypted mit Secure Enclaves
Weitere Informationen finden Sie in den folgenden Artikeln:
- [Abfragen von Spalten mit Always Encrypted mit Secure Enclaves – Übersicht](always-encrypted-enclaves-query-columns.md)
- [Abfragen von Spalten unter Verwendung von Always Encrypted mit Secure Enclaves mit SSMS](always-encrypted-enclaves-query-columns-ssms.md)

## <a name="create-and-use-indexes-on-enclave-enabled-columns"></a>Erstellen und Verwenden von Indizes für Enclave-fähige Spalten
Weitere Informationen finden Sie in den folgenden Artikeln:
- [Erstellen und Verwenden von Indizes in Spalten mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-create-use-indexes.md)

## <a name="develop-applications-using-always-encrypted-with-secure-enclaves"></a>Entwickeln von Anwendungen mithilfe von Always Encrypted mit Secure Enclaves
Weitere Informationen finden Sie in den folgenden Artikeln:
- [Entwickeln von Anwendungen mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-client-development.md)
