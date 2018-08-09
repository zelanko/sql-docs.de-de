---
title: Featureabhängigkeiten des Microsoft JDBC-Treibers für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
caps.latest.revision: 57
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70179d55c6aae5fc01c84f0c4af860f86d528a06
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454224"
---
# <a name="feature-dependencies-of-microsoft-jdbc-driver-for-sql-server"></a>Featureabhängigkeiten des Microsoft JDBC-Treibers für SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Diese Seite führt Sie Bibliotheken, denen von der Microsoft JDBC-Treiber für SQL Server abhängig ist. Das Projekt enthält die folgenden Abhängigkeiten.

## <a name="compile-time"></a>Kompilierzeit

- `azure-keyvault`: Azure Key Vault-Anbieter für Always Encrypted Azure Key Vault-Feature (optional)
- `adal4j`: Azure Active Directory-Bibliothek für Java für Azure Active Directory-Authentifizierung-Feature und Azure Key Vault-Feature (optional)

## <a name="test-time"></a>Testzeit

Bestimmte Projekte, die eines der beiden oben genannten Features erfordern müssen explizit deklarieren, die entsprechenden Abhängigkeiten in ihrer Pom-Datei:

**_Zum Beispiel:_**  Verwendung _Feature von Azure Active Directory-Authentifizierung_, müssen Sie erneut _adal4j_ Abhängigkeit in Pom-Datei des Projekts. Finden Sie unter den folgenden Codeausschnitt:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.0</version>
</dependency>
```

**_Zum Beispiel:_**  Verwendung _Azure Key Vault-Feature_, müssen Sie erneut _Azure Key Vault_ Abhängigkeit und _adal4j_ die Abhängigkeit in Pom-Datei Ihres Projekts. Finden Sie unter den folgenden Codeausschnitt:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.0.0</version>
</dependency>
```

## <a name="dependency-requirements-for-the-jdbc-driver"></a>Abhängigkeitsanforderungen für den JDBC-Treiber

### <a name="working-with-azure-key-vault-provider"></a>Arbeiten mit Azure Key Vault-Anbieters:

- JDBC Driver, Version 7.0.0 - abhängigkeitsversionen: Azure Key Vault (Version 1.0.0), die Adal4j (Version 1.6.0), und ihre Abhängigkeiten ([Beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-7-0-0.md))
- JDBC Driver, Version 6.4.0 - abhängigkeitsversionen: Azure Key Vault (Version 1.0.0), die Adal4j (Version 1.4.0), und ihre Abhängigkeiten ([Beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- JDBC Driver, Version 6.2.2 - abhängigkeitsversionen: Azure Key Vault (Version 1.0.0), die Adal4j (Version 1.4.0), und ihre Abhängigkeiten ([Beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- JDBC Driver, Version 6.0.0 - abhängigkeitsversionen: Azure Key Vault (Version 0.9.7), die Adal4j (Version 1.3.0), und ihre Abhängigkeiten ( [Beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> V6.2.2 und v6.4.0 Treiberversionen haben die Azure-Keyvault-Java-Abhängigkeit auf Version 1.0.0 aktualisiert. Allerdings wird die neue Version war nicht kompatibel mit der früheren Version (Version 0.9.7) und aus diesem Grund unterbrochen wird die vorhandene Implementierung im Treiber. Die neue Implementierung im Treiber erforderlich, API-Änderungen, die unterbrochen wiederum Clientprogramme, die den Azure Key Vault-Anbieter verwenden.

> Dieses Problem wurde mit dem neuesten Treiber Version v7.0.0 gelöst, wie der entfernte Konstruktor mit Rückruf Authentifizierungsmechanismus an Azure Key Vault-Anbieter für Abwärtskompatibilität Kompatibilität hinzugefügt wird.

### <a name="working-with-azure-active-directory-authentication"></a>Arbeiten mit der Azure Active Directory-Authentifizierung:

- JDBC Driver, Version 7.0.0 - abhängigkeitsversionen: Ada4j (Version 1.6.0) und seine Abhängigkeiten
- JDBC Driver, Version 6.4.0 - abhängigkeitsversionen: Adal4j (Version 1.4.0) und seine Abhängigkeiten
- JDBC Driver, Version 6.2.2 - abhängigkeitsversionen: Adal4j (Version 1.4.0) und seine Abhängigkeiten
- JDBC Driver, Version 6.0.0 - abhängigkeitsversionen: Adal4j (Version 1.3.0), und seine Abhängigkeiten – In dieser Version des Treibers, Sie können eine Verbindung herstellen mit _ActiveDirectoryIntegrated_ Authentifizierungsmodus nur auf einem Windows-Betriebssystem und Verwenden von "sqljdbc_auth.dll" und Active Directory-Authentifizierungsbibliothek für SQL Server (ADALSQL. (DLL).

Von Treiberversion 6.4.0 oder höher benötigen Anwendungen nicht zwingend ADALSQL verwenden. Die DLL auf Windows-Betriebssystemen. Für **nicht-Windows-Betriebssystemen**, der Treiber erfordert Kerberos-Ticket mit ActiveDirectoryIntegrated Authentifizierung arbeiten. Weitere Informationen zum Herstellen einer Verbindung mit Active Directory mithilfe von Kerberos finden Sie unter [festgelegt Kerberos-Ticket für Windows, Linux und Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac).

Für **Windows-Betriebssystemen**, Treiber "sqljdbc_auth.dll" in der Standardeinstellung sucht und keine Kerberos-Ticket-Einrichtung oder Azure bibliotheksabhängigkeiten erforderlich. Wenn "sqljdbc_auth.dll" nicht verfügbar ist, sucht Treiber allerdings für Kerberos-Ticket für die Authentifizierung bei Active Directory als bei anderen Betriebssystemen.

Eine beispielanwendung, die mit diesem Feature finden Sie [hier](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md).

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[JDBC-Treiber-GitHub-Repository](https://github.com/microsoft/mssql-jdbc)  
 [API-Referenz für den JDBC-Treiber](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
