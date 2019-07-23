---
title: Featureabhängigkeiten des Microsoft JDBC-Treibers für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/16/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1bf49c4264b89b6a47f083eec3654a757c1dce6b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956596"
---
# <a name="feature-dependencies-of-the-microsoft-jdbc-driver-for-sql-server"></a>Featureabhängigkeiten des Microsoft JDBC-Treibers für SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

In diesem Artikel werden die Bibliotheken aufgeführt, von denen der Microsoft JDBC-Treiber für SQL Server abhängig ist. Für das Projekt gelten die folgenden Abhängigkeiten.

## <a name="compile-time"></a>Kompilierzeit

 - `com.microsoft.azure:azure-keyvault`: Azure Key Vault-Anbieter für das Azure Key Vault-Feature Always Encrypted (optional)
 - `com.microsoft.azure:azure-keyvault-webkey`: Azure Key Vault-Anbieter für das Azure Key Vault-Feature Always Encrypted (optional)
 - `com.microsoft.azure:adal4j`: Azure Active Directory Library für Java für die Azure Active Directory-Authentifizierung und das Azure Key Vault-Feature (optional)
 - `com.microsoft.rest:client-runtime`: Azure Active Directory Library für Java für die Azure Active Directory-Authentifizierung und das Azure Key Vault-Feature (optional)
- `org.osgi:org.osgi.core`: OSGi Core-Bibliothek für OSGi-Framework-Unterstützung.
- `org.osgi:org.osgi.compendium`: OSGi Compendium-Bibliothek für OSGi-Framework-Unterstützung.

## <a name="test-time"></a>Testzeit

Bei bestimmten Projekten, die eines der vorhergehenden Features benötigen, müssen Sie die jeweiligen Abhängigkeiten in der zugehörigen POM-Datei explizit deklarieren.

**Zum Beispiel:** , wenn Sie das Feature für die Azure Active Directory-Authentifizierung verwenden, müssen Sie erneut die `adal4j` Abhängigkeit in POM-Datei des Projekts. Dies ist im folgenden Codeausschnitt dargestellt:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.2.2.jre11</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.3</version>
</dependency>

<dependency>
    <groupId>com.microsoft.rest</groupId>
    <artifactId>client-runtime</artifactId>
    <version>1.6.5</version>
</dependency>
```

**Zum Beispiel:** , wenn Sie die Azure Key Vault-Funktion verwenden, müssen Sie erneut die `azure-keyvault` Abhängigkeit und die `adal4j` Abhängigkeit in POM-Datei des Projekts. Dies ist im folgenden Codeausschnitt dargestellt:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.2.2.jre11</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.3</version>
</dependency>

<dependency>
    <groupId>com.microsoft.rest</groupId>
    <artifactId>client-runtime</artifactId>
    <version>1.6.5</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.2.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault-webkey</artifactId>
    <version>1.2.0</version>
</dependency>
```

## <a name="dependency-requirements-for-the-jdbc-driver"></a>Abhängigkeitsanforderungen für den JDBC-Treiber

### <a name="working-with-the-azure-key-vault-provider"></a>Arbeiten mit dem Azure Key Vault-Anbieter:

- JDBC-Treiber, Version 7.2.2 – Abhängigkeitsversionen: Azure-Keyvault (Version 1.2.0), Azure-Keyvault-Webkey (Version 1.2.0), Adal4j (Version 1.6.3), Client-Runtime-for-AutoRest (1.6.5) und die jeweiligen Abhängigkeiten ([Beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-7.0.md))
- JDBC-Treiber, Version 7.0.0 – Abhängigkeitsversionen: Azure-Keyvault (Version 1.0.0), Adal4j (Version 1.6.0) und die jeweiligen Abhängigkeiten ([Beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-7.0.md))
- JDBC-Treiber, Version 6.4.0 – Abhängigkeitsversionen: Azure-Keyvault (Version 1.0.0), Adal4j (Version 1.4.0) und die jeweiligen Abhängigkeiten ([Beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- JDBC-Treiber, Version 6.2.2 – Abhängigkeitsversionen: Azure-Keyvault (Version 1.0.0), Adal4j (Version 1.4.0) und die jeweiligen Abhängigkeiten ([Beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- JDBC-Treiber, Version 6.0.0 – Abhängigkeitsversionen: Azure-Keyvault (Version 0.9.7), Adal4j (Version 1.3.0) und die jeweiligen Abhängigkeiten ([Beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> Bei den Treiberversionen 6.2.2 und 6.4.0 wurde die Azure-Keyvault-Java-Abhängigkeit auf Version 1.0.0 aktualisiert. Die neue Version war jedoch nicht mit der vorherigen Version (0.9.7) kompatibel und unterbricht die vorhandene Implementierung im Treiber. Die neue Implementierung im Treiber erforderte API-Änderungen, wodurch wiederum Clientprogramme unterbrochen werden, die den Azure Key Vault-Anbieter verwenden.
>
> Dieses Problem wurde in der neuesten Treiberversion (7.0.0) behoben. Der entfernte Konstruktor, der den Authentifizierungsrückrufmechanismus verwendet hat, wird aus Gründen der Abwärtskompatibilität wieder zum Azure Key Vault-Anbieter hinzugefügt.

### <a name="working-with-azure-active-directory-authentication"></a>Arbeiten mit der Azure Active Directory-Authentifizierung:

- JDBC-Treiber, Version 7.2.2 – Abhängigkeitsversionen: Adal4j (Version 1.6.3), Client-Runtime-for-AutoRest (1.6.5) und die jeweiligen Abhängigkeiten
- JDBC-Treiber, Version 7.0.0 – Abhängigkeitsversionen: Adal4j (Version 1.6.0) und ihre Abhängigkeiten
- JDBC-Treiber, Version 6.4.0 – Abhängigkeitsversionen: Adal4j (Version 1.4.0) und ihre Abhängigkeiten
- JDBC-Treiber, Version 6.2.2 – Abhängigkeitsversionen: Adal4j (Version 1.4.0) und ihre Abhängigkeiten
- JDBC-Treiber, Version 6.0.0 – Abhängigkeitsversionen: Adal4j (Version 1.3.0) und ihre Abhängigkeiten. In dieser Treiberversion können Sie unter Verwendung des _ActiveDirectoryIntegrated_-Authentifizierungsmodus nur unter einem Windows-Betriebssystem und mit „sqljdbc_auth.dll“ und Active Directory Authentication Library für SQL Server (ADALSQL.DLL) eine Verbindung herstellen.

Ab Treiberversion 6.4.0 müssen Anwendungen nicht zwangsläufig ADALSQL.DLL unter Windows-Betriebssystemen verwenden. Bei *Nicht-Windows-Betriebssystemen* benötigt der Treiber zum Arbeiten mit der ActiveDirectoryIntegrated-Authentifizierung ein Kerberos-Ticket. Weitere Informationen zum Herstellen einer Verbindung mit Active Directory mithilfe von Kerberos finden Sie unter [Festlegen eines Kerberos-Tickets unter Windows, Linux und Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac).

Bei *Windows-Betriebssystemen* sucht der Treiber standardmäßig nach „sqljdbc_auth.dll“ und erfordert keine Kerberos-Ticketeinrichtung oder Azure-Bibliotheksabhängigkeiten. Wenn „sqljdbc_auth.dll“ nicht verfügbar ist, sucht der Treiber (wie unter anderen Betriebssystemen) nach dem Kerberos-Ticket für die Authentifizierung bei Active Directory.

[Hier finden Sie eine Beispielanwendung](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md), die dieses Feature verwendet.

## <a name="see-also"></a>Siehe auch

[JDBC Driver GitHub repository (GitHub-Repository für den JDBC-Treiber)](https://github.com/microsoft/mssql-jdbc)  
[JDBC-Treiber-API-Referenz](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
