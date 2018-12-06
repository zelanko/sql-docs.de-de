---
title: Featureabhängigkeiten des Microsoft JDBC-Treibers für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01388e48e12a01e18b837cac8e663bf2f52ebe40
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52502630"
---
# <a name="feature-dependencies-of-the-microsoft-jdbc-driver-for-sql-server"></a>Featureabhängigkeiten des Microsoft JDBC-Treibers für SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Dieser Artikel beschreibt die Bibliotheken, denen von der Microsoft JDBC-Treiber für SQL Server abhängig ist. Das Projekt enthält die folgenden Abhängigkeiten.

## <a name="compile-time"></a>Kompilierzeit

- `azure-keyvault`: Azure Key Vault-Anbieter für die Always Encrypted Azure Key Vault-Funktion (optional)
- `adal4j`: Azure Active Directory-Authentifizierungsbibliothek für Java für das Azure Active Directory-Authentifizierung-Feature und die Azure Key Vault-Funktion (optional)

## <a name="test-time"></a>Testzeit

Bestimmte Projekte, die entweder die vorangehenden Funktionen erfordern müssen die entsprechenden Abhängigkeiten in ihrer POM-Datei explizit deklarieren.

**Zum Beispiel:** , wenn Sie das Feature für die Azure Active Directory-Authentifizierung verwenden, müssen Sie erneut die `adal4j` Abhängigkeit in POM-Datei des Projekts. Finden Sie unter den folgenden Codeausschnitt:

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

**Zum Beispiel:** , wenn Sie die Azure Key Vault-Funktion verwenden, müssen Sie erneut die `azure-keyvault` Abhängigkeit und die `adal4j` Abhängigkeit in POM-Datei des Projekts. Finden Sie unter den folgenden Codeausschnitt:

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

### <a name="working-with-the-azure-key-vault-provider"></a>Arbeiten mit dem Azure Key Vault-Anbieter:

- JDBC Driver, Version 7.0.0 - abhängigkeitsversionen: Azure Key Vault (Version 1.0.0), die Adal4j (Version 1.6.0), und ihre Abhängigkeiten ([beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-7-0-0.md))
- JDBC Driver, Version 6.4.0 - abhängigkeitsversionen: Azure Key Vault (Version 1.0.0), die Adal4j (Version 1.4.0), und ihre Abhängigkeiten ([beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- JDBC Driver, Version 6.2.2 - abhängigkeitsversionen: Azure Key Vault (Version 1.0.0), die Adal4j (Version 1.4.0), und ihre Abhängigkeiten ([beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- JDBC Driver, Version 6.0.0 - abhängigkeitsversionen: Azure Key Vault (Version 0.9.7), die Adal4j (Version 1.3.0), und ihre Abhängigkeiten ( [beispielanwendung](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> Mit 6.2.2 und 6.4.0 Treiberversionen haben die Azure-Keyvault-Java-Abhängigkeit auf Version 1.0.0 aktualisiert. Allerdings wird die neue Version war nicht kompatibel mit der früheren Version (0.9.7) und unterbricht die vorhandene Implementierung im Treiber. Die neue Implementierung im Treiber erforderlich, API-Änderungen, die unterbrochen wiederum Clientprogramme, die den Azure Key Vault-Anbieter verwenden.
>
> Dieses Problem ist behoben, mit der neuesten Treiber (7.0.0). Der entfernte Konstruktor, der die Rückruf-Authentifizierung verwendet wird zurück an den Azure Key Vault-Anbieter für die Abwärtskompatibilität hinzugefügt.

### <a name="working-with-azure-active-directory-authentication"></a>Arbeiten mit der Azure Active Directory-Authentifizierung:

- JDBC Driver, Version 7.0.0 - abhängigkeitsversionen: Ada4j (Version 1.6.0) und seine Abhängigkeiten
- JDBC Driver, Version 6.4.0 - abhängigkeitsversionen: Adal4j (Version 1.4.0) und seine Abhängigkeiten
- JDBC Driver, Version 6.2.2 - abhängigkeitsversionen: Adal4j (Version 1.4.0) und seine Abhängigkeiten
- JDBC Driver, Version 6.0.0 - abhängigkeitsversionen: Adal4j (Version 1.3.0), und seine Abhängigkeiten. In dieser Version des Treibers, Sie können eine Verbindung herstellen mit _ActiveDirectoryIntegrated_ Authentifizierungsmodus nur auf einem Windows-Betriebssystem und mithilfe von "sqljdbc_auth.dll" und Active Directory-Authentifizierungsbibliothek für SQL Server () ADALSQL. (DLL).

Von Treiberversion 6.4.0 gerechnet benötigen Anwendungen nicht zwingend ADALSQL verwenden. Die DLL auf Windows-Betriebssystemen. Für *nicht-Windows-Betriebssystemen*, der Treiber erfordert eine Kerberos-Ticket mit ActiveDirectoryIntegrated Authentifizierung arbeiten. Weitere Informationen zum Herstellen einer Verbindung mit Active Directory mithilfe von Kerberos finden Sie unter [festgelegt Kerberos-Ticket für Windows, Linux und Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac).

Für *Windows-Betriebssystemen*, der Treiber "sqljdbc_auth.dll" in der Standardeinstellung sucht und keine Kerberos-Ticket-Einrichtung oder Azure bibliotheksabhängigkeiten erforderlich. Wenn "sqljdbc_auth.dll" nicht verfügbar ist, sucht der Treiber die Kerberos-Ticket für die Authentifizierung bei Active Directory als bei anderen Betriebssystemen.

Sie erhalten eine [beispielanwendung](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md) , die diese Funktion verwendet.

## <a name="see-also"></a>Siehe auch

[JDBC-Treiber-GitHub-repository](https://github.com/microsoft/mssql-jdbc)  
 [JDBC-Treiber-API-Referenz](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
