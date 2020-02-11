---
title: SQL Server Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e528b94e51238a06a9776e58693c3093f4bfb831
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091879"
---
# <a name="sql-server-parameters"></a>SQL Server-Parameter
  Legen Sie auf dieser Seite Parameter fest, die der Analyzer für die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Analyse verwendet. Sie können eine, mehrere oder alle Datenbanken sowie Ablaufverfolgungsdateien, die mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] erstellt wurden, und SQL-Batchdateien analysieren.  
  
> [!NOTE]  
>  Einige Upgradeprobleme können nur erkannt werden, wenn Sie Ablaufverfolgungsdateien oder SQL-Batchdateien zur Analyse übermitteln.  
  
## <a name="options"></a>Tastatur  
 **Zu analysierende Datenbank(en)**  
 Um alle Datenbanken zu analysieren, aktivieren Sie das Kontrollkästchen **alle Datenbanken** . Um eine Auswahl von Datenbanken zu analysieren, aktivieren Sie die Kontrollkästchen neben den Datenbanken, die überprüft werden sollen.  
  
 **Ablaufdateien analysieren**  
 Aktivieren Sie dieses Kontrollkästchen, um Ablaufverfolgungsdateien im Dateisystem zu analysieren.  
  
 **Pfad zu Ablaufdatei(en)**  
 Sie können eine oder mehrere Dateien analysieren. Sie können zu einem Speicherort navigieren und mehrere Dateien auswählen, oder Sie können mehrere Dateinamen angeben. Verwenden Sie den vollen Pfadnamen jeder Datei, geben Sie den Dateinamen an, und trennen Sie die Einträge durch einen senkrechten Strich (|).  
  
 Wenn Sie die Option Ablauf **Verfolgungs Datei (en) analysieren**aktivieren, wird **weiter** deaktiviert, bis Sie einen Pfadnamen und einen Dateinamen eingeben.  
  
 **Batch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datei (en) analysieren**  
 Aktivieren Sie dieses Kontrollkästchen, um [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batchdateien im Dateisystem zu analysieren.  
  
 **Pfad zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Batchdatei (en)**  
 Sie können eine oder mehrere Batchdateien analysieren. Sie können zu einem Speicherort navigieren und mehrere Dateien auswählen, oder Sie können mehrere Dateinamen eingeben. Verwenden Sie den vollen Pfadnamen jeder Datei, geben Sie den Dateinamen an, und trennen Sie die Einträge durch einen senkrechten Strich (|).  
  
 Wenn Sie **SQL-Batchdatei (en) analysieren**aktivieren, wird die Schaltfläche **weiter** deaktiviert, bis Sie einen Pfadnamen und einen Dateinamen eingeben.  
  
 **SQL-Batchtrennzeichen**  
 Der Text, der zum Trennen von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungsbatches verwendet wird. Der Standardwert ist " **go**".  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Benutzeroberflächenreferenz des Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
