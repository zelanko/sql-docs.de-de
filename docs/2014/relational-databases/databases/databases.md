---
title: Datenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- data warehouse [SQL Server]
- OLTP databases [SQL Server]
- databases [SQL Server], about databases
ms.assetid: 316eea58-81b8-4bf3-a1fc-801946740e94
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea3da64ce6da8cbcb32b5854f14e8d24349c0c25
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970080"
---
# <a name="databases"></a>Datenbanken
  Eine Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] besteht aus einer Auflistung von Tabellen, in der eine bestimmte Menge strukturierter Daten gespeichert ist. Eine Tabelle enthält eine Auflistung von Zeilen, auch als Datensätze oder Tupel bezeichnet, sowie Spalten, auch als Attribute bezeichnet. Jede Spalte in der Tabelle dient zum Speichern eines bestimmten Informationstyps, z. B. Datumsangaben, Namen, Geldbeträge und Zahlen.  
  
## <a name="basic-information-about-databases"></a>Grundlegende Informationen zu Datenbanken  
 Auf einem Computer können eine oder mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert werden. Jede Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann eine Datenbank oder viele Datenbanken enthalten.  Innerhalb einer Datenbank gibt es eine oder mehrere Objektbesitzgruppen, so genannte Schemas. In jedem Schema gibt es Datenbankobjekte wie Tabellen, Sichten und gespeicherte Prozeduren. Einige Objekte, z. B. Zertifikate und asymmetrische Schlüssel, sind in der Datenbank, jedoch nicht in einem Schema enthalten. Weitere Informationen zum Erstellen von Tabellen finden Sie unter [Tables](../tables/tables.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken sind im Dateisystem in Dateien gespeichert. Dateien können in Dateigruppen gruppiert werden. Weitere Informationen zu Dateien und Dateigruppen finden Sie unter [Database Files and Filegroups](database-files-and-filegroups.md).  
  
 Wenn Personen Zugriff auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erhalten, werden sie über einen Anmeldenamen identifiziert. Wenn Personen Zugriff auf eine Datenbank erhalten, werden sie als Datenbankbenutzer identifiziert. Ein Datenbankbenutzer kann auf einer Anmeldung basieren. Wenn eigenständige Datenbanken aktiviert werden, kann ein Datenbankbenutzer erstellt werden, der nicht auf einer Anmeldung basiert. Weitere Informationen über Benutzer finden Sie unter [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
 Einem Benutzer mit Zugriff auf eine Datenbank kann die Berechtigung zum Zugreifen auf die Objekte in der Datenbank erteilt werden. Obwohl Berechtigungen einzelnen Benutzern erteilt werden können, sollten Datenbankrollen erstellt, den Rollen Datenbankbenutzer hinzugefügt und dann Zugriffsberechtigungen für die Rollen erteilt werden. Indem Berechtigungen für Rollen und nicht für Benutzer erteilt werden, können die Berechtigungen leichter konsistent und verständlich gehalten werden, während die Anzahl der Benutzer wächst und sich laufend ändert. Weitere Informationen zu Rollenberechtigungen finden Sie unter [CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql) und [Prinzipale &#40;Datenbank-Engine&#41;](../security/authentication-access/principals-database-engine.md).  
  
## <a name="working-with-databases"></a>Arbeiten mit Datenbanken  
 Die meisten Personen, die mit Datenbanken arbeiten, verwenden das Tool [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Das [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] -Tool besitzt eine grafische Benutzeroberfläche zum Erstellen von Datenbanken und den Objekten in den Datenbanken. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] enthält außerdem einen Abfrage-Editor für die Interaktion mit Datenbanken durch das Schreiben von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] kann vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationsdatenträger installiert oder von MSDN heruntergeladen werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|||  
|-|-|  
|[System Datenbanken](system-databases.md)|[Löschen von Daten- oder Protokolldateien aus einer Datenbank](delete-data-or-log-files-from-a-database.md)|  
|[Eigenständige Datenbanken](contained-databases.md)|[Anzeigen von Informationen zum Daten- und Protokollspeicherplatz einer Datenbank](display-data-and-log-space-information-for-a-database.md)|  
|[SQL Server von Datendateien in Azure](sql-server-data-files-in-microsoft-azure.md)|[Erhöhen der Größe einer Datenbank](increase-the-size-of-a-database.md)|  
|[Datenbankdateien und Dateigruppen](database-files-and-filegroups.md)|[Umbenennen einer Datenbank](rename-a-database.md)|  
|[Datenbankstatus](database-states.md)|[Festlegen des Einzelbenutzermodus für eine Datenbank](set-a-database-to-single-user-mode.md)|  
|[Dateistatus](file-states.md)|[Verkleinern einer Datenbank](shrink-a-database.md)|  
|[Schätzen der Größe einer Datenbank](estimate-the-size-of-a-database.md)|[Verkleinern einer Datei](shrink-a-file.md)|  
|[Kopieren von Datenbanken auf andere Server](copy-databases-to-other-servers.md)|[Anzeigen oder Ändern der Eigenschaften einer Datenbank](view-or-change-the-properties-of-a-database.md)|  
|[Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)|[Anzeigen einer Liste der Datenbanken in einer Instanz von SQL Server](view-a-list-of-databases-on-an-instance-of-sql-server.md)|  
|[Hinzufügen von Daten- oder Protokolldateien zu einer Datenbank](add-data-or-log-files-to-a-database.md)|[Anzeigen oder Ändern des Kompatibilitätsgrads einer Datenbank](view-or-change-the-compatibility-level-of-a-database.md)|  
|[Ändern der Konfigurationseinstellungen für eine Datenbank](change-the-configuration-settings-for-a-database.md)|[Verwenden des Wartungsplanungs-Assistenten](../maintenance-plans/use-the-maintenance-plan-wizard.md)|  
|[Erstellen einer Datenbank](create-a-database.md)|[Erstellen eines benutzerdefinierten Datentypalias](create-a-user-defined-data-type-alias.md)|  
|[Löschen einer Datenbank](delete-a-database.md)|[Datenbank-Momentaufnahmen &#40;SQL Server&#41;](database-snapshots-sql-server.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Indizes](../indexes/indexes.md)  
  
 [Ansichten](../views/views.md)  
  
 [Gespeicherte Prozeduren &#40;Datenbank-Engine&#41;](../stored-procedures/stored-procedures-database-engine.md)  
  
  
