---
title: SQL Server-Anmeldedialogfeld (ODBC) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 58248a2772377ccecba0c701d03276025785c964
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47698058"
---
# <a name="sql-server-login-dialog-box-odbc"></a>Dialogfeld „SQL Server-Anmeldung“ (ODBC)

Wenn Sie eine ODBC-Verbindung aufrufen, ohne ausreichende Informationen anzugeben, damit der Treiber eine Verbindung mit einem SQL-Server herstellen kann, zeigt der ODBC-Treiber das Dialogfeld **SQL Server-Anmeldung** an.

## <a name="options"></a>Tastatur

### <a name="server"></a>Server

Der Name einer Instanz von SQL Server in Ihrem Netzwerk. Wählen Sie einen Server-/Instanzennamen aus der Liste aus, oder geben Sie den Server-/Instanzennamen in das Feld **Server** ein. Optional können Sie mit dem **SQL Server-Konfigurations-Manager** einen Serveralias auf dem Clientcomputer erstellen und diesen Namen in das Feld **Server** eingeben.

Sie können „(local)“ eingeben, wenn Sie den gleichen Computer wie SQL Server verwenden. Sie können anschließend eine Verbindung mit einer lokalen Instanz von SQL Server herstellen, selbst wenn eine nicht vernetzte Version von SQL Server ausgeführt wird.

Weitere Informationen über Servernamen für andere Typen von Netzwerken finden Sie in der SQL Server-Installationsdokumentation in der SQL Server-Onlinedokumentation.

### <a name="authentication-mode"></a>Authentifizierungsmodus

Wählt den Authentifizierungsmodus aus einem der folgenden:
- **SQL Server** mit Anmelde-ID und Kennwort
- **Windows-integrierte** Authentifizierung mithilfe des aktuell angemeldeten Benutzers-Kontos
- **Active Directory-Kennwortauthentifizierung** mit Anmelde-ID und Kennwort
- **Active Directory integrierte** Authentifizierung mithilfe des aktuell angemeldeten Benutzers-Kontos
- **Interaktive Active Directory-Authentifizierung** mit Anmelde-ID

Finden Sie unter [Data Source-Assistent Bildschirm 2](../../../connect/odbc/windows/dsn-wizard-2.md) für Weitere Informationen zu den Authentifizierungsmodi.

### <a name="server-spn"></a>Server-SPN

Wenn Sie eine vertrauenswürdige Verbindung verwenden, können Sie einen Dienstprinzipalnamen (SPN) für den Server angeben.

### <a name="login-id"></a>Login ID

Gibt an, die SQL Server oder Azure Active Directory-Anmelde-ID für die Verbindung verwendet werden sollen, wenn **Authentifizierungsmodus** nastaven NA hodnotu **SQL Server** oder **Active Directory-Kennwortauthentifizierung** oder **Interaktive active Directory**. Andernfalls die **Anmelde-ID** Feld ist deaktiviert.

### <a name="password"></a>Kennwort

Gibt das Kennwort für die SQL Server oder Azure Active Directory Anmelde-ID, die für die Verbindung verwendet wird, wenn **Authentifizierungsmodus** nastaven NA hodnotu **SQL Server** oder **Active Directory-Kennwortauthentifizierung**. Andernfalls die **Kennwort** Feld ist deaktiviert.

### <a name="options"></a>Tastatur

Zeigt die Gruppe **Optionen** an oder blendet sie aus. Die Schaltfläche **Optionen** wird aktiviert, wenn **Server** über einen Wert verfügt.

### <a name="change-password"></a>Ändern des Kennworts

Wenn dieses Kästchen aktiviert wird, werden die Felder **Neues Kennwort** und **Neues Kennwort bestätigen** angezeigt.

### <a name="new-password"></a>Neues Kennwort

Gibt das neue Kennwort an.

### <a name="confirm-new-password"></a>Neues Kennwort bestätigen

Gibt das neue Kennwort zur Bestätigung ein zweites Mal an.

### <a name="database"></a>Datenbank

Gibt die Standarddatenbank an, die für die Verbindung verwendet werden soll. Diese Einstellung überschreibt die für die Anmeldung auf dem Server festgelegte Standarddatenbank. Wenn keine Datenbank angegeben ist, wird für die Verbindung die Standarddatenbank verwendet, die für die Anmeldung auf dem Server angegeben ist.

### <a name="mirror-server"></a>Spiegelserver

Gibt den Namen des Failoverpartners der zu spiegelnden Datenbank an.

### <a name="mirror-spn"></a>Spiegelserver-SPN

Optional können Sie einen SPN für den Spiegelserver angeben. Der SPN für den Spiegelserver wird zur gegenseitigen Authentifizierung zwischen Client und Server verwendet.

### <a name="language"></a>Sprache

Gibt die Landessprache an, die für SQL Server-Systemmeldungen verwendet werden soll. Auf dem Computer, auf dem SQL Server ausgeführt wird, muss dies Sprache installiert sein. Diese Einstellung überschreibt die für die Anmeldung auf dem Server festgelegte Standardsprache. Wenn keine Sprache angegeben ist, wird für die Verbindung die Standardsprache verwendet, die für die Anmeldung auf dem Server angegeben ist.

### <a name="application-name"></a>ApplicationName

(Optional) Gibt den Anwendungsnamen an, der in der Spalte **program_name** in der Zeile für diese Verbindung in **sys.sysprocesses** gespeichert werden soll.

### <a name="workstation-id"></a>Workstation ID

(Optional) Gibt die Workstation ID an, die in der Spalte **hostname** in der Zeile für diese Verbindung in **sys.sysprocesses** gespeichert werden soll.

### <a name="use-strong-encryption-for-data"></a>Starke Verschlüsselung für Daten verwenden

Bei Auswahl dieser Option werden Daten, die über die Verbindung übergeben wird verschlüsselt. Anmeldungen werden standardmäßig verschlüsselt, auch wenn das Kontrollkästchen deaktiviert wird.

### <a name="trust-server-certificate"></a>Serverzertifikat vertrauen

Diese Option ist nur anwendbar, wenn **starke Verschlüsselung für Daten verwenden** aktiviert ist. Bei Auswahl dieser Option wird das Zertifikat des Servers nicht überprüft werden, müssen den richtigen Hostnamen des Servers und von einer vertrauenswürdigen Zertifizierungsstelle ausgestellt werden.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
