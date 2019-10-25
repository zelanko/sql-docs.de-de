---
title: Authentifizierung in SQL Server
description: Beschreibt Anmeldungen und Authentifizierung in SQL Server und enthält Links zu weiteren Ressourcen.
ms.date: 09/26/2019
dev_langs:
- csharp
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: eb528eb1045788469b0eb31491fd654997831468
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452310"
---
# <a name="authentication-in-sql-server"></a>Authentifizierung in SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server unterstützt zwei Authentifizierungsmodi: den Windows-Authentifizierungsmodus und den gemischten Modus.  
  
- Die Windows-Authentifizierung ist der Standard. Sie wird häufig auch als "integrierte Sicherheit" bezeichnet, weil dieses SQL Server-Sicherheitsmodell eng in Windows integriert ist. Bestimmte Windows-Benutzer-und-Gruppenkonten sind zum Anmelden bei SQL Server vertrauenswürdig. Windows-Benutzer, die bereits authentifiziert wurden, müssen keine zusätzlichen Anmelde Informationen darstellen.  
  
- Der gemischte Modus unterstützt die Authentifizierung durch Windows und durch SQL Server. Die Paare aus Benutzername und Kennwort werden innerhalb von SQL Server verwaltet.  
  
> [!IMPORTANT]
> Es wird empfohlen, möglichst die Windows-Authentifizierung zu verwenden. Die Windows-Authentifizierung verwendet zum Authentifizieren der Benutzer in SQL Server eine Reihe verschlüsselter Nachrichten. Bei der Verwendung von SQL Server-Anmeldungen werden die SQL Server-Anmeldenamen und verschlüsselten Kennwörter über das Netzwerk übertragen und damit angreifbar.  
  
Bei der Windows-Authentifizierung sind die Benutzer bereits bei Windows angemeldet und müssen sich nicht noch einmal bei SQL Server anmelden. Die folgende `SqlConnection.ConnectionString` legt Windows-Authentifizierung fest, bei der Benutzer weder Benutzernamen noch Kennwort angeben müssen.  
  
```csharp
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
> Anmeldungen unterscheiden sich von Datenbankbenutzern. Sie müssen Anmeldungen oder Windows-Gruppen in einem separaten Vorgang Datenbankbenutzern oder-Rollen zuordnen. Anschließend erteilen Sie Benutzern oder Rollen Berechtigungen für den Zugriff auf Datenbankobjekte.  
  
## <a name="authentication-scenarios"></a>Authentifizierungsszenarien  
Die Windows-Authentifizierung ist in den folgenden Situationen in der Regel die beste Wahl:  
  
- Es ist ein Domänen Controller vorhanden.  
  
- Die Anwendung und die Datenbank befinden sich auf demselben Computer.  
  
- Sie verwenden eine Instanz von SQL Server Express oder LocalDB.  
  
SQL Server Anmeldungen werden häufig in den folgenden Situationen verwendet:  
  
- Wenn Sie über eine Arbeitsgruppe verfügen.  
  
- Benutzer stellen eine Verbindung aus verschiedenen, nicht vertrauenswürdigen Domänen her.  
  
- Internet Anwendungen, z. b. ASP.net.  
  
> [!NOTE]
> Das Angeben der Windows-Authentifizierung führt nicht zu einer Deaktivierung von SQL Server-Anmeldungen. Wenn Sie die SQL Server-Anmeldungen mit den weit reichenden Berechtigungen deaktivieren möchten, verwenden Sie die Transact-SQL-ALTER LOGIN DISABLE-Anweisung.  
  
## <a name="login-types"></a>Anmelde Typen  
SQL Server unterstützt die folgenden drei Anmeldungstypen:  
  
- Ein lokales Windows-Benutzerkonto oder ein vertrauenswürdiges Domänen Konto. SQL Server nutzt zur Authentifizierung der Windows-Benutzerkonten die Windows-Authentifizierung.  
  
- Windows-Gruppe. Wenn Sie Zugriff auf eine Windows-Gruppe gewähren, wird der Zugriff auf alle Windows-Benutzeranmeldungen gewährt, die Mitglieder der Gruppe sind.  
  
- SQL Server-Anmeldung. SQL Server speichert den Benutzernamen und einen Hash des Kennworts in der Masterdatenbank. Zur Überprüfung der Anmeldeversuche werden interne Authentifizierungsmethoden verwendet.  
  
> [!NOTE]
> SQL Server stellt auf Grundlage von Zertifikaten oder asymmetrischen Schlüsseln erstellte Anmeldungen bereit, die ausschließlich für die Codesignierung verwendet werden. Sie können nicht verwendet werden, um eine Verbindung mit SQL Server herzustellen.  
  
## <a name="mixed-mode-authentication"></a>Authentifizierung im gemischten Modus  
Wenn die Authentifizierung im gemischten Modus erforderlich ist, müssen Sie SQL Server-Anmeldungen erstellen, die in SQL Server gespeichert werden. Zur Laufzeit müssen dann der SQL Server-Benutzername und das Kennwort angegeben werden.  
  
> [!IMPORTANT]
> SQL Server wird mit einem SQL Server-Anmelde Namen mit dem Namen `sa` (einer Abkürzung von "Systemadministrator") installiert. Weisen Sie der `sa` Anmeldung ein sicheres Kennwort zu, und verwenden Sie nicht die `sa` Anmeldung in Ihrer Anwendung. Der `sa`-Anmelde Name wird der `sysadmin` Fixed-Server Rolle zugeordnet, die über unwiderrufliche administrative Anmelde Informationen auf dem gesamten Server verfügt. Es gibt keine Beschränkungen für die potenziellen Schäden, wenn ein Angreifer als Systemadministrator Zugriff erhält. Alle Member der Windows-Gruppe `BUILTIN\Administrators` (der lokalen Administratorgruppe) gehören standardmäßig der Rolle `sysadmin` an, können aber aus dieser Rolle entfernt werden.  
  
> [!IMPORTANT]
> Durch das Verketten von Verbindungs Zeichenfolgen von Benutzereingaben können Sie für einen einschleusungs Angriff der Verbindungs Zeichenfolge anfällig Verwenden Sie die <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder>, um zur Laufzeit syntaktisch gültige Verbindungs Zeichenfolgen zu erstellen. 
  
## <a name="external-resources"></a>Externe Ressourcen  
Weitere Informationen finden Sie in den folgenden Ressourcen.  
  
|Ressource|und Beschreibung|  
|--------------|-----------------|  
|[Principals](../../../relational-databases/security/authentication-access/principals-database-engine.md)|Beschreibt Anmeldungen und andere Sicherheitsprinzipale in SQL Server.|  
  
## <a name="next-steps"></a>Nächste Schritte
- [Anwendungssicherheitsszenarios in SQL Server](application-security-scenarios-sql-server.md)
