---
title: SQL Server Profiler - Tools-Optionen (Seite Allgemeine Optionen) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.pro.replay.tools.generaloptions.f1
helpviewer_keywords:
- General Options dialog box
ms.assetid: a888246d-ccfe-415f-bbdc-d6adafac250a
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fed3aec717b21b3c3486d5fd25b27892969de44c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059419"
---
# <a name="sql-server-profiler---tools-options-general-options-page"></a>SQL Server Profiler - Tools-Optionen (Seite Allgemeine Optionen)
  Verwenden Sie das Dialogfeld **Allgemeine Optionen** , um die folgenden Optionen anzuzeigen oder anzugeben.  
  
## <a name="options"></a>Tastatur  
  
### <a name="display-options"></a>Anzeigeoptionen  
 **Schriftartname**  
 Zeigt den Namen der Schriftart an, die im Ergebnisraster der Ablaufverfolgung verwendet wird.  
  
 **Schriftgrad**  
 Zeigt die Größe der Schrift an, die im Ergebnisraster der Ablaufverfolgung verwendet wird.  
  
 **Schriftart auswählen**  
 Öffnet ein Dialogfeld, in dem die Schriftarteinstellungen geändert werden können.  
  
 **Einstellungen für Land/Region zum Anzeigen von Datums- und Uhrzeitwerten verwenden**  
 Zeigt Datums- und Uhrzeitwerte entsprechend den Einstellungen für das Land/die Region an, die für Ihren Computer konfiguriert sind. Wenn Sie diese Option nicht aktivieren, werden die Datums- und Uhrzeitwerte in dem festgelegten Format anzeigt, das von Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verwendet wird und bei dem auch Millisekunden angezeigt werden.  
  
> [!NOTE]  
>  Wenn Sie dieses Kontrollkästchen umschalten, wird das Anzeigeformat der Zeitspalten, z. B. **StartTime** und **EndTime**, geändert. Nicht geändert werden jedoch die **DateTime**-Wertparameter in den Sprachereignissen oder den Remoteprozeduraufrufen (Remote Procedure Calls, RPCs).  
  
 **Werte in der Spalte 'Dauer' in Mikrosekunden anzeigen**  
 Zeigt die Werte in der **Dauer** -Datenspalte bei Ablaufverfolgungen in Mikrosekunden an. Standardmäßig werden die Werte unter **Dauer** in Millisekunden angezeigt.  
  
### <a name="tracing-options"></a>Ablaufverfolgungsoptionen  
 **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten**  
 Startet eine Ablaufverfolgung mithilfe der Standardvorlage, sobald eine Verbindung hergestellt ist.  
  
 **Ablaufverfolgungsdefinition bei Änderung der Anbieterversion aktualisieren**  
 Wendet die neueste Ablaufverfolgungsdefinition auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] an, wenn der Anbieter aktualisiert wird. Diese Option ist standardmäßig nicht aktiviert. Dadurch ist [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] gezwungen, die Ablaufverfolgungsdefinition beim Server abzufragen und, sofern diese vorhanden ist, die Datei auf dem Datenträger neu zu erstellen.  
  
### <a name="file-rollover-options"></a>Dateirolloveroptionen  
 **Alle Rolloverdateien nacheinander ohne Eingabeaufforderung laden**  
 Lädt die Rolloverdateien automatisch, wenn eine Ablaufverfolgungsdatei geöffnet wird. Wenn mehrere Dateien bei der Ablaufverfolgung erstellt wurden, werden bei Auswahl dieser Option alle Rolloverdateien automatisch geladen.  
  
 **Bestätigung vor dem Laden von Rolloverdateien**  
 Legt fest, dass Sie beim Öffnen einer Ablaufverfolgungsdatei von [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] zur Bestätigung aufgefordert werden, bevor eine Rolloverdatei hinzugefügt wird.  
  
 **Nachfolgende Rolloverdateien niemals laden**  
 Verhindert, dass [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] beim Öffnen einer Ablaufverfolgungsdatei nachfolgende Rolloverdateien lädt.  
  
### <a name="replay-options"></a>Wiedergabeoptionen  
 **Standardanzahl von Wiedergabethreads**  
 Gibt die Anzahl der Threads an, die gleichzeitig verwendet werden können. Eine größere Anzahl beansprucht mehr Ressourcen bei der Wiedergabe, erhöht aber die Wiedergabeparallelität.  
  
 **Standardwartezeit für Systemüberwachung (Sek.)**  
 Gibt die Wartezeit für die Wiedergabe in Sekunden an. Der Standardwert ist 3600 Sekunden (1 Stunde). Die Einstellung bestimmt den Zeitraum, in dem ein Thread ausgeführt werden kann, bevor er von der Systemüberwachung beendet wird.  
  
 **Standardabrufintervall für Systemüberwachung (Sek.)**  
 Gibt das Abrufinterval für die Systemüberwachung während der Wiedergabe in Sekunden an. Der Standardwert ist 60 Sekunden. Mit diesem Wert kann der Benutzer konfigurieren, wie oft die Systemüberwachung Informationen zu potenziell zu beendenden Vorgängen abruft.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten eine Ablaufverfolgung automatisch nach dem Herstellen einer Verbindung mit einem Server &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [Legen Sie Ablaufverfolgungsanzeige &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)   
 [Wiedergeben einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Wiedergeben einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Wiedergeben von Ablaufverfolgungen](../tools/sql-server-profiler/replay-traces.md)   
 [Festlegen globaler Ablaufverfolgungsoptionen &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)   
 [Vorlagen und Berechtigungen in SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  