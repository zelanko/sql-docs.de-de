---
title: Optionen (Text-Editor-Transact-SQL-IntelliSense) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Advanced
dev_langs:
- TSQL
ms.assetid: 1855d916-5bf9-4d94-b0fb-9f9bb05ff950
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 7c63a9d226372e155f52f57b473346c9caf7ba1e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332227"
---
# <a name="options-text-editor-transact-sql-intellisense"></a>Optionen (Text-Editor-Transact-SQL-IntelliSense)
  Im Dialogfeld **Optionen** können Sie die IntelliSense-Einstellungen für den [!INCLUDE[ssDE](../includes/ssde-md.md)]-Abfrage-Editor ändern. Diese Einstellungen sind verfügbar, wenn Sie im Menü **Extras** auf **Optionen** klicken. Erweitern Sie den Ordner **Text-Editor**, erweitern Sie den Ordner **Transact-SQL**, und klicken Sie anschließend auf **Erweitert**.  
  
## <a name="transact-sql-intellisense-settings"></a>IntelliSense-Einstellungen für Transact-SQL  
 Gibt die IntelliSense-Optionen für den [!INCLUDE[ssDE](../includes/ssde-md.md)]-Abfrage-Editor an.  
  
### <a name="enable-intellisense"></a>IntelliSense aktivieren  
 Aktiviert die IntelliSense-Funktionen. Wenn dieses Kontrollkästchen nicht aktiviert ist, sind die angegebenen IntelliSense-Optionen nicht verfügbar. Standardmäßig ist dieses Kontrollkästchen aktiviert.  
  
 **Fehler unterstreichen**  
 Identifiziert Syntax- und Semantikfehler in [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen im Abfragefenster. Alle Fehler und Warnungen werden in roter Schrift angezeigt. Fehler und Warnungen werden nur für die [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen unterstützt, für die IntelliSense implementiert wurde. Standardmäßig ist dieses Kontrollkästchen aktiviert.  
  
 **Gliederungsanweisungen**  
 Aktiviert die Gliederungsfunktion beim Öffnen von Dateien. Dadurch werden reduzierbare Blöcke von [!INCLUDE[tsql](../includes/tsql-md.md)] -Code erstellt. Standardmäßig ist dieses Kontrollkästchen aktiviert.  
  
 **Maximale Skriptgröße**  
 Gibt die Größe an, bei der IntelliSense-Funktionalität deaktiviert wird. Wenn ein Skript die angegebene Größe überschreitet, wird eine Warnmeldung ausgegeben. Alle IntelliSense-Funktionen mit Ausnahme von Farbcodierung werden für dieses Editorfenster deaktiviert. IntelliSense wird erneut aktiviert, wenn genug Text gelöscht wurde, um die Skriptgröße auf die maximale Größe zu reduzieren. Das Aktivieren von IntelliSense für große Skripts kann bei langsamen Computern zu Leistungseinbußen führen. Die zulässigen Größen sind 100 KB, 500 KB, 1 MB, 2 MB und Unbegrenzt. Die Standardeinstellung ist 1 MB.  
  
 **Schreibweise für integrierte Funktionsnamen**  
 Gibt an, ob die Namen integrierter [!INCLUDE[tsql](../includes/tsql-md.md)]-Funktionen, die in Vervollständigungslisten enthalten sind, Großbuchstaben verwenden, wie z.B. DATEADD, oder Kleinbuchstaben, wie z.B. dateadd. Wählen Sie die Option aus, die mit den von Ihnen verwendeten [!INCLUDE[tsql](../includes/tsql-md.md)] -Codierungskonventionen am besten übereinstimmt.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei IntelliSense &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/troubleshooting-intellisense.md)  
  
  
