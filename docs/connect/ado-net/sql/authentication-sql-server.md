---
title: Authentifizierung in SQL Server
description: Beschreibt die Anmeldung und Authentifizierung in SQL Server und bietet Links zu weiteren Ressourcen.
ms.date: 09/26/2019
dev_langs:
- csharp
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 13676265a7e468065506c31bc2362baf25612512
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "78897048"
---
# <a name="authentication-in-sql-server"></a>Authentifizierung in SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server unterstützt zwei Authentifizierungsmodi: den Windows-Authentifizierungsmodus und den gemischten Modus.  
  
- Die Windows-Authentifizierung ist der Standard. Sie wird häufig auch als "integrierte Sicherheit" bezeichnet, weil dieses SQL Server-Sicherheitsmodell eng in Windows integriert ist. Bestimmte Benutzer- und Gruppenkonten in Windows werden für die Anmeldung bei SQL Server als vertrauenswürdig eingestuft. Windows-Benutzer, die bereits authentifiziert wurden, müssen keine zusätzlichen Anmeldeinformationen eingeben.  
  
- Der gemischte Modus unterstützt die Authentifizierung durch Windows und durch SQL Server. Die Paare aus Benutzername und Kennwort werden innerhalb von SQL Server verwaltet.  
  
> [!IMPORTANT]
> Es wird empfohlen, wenn möglich stets die Windows-Authentifizierung zu verwenden. Die Windows-Authentifizierung verwendet zum Authentifizieren der Benutzer in SQL Server eine Reihe verschlüsselter Nachrichten. Bei der Verwendung von SQL Server-Anmeldungen werden die SQL Server-Anmeldenamen und verschlüsselten Kennwörter über das Netzwerk übertragen und damit angreifbar.  
  
Bei der Windows-Authentifizierung sind die Benutzer bereits bei Windows angemeldet und müssen sich nicht noch einmal bei SQL Server anmelden. Die folgende `SqlConnection.ConnectionString` legt Windows-Authentifizierung fest, bei der Benutzer weder Benutzernamen noch Kennwort angeben müssen.  
  
```csharp
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
> Anmeldungen sind nicht mit Datenbankbenutzern identisch. Sie müssen Anmeldungen oder Windows-Gruppen separat zu Datenbankbenutzern oder -rollen zuordnen. Anschließend erteilen Sie Benutzern oder Rollen Berechtigungen für den Zugriff auf Datenbankobjekte.  
  
## <a name="authentication-scenarios"></a>Authentifizierungsszenarien  
Die Windows-Authentifizierung ist üblicherweise in den folgenden Situationen die beste Wahl:  
  
- Es gibt einen Domänencontroller.  
  
- Die Anwendung und die Datenbank befinden sich auf demselben Computer.  
  
- Sie verwenden eine Instanz von SQL Server Express oder LocalDB.  
  
SQL Server-Anmeldungen werden häufig in den folgenden Situationen verwendet:  
  
- Sie verfügen über eine Arbeitsgruppe.  
  
- Benutzer verbinden sich über unterschiedliche, nicht vertrauenswürdige Domänen.  
  
- Internetanwendungen wie ASP.NET.  
  
> [!NOTE]
> Das Angeben der Windows-Authentifizierung führt nicht zu einer Deaktivierung von SQL Server-Anmeldungen. Wenn Sie die SQL Server-Anmeldungen mit den weit reichenden Berechtigungen deaktivieren möchten, verwenden Sie die Transact-SQL-ALTER LOGIN DISABLE-Anweisung.  
  
## <a name="login-types"></a>Anmeldetypen  
SQL Server unterstützt die folgenden drei Anmeldungstypen:  
  
- Ein lokales Windows-Benutzerkonto oder ein vertrauenswürdiges Domänenkonto. SQL Server nutzt zur Authentifizierung der Windows-Benutzerkonten die Windows-Authentifizierung.  
  
- Windows-Gruppe. Wenn Sie Zugriff für eine Windows-Gruppe gewähren, wird der Zugriff für alle Windows-Benutzeranmeldungen gewährt, die Mitglieder der Gruppe sind.  
  
- SQL Server-Anmeldung. SQL Server speichert den Benutzernamen und einen Hash des Kennworts in der Masterdatenbank. Zur Überprüfung der Anmeldeversuche werden interne Authentifizierungsmethoden verwendet.  
  
> [!NOTE]
> SQL Server stellt auf Grundlage von Zertifikaten oder asymmetrischen Schlüsseln erstellte Anmeldungen bereit, die ausschließlich für die Codesignierung verwendet werden. Sie können nicht verwendet werden, um eine Verbindung mit SQL Server herzustellen.  
  
## <a name="mixed-mode-authentication"></a>Authentifizierung im gemischten Modus  
Wenn die Authentifizierung im gemischten Modus erforderlich ist, müssen Sie SQL Server-Anmeldungen erstellen, die in SQL Server gespeichert werden. Zur Laufzeit müssen dann der SQL Server-Benutzername und das Kennwort angegeben werden.  
  
> [!IMPORTANT]
> SQL Server wird mit der SQL Server-Anmeldung `sa` installiert (eine Abkürzung für „Systemadministrator“). Weisen Sie der Anmeldung `sa` ein sicheres Kennwort zu, und verwenden Sie die Anmeldung `sa` nicht in Ihrer Anwendung. Die Anmeldung `sa` ist der festen Serverrolle `sysadmin` zugeordnet, die über unwiderrufliche Administratoranmeldeinformationen auf dem gesamten Server verfügt. Wenn ein Angreifer Zugriff als Systemadministrator erhält, ist der potenzielle Schaden enorm. Alle Member der Windows-Gruppe `BUILTIN\Administrators` (der lokalen Administratorgruppe) gehören standardmäßig der Rolle `sysadmin` an, können aber aus dieser Rolle entfernt werden.  
  
> [!IMPORTANT]
> Durch das Verketten von Verbindungszeichenfolgen aus Benutzereingaben kann ein System anfällig für Angriffe durch Einschleusung von Verbindungszeichenfolgen werden. Verwenden Sie <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder>, um zur Laufzeit Verbindungszeichenfolgen mit gültiger Syntax zu erstellen. 
  
## <a name="external-resources"></a>Externe Ressourcen  
Weitere Informationen finden Sie in den folgenden Ressourcen.  
  
|Resource|BESCHREIBUNG|  
|--------------|-----------------|  
|[Principals](../../../relational-databases/security/authentication-access/principals-database-engine.md)|Beschreibt Anmeldungen und andere Sicherheitsprinzipale in SQL Server.|  
  
## <a name="next-steps"></a>Nächste Schritte
- [Anwendungssicherheitsszenarios in SQL Server](application-security-scenarios-sql-server.md)
