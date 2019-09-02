---
title: Datenquellen-Assistent (Bildschirm 2) (ODBC-Treiber für SQL Server) | Microsoft-Dokumentation
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
ms.openlocfilehash: 4ab8be02351a23c78251a99ca707e946ee8944c8
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70152567"
---
# <a name="data-source-wizard-screen-2"></a>Datenquellen-Assistent (Bildschirm 2)

Geben Sie die Authentifizierungsmethode an, und richten Sie Einträge des erweiterten Clients von Microsoft SQL Server sowie den Anmeldenamen und das Kennwort ein, die der ODBC Driver for SQL Server zum Herstellen einer Verbindung mit SQL Server verwendet, während die Datenquelle konfiguriert wird.

## <a name="options"></a>enthalten

### <a name="with-integrated-windows-authentication"></a>Mit integrierter Windows-Authentifizierung

Gibt an, dass der Treiber eine sichere (oder vertrauenswürdige) Verbindung zu einem SQL Server anfordert. Wenn diese Option aktiviert ist, verwendet SQL Server unabhängig vom aktuellen Anmeldesicherheitsmodus auf dem Server die integrierte Anmeldesicherheit, um Verbindungen mit dieser Datenquelle herzustellen. Alle angegebenen Anmelde-IDs oder Kennwörter werden ignoriert. Der SQL Server-Systemadministrator muss ihren Windows-Anmelde Namen mit einer SQL Server Anmelde-ID verknüpft haben (z. b. mit SQL Server Management Studio).

Optional können Sie einen Dienstprinzipalnamen (Service Principal Name, SPN) für den Server angeben.

### <a name="with-active-directory-integrated-authentication"></a>Mit integrierter Active Directory-Authentifizierung

Gibt an, dass der Treiber mithilfe Azure Active Directory bei SQL Server authentifiziert wird. Wenn diese Option aktiviert ist, verwendet SQL Server unabhängig vom aktuellen Anmeldesicherheitsmodus auf dem Server die integrierte Anmeldesicherheit von Azure Active Directory, um Verbindungen mit dieser Datenquelle herzustellen.

### <a name="with-sql-server-authentication"></a>Mit SQL Server-Authentifizierung

Gibt an, dass sich der Treiber bei SQL Server mithilfe einer Anmelde-ID und eines Kennworts authentifiziert.

### <a name="with-active-directory-password-authentication"></a>Mit Active Directory-Kennwortauthentifizierung

Gibt an, dass sich der Treiber bei SQL Server mithilfe einer Azure Active Directory Anmelde-ID und eines Kennworts authentifiziert.

### <a name="with-active-directory-interactive-authentication"></a>Mit interaktiver Active Directory-Authentifizierung

Gibt an, dass sich der Treiber bei SQL Server mithilfe Azure Active Directory interaktiven Modus authentifiziert, indem eine Anmelde-ID angegeben wird. Dadurch wird das Dialogfeld für die Azure-Authentifizierungs Aufforderung angezeigt.

### <a name="login-id"></a>Login ID

Gibt die Anmelde-ID an, die der Treiber beim Herstellen einer Verbindung mit SQL Server verwendet, wenn **SQL Server Authentifizierung mit einer vom Benutzer eingegebenen Anmelde-ID und einem Kennwort** oder **mit Active Directory Kenn Wort Authentifizierung mithilfe einer vom Benutzer eingegebenen Anmelde-ID und eines Kennworts verwendet** oder **mit Active Directory interaktive Authentifizierung mit einer vom Benutzer eingegebenen Anmelde-ID** ausgewählt ist. Die gilt nur für die Verbindung, die zum Bestimmen der Standardeinstellungen des Servers hergestellt wird; es gilt nicht für folgende Verbindungen, die nach dem Erstellen mit der Datenquelle hergestellt werden.

### <a name="password"></a>Kennwort

Gibt das Kennwort an, das der Treiber beim Herstellen einer Verbindung mit SQL Server verwendet, wenn **SQL Server Authentifizierung mit einer vom Benutzer eingegebenen Anmelde-ID und einem Kennwort** oder **mit Active Directory Kenn Wort Authentifizierung mit einer vom Benutzer eingegebenen Anmelde-ID und einem Kennwort verwendet** ist ausgewählt. Die gilt nur für die Verbindung, die zum Bestimmen der Standardeinstellungen des Servers hergestellt wird; es gilt nicht für folgende Verbindungen, die mit der neuen Datenquelle hergestellt werden.

Die Felder **Anmelde-ID** und **Kennwort** sind deaktiviert, wenn **mit integrierter Windows-Authentifizierung** oder **mit Active Directory integrierte Authentifizierung** ausgewählt ist.

### <a name="next"></a>Weiter

Wechselt zum nächsten Bildschirm des Assistenten.

### <a name="back"></a>Zurück

Kehrt zum vorherigen Bildschirm des Assistenten zurück.

## <a name="next-steps"></a>Nächste Schritte

[Datenquellen-Assistent (Bildschirm 1)](../../../connect/odbc/windows/dsn-wizard-1.md)

[Datenquellen-Assistent (Bildschirm 3)](../../../connect/odbc/windows/dsn-wizard-3.md)

