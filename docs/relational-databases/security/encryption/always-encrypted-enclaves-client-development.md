---
title: Entwickeln von Anwendungen mithilfe von Always Encrypted mit Secure Enclaves | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 971cce5ddf61f528e9e4ffdc0377603b6ce96946
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411379"
---
# <a name="develop-applications-using-always-encrypted-with-secure-enclaves"></a>Entwickeln von Anwendungen mithilfe von Always Encrypted mit Secure Enclaves
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

[Always Encrypted mit Secure Enclaves](always-encrypted-enclaves.md) ist eine Erweiterung von [Always Encrypted](always-encrypted-database-engine.md), die umfangreichere Funktionen für Anwendungsabfragen in verschlüsselten vertraulichen Datenbankspalten bietet. Dabei kommen Secure Enclave-Technologien zum Einsatz, mit deren Hilfe der Abfrageexecutor in [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] Berechnungen mit verschlüsselten Spalten an eine Secure Enclave im [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]-Prozess delegieren kann.

## <a name="client-driver-for-always-encrypted-with-secure-enclaves"></a>Clienttreiber für Always Encrypted mit Secure Enclaves

Zum Entwickeln von Anwendungen mit Always Encrypted mit Secure Enclaves benötigen Sie eine Version des SQL-Clienttreibers, die Secure Enclaves unterstützt. Der Clienttreiber spielt die folgende wichtige Rolle:
- Bevor Sie eine Abfrage, für die eine Secure Enclave verwendet wird, zur Ausführung an [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] senden, initiiert der Treiber einen Enclave-Nachweis, um zu prüfen, ob die Secure Enclave vertrauenswürdig ist und ohne Risiko zur Verarbeitung vertraulicher Daten verwendet werden kann. Weitere Informationen zum Nachweis finden Sie unter [Secure Enclave-Nachweis](always-encrypted-enclaves.md#secure-enclave-attestation).
- Wenn der Nachweis erfolgreich geführt werden kann, richtet der Clienttreiber eine sichere Sitzung mit der Enclave ein, indem er ein gemeinsames Geheimnis aushandelt.
- Der Treiber verwendet das gemeinsame Geheimnis zur Verschlüsselung der Spaltenverschlüsselungsschlüssel, die von der Enclave zum Verarbeiten der Abfrage benötigt werden, und sendet die Schlüssel an [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)], von wo aus sie zur Entschlüsselung an die Secure Enclave weitergeleitet werden. 
- Abschließend sendet der Treiber die Abfrage zur Ausführung, wodurch in der Secure Enclave Berechnungen ausgelöst werden.

Wenn Sie die Secure Enclave-Funktionen verwenden möchten, müssen Sie Ihre Anwendung und Ihren Clienttreiber so konfigurieren, dass beim Herstellen einer Verbindung mit der Datenbank Enclave-Berechnungen aktiviert werden. Darüber hinaus müssen Sie einen Nachweisdienstendpunkt (eine Enclave-Nachweis-URL) angeben, die auf einen Nachweisdienst für Ihre Enclave zeigt. Die Details hängen vom verwendeten Treiber sowie vom verwendeten Nachweisdienst/Protokoll ab.

## <a name="next-steps"></a>Nächste Schritte

Always Encrypted mit Secure Enclaves wird von folgenden Clienttreibern unterstützt:
- .NET Framework-Datenanbieter für SQL Server in .NET Framework 4.7.2 oder höher. 
    - Weitere Informationen finden Sie unter [Verwenden von Always Encrypted mit dem .NET Framework-Datenanbieter für SQL Server](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
    - Ein Schritt-für-Schritt-Tutorial finden Sie unter [Tutorial: Entwickeln einer .NET Framework-Anwendung mithilfe von Always Encrypted mit Secure Enclaves](../tutorial-always-encrypted-enclaves-develop-net-framework-apps.md)
- Microsoft .NET-Datenanbieter für SQL Server in .NET Framework 4.6 oder höher und .NET Core 2.1 oder höher 
    - Weitere Informationen finden Sie unter [Verwenden von Always Encrypted mit dem Microsoft .NET-Datenanbieter für SQL Server](../../../connect/ado-net/sql/sqlclient-support-always-encrypted.md).
    - Ein Schritt-für-Schritt-Tutorial finden Sie unter [Tutorial: Entwickeln einer .NET-Anwendung mithilfe von Always Encrypted mit Secure Enclaves](../../../connect/ado-net/sql/tutorial-always-encrypted-enclaves-develop-net-apps.md)
- Microsoft ODBC Driver for SQL Server, Version 17.4 oder höher. 
    - Weitere Informationen finden Sie unter [Using Always Encrypted with the ODBC Driver (Verwenden von Always Encrypted mit dem ODBC-Treiber)](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md). 
    - Informationen zum Aktivieren von Enclave-Berechnungen für eine Datenbankverbindung mithilfe von ODBC finden Sie im Abschnitt [Aktivieren von Always Encrypted mit Secure Enclaves](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#enabling-always-encrypted-with-secure-enclaves).
