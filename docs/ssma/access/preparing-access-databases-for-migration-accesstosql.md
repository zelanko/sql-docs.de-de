---
title: Vorbereiten der Access-Datenbanken für die Migration (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
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
caps.latest.revision: 20
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: dd412dee3a9265d19e255d23900125691d1a0f9a
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396508"
---
# <a name="preparing-access-databases-for-migration-accesstosql"></a>Vorbereiten der Access-Datenbanken für die Migration (AccessToSQL)
Bevor Sie die Access-Datenbanken migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie müssen bestimmen, welche Datenbanken migrieren, und stellen Sie sicher, dass diese Datenbanken für die Migration bereit sind.  
  
## <a name="determining-when-to-migrate-to-sql-server"></a>Wann müssen die Migration zu SQL Server  
Der Jet-Datenbank-Engine, das als die Datenbank-Engine für den Zugriff verwendet wird, ist eine flexible, einfach zu bedienende Lösung für die datenverwaltung. Allerdings stellen viele Benutzer als größeren Datenbanken und weitere unternehmenskritische, bessere Leistung, Sicherheit oder Verfügbarkeit erfordern. Für Anwendungen, die eine robustere Datenplattform erfordern, sollten Sie das Verschieben der zugrunde liegenden Datenbanken für diese Anwendungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen zu entscheiden, wann zu migrieren, finden Sie unter den [Informationsseite für die Migration](http://go.microsoft.com/fwlink/?LinkId=68571) auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Website.  
  
Nach dem Migrieren von Datenbanken, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], können Sie weiterhin Zugriff zu verwenden, indem Sie verknüpfte Tabellen, oder Sie können manuell migrieren Ihrer Anwendungen in [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework-basierten Code, der direkt mit interagiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="determining-which-databases-to-migrate"></a>Bestimmen der zu migrierenden Datenbanken  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für den Zugriff, können den Zugriff auf Datenbanken Sie suchen. Sie können dann exportieren Sie Metadaten zu diesen Datenbanken dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen zum Exportieren und Abfragen von Metadaten finden Sie unter [Exportieren eines Access-Inventars](exporting-an-access-inventory-accesstosql.md).  

   > [!NOTE]
   > Nicht alle Access-Funktionen und Einstellungen werden von unterstützt und können problemlos konvertiert werden können, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bevor Sie beginnen, Migrieren von Datenbanken, finden Sie unter [inkompatible Access-Features](incompatible-access-features-accesstosql.md).
  
## <a name="preparing-for-migration"></a>Vorbereiten der migration  
Verwenden Sie die folgenden Richtlinien, um die Access-Datenbanken für die Migration zu vorbereiten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="upgrading-older-access-databases"></a>Upgrade von älteren Access-Datenbanken  
SSMA für Access unterstützt Access 97 und höher. Wenn Sie Datenbanken aus früheren Versionen von Access haben, öffnen Sie, und speichern Sie die Datenbanken in Access 97 oder höher.  
  
### <a name="removing-workgroup-protection"></a>Entfernen des Schutzes von Arbeitsgruppe  
SSMA kann keine Datenbanken migrieren, die Arbeitsgruppen-Schutz verwenden. Zum Schutz der Arbeitsgruppe aus einer Access-Datenbank zu entfernen, führen Sie die folgenden Schritte aus:  
  
1.  Access-Datenbankdatei an einen anderen Speicherort zu kopieren.  
  
2.  Öffnen Sie die kopierte Datenbank an.  
  
3.  Auf der **Tools** Startmenü **Sicherheit**, und wählen Sie dann **Benutzer- und Gruppenberechtigungen**.  
  
4.  Wählen Sie die **Benutzer** auswählen, wählen die **Admin** Benutzer, und dann sicherstellen, dass die **verwalten** Berechtigung aktiviert ist.  
  
5.  Wählen Sie die **Gruppen** auswählen, wählen die **Benutzer** gruppieren und dann sicherstellen, dass die **verwalten** Berechtigung aktiviert ist.  
  
6.  Klicken Sie auf **OK**, und klicken Sie dann auf die **Datei** Menü klicken Sie auf **beenden**.  
  
SSMA können Sie jetzt die kopierte Datenbank zu migrieren. Nach dem Laden des Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie können die Datenbank manuell sichern, auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="backing-up-databases"></a>Sichern von Datenbanken  
Bevor Sie Ihre Access-Datenbanken migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sichern Sie sowohl die Access-Datenbanken, die migriert werden soll, sowie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken Sie in den migrieren Zugriff auf Objekte und Daten.  
  
Zum Sichern einer Access-Datenbank auf dem **Tools** Startmenü **-Hilfsprogramme für Datenbanken**, und wählen Sie dann **Datenbank sichern**.  
  
Informationen zum Sichern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken, finden Sie unter "Sichern und Wiederherstellen von Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
### <a name="documenting-databases"></a>Dokumentieren von Datenbanken  
Sie möchten auch die Eigenschaften, z. B. Listen von Datenbankobjekten, Dateigrößen und Berechtigungen der Access-Datenbanken zu dokumentieren. Zum Generieren dieser Dokumentation in Access für die **Tools** Startmenü **analysieren**, und klicken Sie dann auf **dokumentierte**.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Verknüpfen den Zugriff auf Anwendungen mit SQLServer](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)
