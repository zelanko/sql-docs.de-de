---
title: Ablaufverfolgungseigenschaften (Registerkarte "Allgemein") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.general.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: 25227268-143b-477e-aac9-8268bcaf2078
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 35e9ee16ee50d5dc697e862b2777db7f0199970d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48184780"
---
# <a name="trace-properties-general-tab"></a>Ablaufverfolgungseigenschaften (Registerkarte Allgemein)
  Mithilfe der Registerkarte **Allgemein** im Dialogfeld **Ablaufverfolgungseigenschaften** können Sie die Eigenschaften einer Ablaufverfolgung anzeigen und festlegen.  
  
## <a name="options"></a>Tastatur  
 **Ablaufverfolgungsname**  
 Gibt den Namen der Ablaufverfolgung an.  
  
 **Name des Ablaufverfolgungsanbieters**  
 Zeigt den Namen der Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] an, für die die Ablaufverfolgung ausgeführt wird. Dieses Feld wird automatisch mit dem Namen des Servers ausgefüllt, den Sie bei der Verbindung angegeben haben. Um den Namen des Ablaufverfolgungsanbieters zu ändern, klicken Sie auf **Abbrechen** , um das Dialogfeld zu schließen, und starten Sie eine neue Ablaufverfolgung.  
  
 **Typ des Ablaufverfolgungsanbieters**  
 Zeigt den Servertyp an, der die Ablaufverfolgung bereitstellt. Das Feld **Typ des Ablaufverfolgungsanbieters** wird automatisch mithilfe der Datei mit den Ablaufverfolgungsdefinitionen ausgefüllt. Sie können diesen Eintrag nicht ändern.  
  
 **version**  
 Zeigt die Version des Servers an, der die Ablaufverfolgung bereitstellt. Das Feld **Version** wird automatisch mithilfe der Datei mit den Ablaufverfolgungsdefinitionen ausgefüllt. Sie können diesen Eintrag nicht ändern.  
  
 **Vorlage verwenden**  
 Wählt eine Vorlage aus dem Vorlagenverzeichnis aus. Das Verzeichnis enthält die Standardvorlagen und alle benutzerdefinierten Vorlagen, die für den aktuellen Typ des Ablaufverfolgungsanbieters erstellt wurden.  
  
 **In Datei speichern**  
 Zeichnet die Ablaufverfolgungsdaten in einer TRC-Datei auf. Das Speichern von Ablaufverfolgungsdaten ist für die spätere Überprüfung und Analyse nützlich.  
  
 **Maximale Dateigröße festlegen (MB)**  
 Wenn Sie die Ablaufverfolgungsdaten in einer Datei speichern, müssen Sie die maximale Größe der Ablaufverfolgungsdatei angeben. Der Standardwert ist 5 MB. Die maximale Größe ist nur durch das Dateisystem (NTFS, FAT) begrenzt, in dem die Datei gespeichert wird.  
  
 \<Grafische > **speichern unter**  
 Nachdem Sie die Option zum Speichern ausgewählt haben, können Sie dieses Symbol verwenden, um den Dateinamen zu ändern.  
  
 **Dateirollover aktivieren**  
 Wählen Sie diese Option, um das Erstellen zusätzlicher Dateien für Ablaufverfolgungsdaten zu ermöglichen, wenn die maximale Dateigröße erreicht wird. Jeder neue Dateiname besteht aus dem ursprünglichen Namen der TRC-Datei mit einer aufsteigenden Nummer. Wenn z. B. für die Datei **NewTrace.trc** die maximale Dateigröße erreicht ist, wird sie geschlossen und eine neue Datei mit dem Namen **NewTrace_1.trc**geöffnet, gefolgt von der Datei **NewTrace_2.trc**usw. Der Dateirollover wird standardmäßig aktiviert, wenn Sie eine Ablaufverfolgung in eine Datei speichern.  
  
 **Ablaufverfolgungsdaten von Serverprozessen**  
 Gibt an, dass der Server, der die Ablaufverfolgung ausführt, die Ablaufverfolgungsdaten verarbeiten soll. Mit dieser Option kann der Verarbeitungsaufwand reduziert werden, der durch die Ablaufverfolgung verursacht wird. Ist sie aktiviert, werden keine Ereignisse ausgelassen, auch nicht unter Belastungsbedingungen. Ist dieses Kontrollkästchen deaktiviert, übernimmt SQL Server Profiler die Verarbeitung. In diesem Fall besteht die Möglichkeit, dass einige Ereignisse bei hoher Belastung nicht verfolgt werden.  
  
 **In Tabelle speichern**  
 Zeichnet die Ablaufverfolgungsdaten in einer Datenbanktabelle auf. Das Speichern von Ablaufverfolgungsdaten ist für die spätere Überprüfung und Analyse nützlich. Durch das Speichern von Ablaufverfolgungsdaten in einer Tabelle kann es jedoch zu einem hohen Verarbeitungsaufwand auf dem Server kommen, auf dem die Ablaufverfolgung gespeichert wird. Vermeiden Sie daher wenn möglich, die Ablaufverfolgungstabelle auf demselben Server zu speichern, für den die Ablaufverfolgung ausgeführt wird.  
  
 \<Grafische > **Zieltabelle**  
 Wenn Sie die Option zum Speichern der Ablaufverfolgungsdaten in einer Datenbanktabelle ausgewählt haben, können Sie auf dieses Symbol klicken, um den Tabellennamen zu ändern.  
  
 **Maximale Zeilenzahl festlegen (in Tausend)**  
 Gibt die Höchstanzahl der Zeilen an, in denen Daten gespeichert werden sollen. Die Standardeinstellung ist 1000 Zeilen.  
  
 **Beendigungszeit für Ablaufverfolgung aktivieren**  
 Legt das Datum und die Uhrzeit für das Ende und das Schließen der Ablaufverfolgung fest.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
