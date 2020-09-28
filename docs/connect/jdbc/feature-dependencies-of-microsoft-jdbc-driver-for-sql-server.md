---
title: Featureabhängigkeiten des Microsoft JDBC-Treibers
description: Erfahren Sie mehr über die Abhängigkeiten des Microsoft JDBC-Treibers für SQL Server und wie Sie ihnen gerecht werden.
ms.custom: ''
ms.date: 8/24/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9e7c01c160848e5a0067db9d37b7e2dbe220386f
ms.sourcegitcommit: 9be0047805ff14e26710cfbc6e10d6d6809e8b2c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "89042433"
---
# <a name="feature-dependencies-of-the-microsoft-jdbc-driver-for-sql-server"></a>Featureabhängigkeiten des Microsoft JDBC-Treibers für SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

In diesem Artikel werden die Bibliotheken aufgeführt, von denen der Microsoft JDBC-Treiber für SQL Server abhängig ist. Für das Projekt gelten die folgenden Abhängigkeiten.

## <a name="compile-time"></a>Kompilierzeit

 - `com.microsoft.azure:azure-keyvault` : Azure Key Vault-Anbieter für das Azure Key Vault-Feature Always Encrypted (Optional)
 - `com.microsoft.azure:adal4j` : Azure Active Directory Library für Java für die Azure Active Directory-Authentifizierung und das Azure Key Vault-Feature (Optional)
 - `com.microsoft.rest:client-runtime` : Azure Active Directory Library für Java für die Azure Active Directory-Authentifizierung und das Azure Key Vault-Feature (Optional)
 - `org.antlr:antlr4-runtime`: ANTLR 4 Runtime für das useFmtOnly-Feature (Optional)
 - `org.osgi:org.osgi.core`: OSGi Core-Bibliothek für OSGi-Framework-Unterstützung
 - `org.osgi:org.osgi.compendium`: OSGi Compendium-Bibliothek für OSGi-Framework-Unterstützung
 - `com.google.code.gson`: JSON-Parser für Always Encrypted mit Secure Enclaves-Feature (Optional)
 - `org.bouncycastle.bcprov-jdk15on`: Bouncy Castle Provider für Always Encrypted mit dem Secure Enclaves-Feature bei ausschließlicher Verwendung von Java 8 (Optional)

## <a name="test-time"></a>Testzeit

Bei bestimmten Projekten, die eines der vorhergehenden Features benötigen, müssen Sie die jeweiligen Abhängigkeiten in der zugehörigen POM-Datei explizit deklarieren.

**Beispiel:** Wenn Sie das Feature für die Azure Active Directory-Authentifizierung verwenden, müssen Sie erneut die `adal4j`-Abhängigkeit in der POM-Datei Ihres Projekts erklären. Dies ist im folgenden Codeausschnitt dargestellt:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.4.1.jre11</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.5</version>
</dependency>

<dependency>
    <groupId>com.microsoft.rest</groupId>
    <artifactId>client-runtime</artifactId>
    <version>1.7.4</version>
</dependency>
```

**Beispiel:** Wenn Sie das Azure Key Vault-Feature verwenden, müssen Sie die `azure-keyvault`-Abhängigkeit und die `adal4j`-Abhängigkeit noch mal in der POM-Datei Ihres Projekts erklären. Dies ist im folgenden Codeausschnitt dargestellt:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.4.1.jre11</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.5</version>
</dependency>

<dependency>
    <groupId>com.microsoft.rest</groupId>
    <artifactId>client-runtime</artifactId>
    <version>1.7.4</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.2.4</version>
</dependency>
```

## <a name="dependency-requirements-for-the-jdbc-driver"></a>Abhängigkeitsanforderungen für den JDBC-Treiber

### <a name="working-with-the-azure-key-vault-provider"></a>Arbeiten mit dem Azure Key Vault-Anbieter:

- Version 8.4.1 des JDBC-Treibers – Abhängigkeitsversionen: Azure-Keyvault (Version 1.2.4), Adal4j (Version 1.6.5), Client-Runtime-for-AutoRest (1.7.4) und die jeweiligen Abhängigkeiten ([Beispielanwendung](azure-key-vault-sample-version-7.0.md))
- Version 8.2.2 des JDBC-Treibers – Abhängigkeitsversionen: Azure-Keyvault (Version 1.2.2), Adal4j (Version 1.6.4), Client-Runtime-for-AutoRest (1.7.0) und die jeweiligen Abhängigkeiten ([Beispielanwendung](azure-key-vault-sample-version-7.0.md))
- Version 7.4.1 des JDCB-Treibers – Abhängigkeitsversionen: Azure-Keyvault (Version 1.2.1), Adal4j (Version 1.6.4), Client-Runtime-for-AutoRest (1.6.10) und die jeweiligen Abhängigkeiten ([Beispielanwendung](azure-key-vault-sample-version-7.0.md))
- Version 7.2.2 des JDCB-Treibers – Abhängigkeitsversionen: Azure-Keyvault (Version 1.2.0), Azure-Keyvault-Webkey (Version 1.2.0), Adal4j (Version 1.6.3), Client-Runtime-for-AutoRest (1.6.5) und die jeweiligen Abhängigkeiten ([Beispielanwendung](azure-key-vault-sample-version-7.0.md))
- Version 7.0.0 des JDCB-Treibers – Abhängigkeitsversionen: Azure-Keyvault (Version 1.0.0), Adal4j (Version 1.6.0) und die jeweiligen Abhängigkeiten ([Beispielanwendung](azure-key-vault-sample-version-7.0.md))
- Version 6.4.0 des JDCB-Treibers – Abhängigkeitsversionen: Azure-Keyvault (Version 1.0.0), Adal4j (Version 1.4.0) und die jeweiligen Abhängigkeiten ([Beispielanwendung](azure-key-vault-sample-version-6.2.2.md))
- Version 6.2.2 des JDCB-Treibers – Abhängigkeitsversionen: Azure-Keyvault (Version 1.0.0), Adal4j (Version 1.4.0) und die jeweiligen Abhängigkeiten ([Beispielanwendung](azure-key-vault-sample-version-6.2.2.md))
- Version 6.0.0 des JDCB-Treibers – Abhängigkeitsversionen: Azure-Keyvault (Version 0.9.7), Adal4j (Version 1.3.0) und die jeweiligen Abhängigkeiten ([Beispielanwendung](azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> Bei den Treiberversionen 6.2.2 und 6.4.0 wurde die Azure-Keyvault-Java-Abhängigkeit auf Version 1.0.0 aktualisiert. Die neue Version war jedoch nicht mit der vorherigen Version (0.9.7) kompatibel und unterbricht die vorhandene Implementierung im Treiber. Die neue Implementierung im Treiber erforderte API-Änderungen, wodurch wiederum Clientprogramme unterbrochen werden, die den Azure Key Vault-Anbieter verwenden.
>
> Dieses Problem wurde in den neuesten Treiberversionen (ab 7.0.0) behoben. Der entfernte Konstruktor, der den Authentifizierungsrückrufmechanismus verwendet hat, wird aus Gründen der Abwärtskompatibilität wieder zum Azure Key Vault-Anbieter hinzugefügt.

### <a name="working-with-azure-active-directory-authentication"></a>Arbeiten mit der Azure Active Directory-Authentifizierung:

- Version 8.4.1 des JDBC-Treibers – Abhängigkeitsversionen: Adal4j (Version 1.6.5), Client-Runtime-for-AutoRest (1.7.4) und die jeweiligen Abhängigkeiten
- Version 8.2.2 des JDBC-Treibers – Abhängigkeitsversionen: Adal4j (Version 1.6.4), Client-Runtime-for-AutoRest (1.7.0) und die jeweiligen Abhängigkeiten In dieser Treiberversion wurde „sqljdbc_auth.dll“ in „mssql-jdbc_auth-\<version>-\<arch>.dll“ umbenannt.
- Version 7.4.1 des JDCB-Treibers – Abhängigkeitsversionen: Adal4j (Version 1.6.4), Client-Runtime-for-AutoRest (1.6.10) und die jeweiligen Abhängigkeiten
- Version 7.2.2 des JDCB-Treibers – Abhängigkeitsversionen: Adal4j (Version 1.6.3), Client-Runtime-for-AutoRest (1.6.5) und die jeweiligen Abhängigkeiten
- Version 7.0.0 des JDCB-Treibers – Abhängigkeitsversionen: Adal4j (Version 1.6.0) und die entsprechenden Abhängigkeiten
- Version 6.4.0 des JDCB-Treibers – Abhängigkeitsversionen: Adal4j (Version 1.4.0) und die entsprechenden Abhängigkeiten
- Version 6.2.2 des JDCB-Treibers – Abhängigkeitsversionen: Adal4j (Version 1.4.0) und die entsprechenden Abhängigkeiten
- Version 6.0.0 des JDCB-Treibers – Abhängigkeitsversionen: Adal4j (Version 1.3.0) und die entsprechenden Abhängigkeiten In dieser Treiberversion können Sie unter Verwendung des _ActiveDirectoryIntegrated_-Authentifizierungsmodus nur unter einem Windows-Betriebssystem und mit „sqljdbc_auth.dll“ und Active Directory Authentication Library für SQL Server (ADALSQL.DLL) eine Verbindung herstellen.

Ab Treiberversion 6.4.0 müssen Anwendungen nicht zwangsläufig ADALSQL.DLL unter Windows-Betriebssystemen verwenden. Bei *Nicht-Windows-Betriebssystemen* benötigt der Treiber zum Arbeiten mit der ActiveDirectoryIntegrated-Authentifizierung ein Kerberos-Ticket. Weitere Informationen zum Herstellen einer Verbindung mit Active Directory mithilfe von Kerberos finden Sie unter [Festlegen eines Kerberos-Tickets unter Windows, Linux und macOS](connecting-using-azure-active-directory-authentication.md#set-kerberos-ticket-on-windows-linux-and-macos).

Bei *Windows-Betriebssystemen* sucht der Treiber standardmäßig nach „sqljdbc_auth.dll“ und erfordert keine Kerberos-Ticketeinrichtung oder Azure-Bibliotheksabhängigkeiten. Wenn „sqljdbc_auth.dll“ nicht verfügbar ist, sucht der Treiber (wie unter anderen Betriebssystemen) nach dem Kerberos-Ticket für die Authentifizierung bei Active Directory.

Ab der Treiberversion 8.2.2 wurde „sqljdbc_auth.dll“ in „mssql-jdbc_auth-\<version>-\<arch>.dll“ umbenannt. Beispiel: „mssql-jdbc_auth-8.2.2.x64.dll“.

[Hier finden Sie eine Beispielanwendung](connecting-using-azure-active-directory-authentication.md), die dieses Feature verwendet.

## <a name="see-also"></a>Weitere Informationen

[JDBC Driver GitHub repository (GitHub-Repository für den JDBC-Treiber)](https://github.com/microsoft/mssql-jdbc)  
[JDBC-Treiber-API-Referenz](reference/jdbc-driver-api-reference.md)
