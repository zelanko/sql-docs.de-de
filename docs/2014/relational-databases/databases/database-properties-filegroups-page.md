---
title: Datenbankeigenschaften (Seite Dateigruppen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.filegroups.f1
ms.assetid: 8d06e859-73dd-4019-b6e8-99c5c5297697
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b8de45556d3c19ee8460b33e7f07ceb485b37597
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62917116"
---
# <a name="database-properties-filegroups-page"></a>Datenbankeigenschaften (Seite Dateigruppen)
  Mithilfe dieser Seite können Sie Dateigruppen anzeigen oder der ausgewählten Datenbank eine neue Dateigruppe hinzufügen. Dateigruppentypen werden in *Zeilen* dateigruppen, FILESTREAM-Datendateigruppen und speicheroptimierte Dateigruppen unterteilt.  
  
 Zeilendateigruppen enthalten reguläre Daten und Protokolldateien. FILESTREAM-Datendateigruppen enthalten FILESTREAM-Datendateien. Diese Datendateien speichern Informationen darüber, wie BLOB (Binary Large Object)-Daten im Dateisystem gespeichert werden, wenn Sie die FILESTREAM-Speicherung verwenden. Die Optionen sind für beide Typen von Dateigruppen gleich.  
  
 Wenn FILESTREAM nicht aktiviert ist, ist der Abschnitt **Filestream** nicht verfügbar. Die FILESTREAM-Speicherung kann über [Servereigenschaften (Seite „Erweitert“)](../../database-engine/configure-windows/server-properties-advanced-page.md)aktiviert werden.  
  
 Weitere Informationen dazu, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeilendateigruppen verwendet, finden Sie unter [Datenbankdateien und Dateigruppen](database-files-and-filegroups.md). Weitere Informationen über FILESTREAM-Daten und -Dateigruppen finden Sie unter [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).  
  
 Speicheroptimierte Dateigruppen sind erforderlich, damit eine Datenbank mindestens eine speicheroptimierte Tabelle enthalten kann.  
  
## <a name="row-and-filestream-data-filegroup-options"></a>Optionen für Zeilen- und FILESTREAM-Datendateigruppen  
 **Name**  
 Geben Sie den Namen der Dateigruppe ein.  
  
 **Dateien**  
 Zeigt die Anzahl der Dateien in der Dateigruppe an.  
  
 **Schreibgeschützt**  
 Wählen Sie diese Option aus, um für die Dateigruppe den schreibgeschützten Modus festzulegen.  
  
 **Standard**  
 Wählen Sie diese Option aus, um diese Dateigruppe zur Standarddateigruppe zu machen. Sie können eine Standarddateigruppe für Zeilen und eine Standarddateigruppe für FILESTREAM-Daten verwenden.  
  
 **Add (Hinzufügen)**  
 Fügt dem Raster mit den Dateigruppen für die Datenbank eine neue leere Zeile hinzu.  
  
 **Remove**  
 Entfernt die ausgewählte Dateigruppenzeile aus dem Raster.  
  
## <a name="memory-optimized-data-filegroup-options"></a>Optionen für speicheroptimierte Datendateigruppen  
 **Name**  
 Geben Sie den Namen der speicheroptimierten Dateigruppe ein.  
  
 **FILESTREAM-Dateien**  
 Zeigt die Anzahl der Dateien (Container) in der speicheroptimierten Datendateigruppe an. Sie können Container auf der Seite **Dateien** hinzufügen.  
  
 **Add (Hinzufügen)**  
 Fügt dem Raster mit den Dateigruppen für die Datenbank eine neue leere Zeile hinzu.  
  
 **Remove**  
 Entfernt die ausgewählte Dateigruppenzeile aus dem Raster.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
