---
title: Datenquellen-Assistent – Bildschirm 2 (ODBC Driver for SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: David-Engel
ms.author: v-jizho2
ms.openlocfilehash: e2e6b323428b1ad8ae188ea65bf10382651d3d71
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928248"
---
# <a name="data-source-wizard-screen-2"></a>Datenquellen-Assistent (Bildschirm 2)

Geben Sie die Authentifizierungsmethode an, und richten Sie Einträge des erweiterten Clients von Microsoft SQL Server sowie den Anmeldenamen und das Kennwort ein, die der ODBC Driver for SQL Server zum Herstellen einer Verbindung mit SQL Server verwendet, während die Datenquelle konfiguriert wird.

## <a name="options"></a>Tastatur

### <a name="with-integrated-windows-authentication"></a>Mit integrierter Windows-Authentifizierung

Gibt an, dass der Treiber eine sichere (oder vertrauenswürdige) Verbindung mit einer SQL Server-Instanz anfordert. Wenn diese Option aktiviert ist, verwendet SQL Server unabhängig vom aktuellen Anmeldesicherheitsmodus auf dem Server die integrierte Anmeldesicherheit, um Verbindungen mit dieser Datenquelle herzustellen. Alle angegebenen Anmelde-IDs oder Kennwörter werden ignoriert. Der SQL Server-Systemadministrator muss Ihren Windows-Anmeldenamen mit einer SQL Server-Anmelde-ID verknüpft haben (beispielsweise in SQL Server Management Studio).

Optional können Sie einen Dienstprinzipalnamen (Service Principal Name, SPN) für den Server angeben.

### <a name="with-active-directory-integrated-authentication"></a>Mit integrierter Active Directory-Authentifizierung

Gibt an, dass der Treiber sich unter Verwendung von Azure Active Directory bei SQL Server authentifiziert. Wenn diese Option aktiviert ist, verwendet SQL Server unabhängig vom aktuellen Anmeldesicherheitsmodus auf dem Server die integrierte Anmeldesicherheit von Azure Active Directory, um Verbindungen mit dieser Datenquelle herzustellen.

### <a name="with-sql-server-authentication"></a>Mit SQL Server-Authentifizierung

Gibt an, dass der Treiber sich mit einer Anmelde-ID und dem zugehörigen Kennwort bei SQL Server authentifiziert.

### <a name="with-active-directory-password-authentication"></a>Mit Active Directory-Kennwortauthentifizierung

Gibt an, dass der Treiber sich mit einer Azure Active Directory-Anmelde-ID und dem zugehörigen Kennwort bei SQL Server authentifiziert.

### <a name="with-active-directory-interactive-authentication"></a>Mit interaktiver Active Directory-Authentifizierung

Gibt an, dass der Treiber sich mit dem interaktiven Azure Active Directory-Modus und der Angabe einer Anmelde-ID bei SQL Server authentifiziert. Dadurch wird das Dialogfeld zur Eingabe der Azure-Authentifizierungsdaten ausgelöst.

### <a name="login-id"></a>Login ID

Gibt die Anmelde-ID an, die der Treiber beim Herstellen einer Verbindung mit SQL Server verwendet, wenn eine der folgenden Optionen ausgewählt ist: **Mit SQL Server-Authentifizierung anhand der vom Benutzer eingegebenen Anmelde-ID und des Kennworts** oder **Mit Active Directory-Kennwortauthentifizierung über eine vom Benutzer eingegebene Anmelde-ID und ein Kennwort** oder **Mit interaktiver Active Directory-Authentifizierung anhand einer vom Benutzer eingegebenen Anmelde-ID**. Die gilt nur für die Verbindung, die zum Bestimmen der Standardeinstellungen des Servers hergestellt wird; es gilt nicht für folgende Verbindungen, die nach dem Erstellen mit der Datenquelle hergestellt werden.

### <a name="password"></a>Kennwort

Gibt das Kennwort an, das der Treiber beim Herstellen einer Verbindung mit SQL Server verwendet, wenn eine der folgenden Optionen ausgewählt ist: **Mit SQL Server-Authentifizierung anhand der vom Benutzer eingegebenen Anmelde-ID und des Kennworts** oder **Mit Active Directory-Kennwortauthentifizierung über eine vom Benutzer eingegebene Anmelde-ID und ein Kennwort**. Die gilt nur für die Verbindung, die zum Bestimmen der Standardeinstellungen des Servers hergestellt wird; es gilt nicht für folgende Verbindungen, die mit der neuen Datenquelle hergestellt werden.

Sowohl das Feld für **Anmelde-ID** als auch das Feld für **Kennwort** sind deaktiviert, wenn **Mit integrierter Windows-Authentifizierung** oder **Mit integrierter Active Directory-Authentifizierung** ausgewählt ist.

### <a name="next"></a>Next (Weiter)

Wechselt zum nächsten Bildschirm des Assistenten

### <a name="back"></a>Zurück

Kehrt zum vorherigen Bildschirm des Assistenten zurück

## <a name="next-steps"></a>Nächste Schritte

[Datenquellen-Assistent (Bildschirm 1)](../../../connect/odbc/windows/dsn-wizard-1.md)

[Datenquellen-Assistent (Bildschirm 3)](../../../connect/odbc/windows/dsn-wizard-3.md)

