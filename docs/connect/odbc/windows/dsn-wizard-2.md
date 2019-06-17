---
title: Datenquellen (Assistentenbildschirm 2) (ODBC-Treiber für SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: v-jizho2
manager: jroth
ms.openlocfilehash: 2c41b9215979488cbec9ebda89d98bb0f464d11a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797809"
---
# <a name="data-source-wizard-screen-2"></a>Datenquellen-Assistent (Bildschirm 2)

Geben Sie die Authentifizierungsmethode an, und richten Sie Einträge des erweiterten Clients von Microsoft SQL Server sowie den Anmeldenamen und das Kennwort ein, die der ODBC Driver for SQL Server zum Herstellen einer Verbindung mit SQL Server verwendet, während die Datenquelle konfiguriert wird.

## <a name="options"></a>enthalten

### <a name="with-integrated-windows-authentication"></a>Mit integrierter Windows-Authentifizierung

Gibt an, dass der Treiber eine sichere (oder vertrauenswürdige) Verbindung mit einem SQL Server anfordern. Wenn diese Option aktiviert ist, verwendet SQL Server unabhängig vom aktuellen Anmeldesicherheitsmodus auf dem Server die integrierte Anmeldesicherheit, um Verbindungen mit dieser Datenquelle herzustellen. Alle angegebenen Anmelde-IDs oder Kennwörter werden ignoriert. Der SQL Server-Systemadministrator muss Ihren Windows-Anmeldenamen eine SQL Server-Anmelde-ID zugeordnet haben (z. B. mithilfe von SQL Server Management Studio).

Optional können Sie einen Dienstprinzipalnamen (Service Principal Name, SPN) für den Server angeben.

### <a name="with-active-directory-integrated-authentication"></a>Mit integrierter Active Directory-Authentifizierung

Gibt an, dass der Treiber mit SQL Server mithilfe von Azure Active Directory authentifizieren. Wenn diese Option aktiviert ist, verwendet SQL Server unabhängig vom aktuellen Anmeldesicherheitsmodus auf dem Server die integrierte Anmeldesicherheit von Azure Active Directory, um Verbindungen mit dieser Datenquelle herzustellen.

### <a name="with-sql-server-authentication"></a>Mit SQL Server-Authentifizierung

Gibt an, dass der Treiber mit SQL Server mithilfe der Anmelde-ID und Kennwort authentifizieren.

### <a name="with-active-directory-password-authentication"></a>Mit Active Directory-Kennwortauthentifizierung

Gibt an, dass der Treiber mit SQL Server mithilfe einer Azure Active Directory-Anmelde-ID und Kennwort authentifizieren.

### <a name="with-active-directory-interactive-authentication"></a>Mit interaktiver Active Directory-Authentifizierung

Gibt an, dass der Treiber mit SQL Server mithilfe von Azure Active Directory interaktiven Modus durch die Bereitstellung der Anmelde-ID zu authentifizieren. Dadurch wird das Dialogfeld mit der Windows Azure-Authentifizierung Eingabeaufforderung ausgelöst.

### <a name="login-id"></a>Login ID

Gibt die Anmelde-ID, der Treiber beim SQL Server herstellen können verwendet, wenn **mit SQL Server-Authentifizierung mit Anmelde-ID und Kennwort, die vom Benutzer eingegebene** oder **mit Active Directory-Kennwortauthentifizierung-Authentifizierung, die mit einer Anmelde-ID und das Kennwort, die vom Benutzer eingegebene** oder **mit Active Directory Interavtive Authentifizierung, die mit einer Anmelde-ID, die vom Benutzer eingegebene** ausgewählt ist. Die gilt nur für die Verbindung, die zum Bestimmen der Standardeinstellungen des Servers hergestellt wird; es gilt nicht für folgende Verbindungen, die nach dem Erstellen mit der Datenquelle hergestellt werden.

### <a name="password"></a>Kennwort

Gibt das Kennwort, der Treiber beim SQL Server herstellen können verwendet, wenn **mit SQL Server-Authentifizierung mit Anmelde-ID und Kennwort, die vom Benutzer eingegebene** oder **mit Active Directory-Kennwortauthentifizierung-Authentifizierung, die mit einer Anmelde-ID und das Kennwort, die vom Benutzer eingegebene** ausgewählt ist. Die gilt nur für die Verbindung, die zum Bestimmen der Standardeinstellungen des Servers hergestellt wird; es gilt nicht für folgende Verbindungen, die mit der neuen Datenquelle hergestellt werden.

Sowohl die **Anmelde-ID** und **Kennwort** sind deaktiviert, wenn **mit integrierten Windows-Authentifizierung** oder **mit Active Directory-integriert Authentifizierung** ausgewählt ist.

### <a name="next"></a>Weiter

Setzt den Vorgang mit dem nächsten Bildschirm des Assistenten fort.

### <a name="back"></a>Zurück

Gibt Sie zurück zum vorherigen Bildschirm des Assistenten.

## <a name="next-steps"></a>Nächste Schritte

[Datenquellen-Assistent (Bildschirm 1)](../../../connect/odbc/windows/dsn-wizard-1.md)

[Datenquellen-Assistent (Bildschirm 3)](../../../connect/odbc/windows/dsn-wizard-3.md)

