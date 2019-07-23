---
title: Dialog Feld "SQL Server-Anmeldung" (ODBC) | Microsoft-Dokumentation
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
ms.openlocfilehash: fcfde122b978fa1e77baa690a1f3e09417dab1c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989423"
---
# <a name="sql-server-login-dialog-box-odbc"></a>Dialogfeld „SQL Server-Anmeldung“ (ODBC)

Wenn Sie eine ODBC-Verbindung aufrufen, ohne ausreichende Informationen anzugeben, damit der Treiber eine Verbindung mit einem SQL-Server herstellen kann, zeigt der ODBC-Treiber das Dialogfeld **SQL Server-Anmeldung** an.

## <a name="options"></a>enthalten

### <a name="server"></a>Server

Der Name einer Instanz von SQL Server in Ihrem Netzwerk. Wählen Sie einen Server-/Instanzennamen aus der Liste aus, oder geben Sie den Server-/Instanzennamen in das Feld **Server** ein. Optional können Sie mit dem **SQL Server-Konfigurations-Manager** einen Serveralias auf dem Clientcomputer erstellen und diesen Namen in das Feld **Server** eingeben.

Sie können „(local)“ eingeben, wenn Sie den gleichen Computer wie SQL Server verwenden. Sie können anschließend eine Verbindung mit einer lokalen Instanz von SQL Server herstellen, selbst wenn eine nicht vernetzte Version von SQL Server ausgeführt wird.

Weitere Informationen über Servernamen für andere Typen von Netzwerken finden Sie in der SQL Server-Installationsdokumentation in der SQL Server-Onlinedokumentation.

### <a name="authentication-mode"></a>Authentifizierungsmodus

Wählt den Authentifizierungsmodus aus einer der folgenden Aktionen aus:
- **SQL Server** mit Anmelde-ID und Kennwort
- **Integrierte Windows** -Authentifizierung mit dem Konto des aktuell angemeldeten Benutzers
- **Kennwort** mit Anmelde-ID und Kennwort Active Directory
- **Active Directory integrierte** Authentifizierung mit dem Konto des aktuell angemeldeten Benutzers
- **Interaktive Active Directory-Authentifizierung** mit Anmelde-ID

Weitere Informationen zu den Authentifizierungs Modi finden Sie unter [Datenquellen-Assistent (Bildschirm 2](../../../connect/odbc/windows/dsn-wizard-2.md) ).

### <a name="server-spn"></a>Server-SPN

Wenn Sie eine vertrauenswürdige Verbindung verwenden, können Sie einen Dienstprinzipalnamen (SPN) für den Server angeben.

### <a name="login-id"></a>Login ID

Gibt die SQL Server oder Azure Active Directory Anmelde-ID an, die für die Verbindung verwendet werden soll, wenn der **Authentifizierungsmodus** auf **SQL Server** oder **Active Directory Kennwort** oder **Active Directory interaktiv**festgelegt ist. Andernfalls ist das Feld **Anmelde-ID** deaktiviert.

### <a name="password"></a>Kennwort

Gibt das Kennwort für den SQL Server oder Azure Active Directory Anmelde-ID für die Verbindung an, wenn der **Authentifizierungsmodus** auf **SQL Server** oder **Active Directory Kennwort**festgelegt ist. Andernfalls ist das Feld **Kennwort** deaktiviert.

### <a name="options"></a>enthalten

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

Wenn diese Option ausgewählt ist, werden die Daten, die über die Verbindung übermittelt werden, verschlüsselt. Anmeldungen werden standardmäßig verschlüsselt, auch wenn das Kontrollkästchen deaktiviert wird.

### <a name="trust-server-certificate"></a>Serverzertifikat vertrauen

Diese Option ist nur anwendbar, wenn die Option **starke Verschlüsselung für Daten verwenden** aktiviert ist. Wenn diese Option ausgewählt ist, wird das Zertifikat des Servers nicht so überprüft, dass es den richtigen Hostnamen des Servers hat und von einer vertrauenswürdigen Zertifizierungsstelle ausgestellt wird.

## <a name="see-also"></a>Weitere Informationen

[Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
