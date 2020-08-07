---
title: Vorbereiten von Access-Datenbanken für die Migration (accesstosql) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ermitteln können, welche Access-Datenbanken zu SQL Server oder Azure SQL-Datenbank migriert werden sollen, und stellen Sie sicher, dass diese Datenbanken
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases, versions
- Access databases, when to migrate
- Access databases, workgroup security
- backing up databases
- documenting databases
- files, preparing
- migrating databases, versions
- migrating databases, when to migrate
- versions of Access
- workgroup security
ms.assetid: 9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 038ffa60562a443c916d0143fa432d3e5da87bc4
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87937871"
---
# <a name="preparing-access-databases-for-migration-accesstosql"></a>Vorbereiten von Access-Datenbanken für die Migration (accesstosql)
Bevor Sie Access-Datenbanken zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , müssen Sie die zu migrierenden Datenbanken ermitteln und sicherstellen, dass diese Datenbanken für die Migration bereit sind.  
  
## <a name="determining-when-to-migrate-to-sql-server"></a>Bestimmen, wann die Migration zu SQL Server  
Die Jet-Datenbank-Engine, die als Datenbank-Engine für den Zugriff verwendet wird, ist eine flexible, einfach zu verwendende Lösung für die Datenverwaltung. Wenn die Datenbanken jedoch größer und Unternehmens kritischer werden, stellen viele Benutzer fest, dass Sie eine höhere Leistung, Sicherheit oder Verfügbarkeit erfordern. Erwägen Sie für Anwendungen, die eine stabilere Datenplattform erfordern, das Verschieben der zugrunde liegenden Datenbanken für diese Anwendungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen zur Entscheidung, wann migriert werden soll, finden Sie auf der [Seite Migrations Informationen](https://go.microsoft.com/fwlink/?LinkId=68571) auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Website.  
  
Nachdem Sie Datenbanken zu migriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] haben, können Sie den Zugriff weiterhin mithilfe verknüpfter Tabellen verwenden, oder Sie können Ihre Anwendungen manuell zu [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework basierten Code migrieren, der direkt mit interagiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="determining-which-databases-to-migrate"></a>Bestimmen der zu migrierenden Datenbanken  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) für den Zugriff kann Zugriffs Datenbanken für Sie finden. Anschließend können Sie Metadaten zu diesen Datenbanken in exportieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen zum Exportieren und Abfragen von Metadaten finden Sie unter [Exportieren einer Zugriffs Inventur](exporting-an-access-inventory-accesstosql.md).  

   > [!NOTE]
   > Nicht alle Zugriffs Features und-Einstellungen werden von unterstützt oder können problemlos in konvertiert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Informationen zum Migrieren von Datenbanken finden Sie unter [inkompatible Zugriffs Features](incompatible-access-features-accesstosql.md).
  
## <a name="preparing-for-migration"></a>Vorbereitung auf die Migration  
Verwenden Sie die folgenden Richtlinien, um Ihre Access-Datenbanken für die Migration zu vorzubereiten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="upgrading-older-access-databases"></a>Aktualisieren älterer Access-Datenbanken  
SSMA für Access unterstützt den Zugriff 97 und höhere Versionen. Wenn Sie über Datenbanken früherer Zugriffs Versionen verfügen, können Sie die Datenbanken in Access 97 oder einer höheren Version öffnen und speichern.  
  
### <a name="removing-workgroup-protection"></a>Entfernen des Arbeitsgruppen Schutzes  
SSMA kann keine Datenbanken migrieren, die den Arbeitsgruppen Schutz verwenden. Führen Sie die folgenden Schritte aus, um den Arbeitsgruppen Schutz aus einer Access-Datenbank zu entfernen:  
  
1.  Kopieren Sie die Access-Datenbankdatei an einen anderen Speicherort.  
  
2.  Öffnen Sie die kopierte Datenbank.  
  
3.  Zeigen Sie **im Menü Extras** auf **Sicherheit**, und wählen Sie dann **Benutzer-und Gruppenberechtigungen**aus.  
  
4.  Wählen Sie die Option **Benutzer** aus, wählen Sie den **Administrator** Benutzer aus, und stellen Sie sicher, dass die Berechtigung **Verwalten** ausgewählt ist.  
  
5.  Wählen Sie die Option **Gruppen** aus, wählen Sie die Gruppe **Benutzer** aus, und stellen Sie dann sicher, dass die Berechtigung **Verwalten** ausgewählt ist.  
  
6.  Klicken Sie auf **OK**, und klicken Sie dann im Menü **Datei** auf **Beenden**.  
  
Nun können Sie SSMA verwenden, um die kopierte Datenbank zu migrieren. Nachdem Sie das Schema in geladen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] haben, können Sie die Datenbank auf manuell sichern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="backing-up-databases"></a>Sichern von Datenbanken  
Bevor Sie Ihre Access-Datenbanken zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sollten Sie sowohl die Access-Datenbanken, die Sie migrieren möchten, als auch die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken sichern, in die Sie Access-Objekte und-Daten migrieren möchten.  
  
Zeigen Sie zum Sichern einer Access-Datenbank im **Menü Extras** auf **Daten Bank Dienstprogramme**, und wählen Sie dann **Datenbank sichern**aus.  
  
Weitere Informationen zum Sichern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken finden Sie unter "sichern und Wiederherstellen von Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] " in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation.  
  
### <a name="documenting-databases"></a>Dokumentieren von Datenbanken  
Möglicherweise möchten Sie auch die Eigenschaften, z. b. Listen mit Datenbankobjekten, Dateigrößen und Berechtigungen, von ihren Access-Datenbanken dokumentieren. Um diese Dokumentation in Access zu generieren, zeigen Sie **im Menü Extras** auf **analysieren**, und klicken Sie dann auf **dokumentiert**.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Verknüpfen von Zugriffs Anwendungen mit SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)
