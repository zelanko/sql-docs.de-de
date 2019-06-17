---
title: Skripttask-Beispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], examples
- examples [Integration Services]
- SSIS Script task, examples
ms.assetid: b0dd77ee-ee11-4cd9-87aa-61dd67f2fe1c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d47fa22b8207facc5b4bc22a4077b8bd81837ec2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62768476"
---
# <a name="script-task-examples"></a>Skripttask-Beispiele
  Bei Skripttask handelt es sich um ein Mehrzwecktool, das Sie in einem Paket verwenden können, um nahezu alle Anforderungen zu erfüllen, die von den Tasks nicht erfüllt werden, die in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthalten sind. In diesem Thema werden Skripttaskcodebeispiele aufgeführt, in denen einige der verfügbaren Funktionen veranschaulicht werden.  
  
> [!NOTE]  
>  Wenn Sie Tasks erstellen möchten, die Sie einfacher in mehreren Paketen wiederverwenden können, empfiehlt es sich, den Code in diesen Skripttaskbeispielen als Ausgangspunkt für einen benutzerdefinierten Task zu verwenden. Weitere Informationen finden Sie unter [Entwickeln eines benutzerdefinierten Tasks](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
### <a name="example-topics"></a>Beispielthemen  
 Dieser Abschnitt enthält Codebeispiele, die verschiedene Einsatzbereiche der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Klassen veranschaulichen, die Sie in einen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Skripttask integrieren können:  
  
 [Erkennen einer leeren flachen Datei mit dem Skripttask](../extending-packages-scripting-task-examples/detecting-an-empty-flat-file-with-the-script-task.md)  
 Überprüft eine Flatfile auf vorhandene Datenzeilen, und speichert das Ergebnis in einer Variablen zur Verzweigung der Ablaufsteuerung.  
  
 [Erfassen einer Liste für die ForEach-Schleife mit dem Skripttask](../extending-packages-scripting-task-examples/gathering-a-list-for-the-foreach-loop-with-the-script-task.md)  
 Erstellt eine Liste mit Dateien, die benutzerspezifische Kriterien erfüllen, und füllt eine Variable für den späteren Gebrauch durch den Foreach from-Variablenenumerator.  
  
 [Abfragen des Active Directory mit dem Skripttask](../extending-packages-scripting-task-examples/querying-the-active-directory-with-the-script-task.md)  
 Ruft Benutzerinformationen von Active Directory basierend auf dem Wert einer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Variable ab, indem im System.DirectoryServices-Namespace Klassen verwendet werden.  
  
 [Überwachen von Leistungsindikatoren mit dem Skripttask](../extending-packages-scripting-task-examples/monitoring-performance-counters-with-the-script-task.md)  
 Erstellt einen benutzerdefinierten Leistungsindikator, mit dem der Ausführungsfortschritt eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakets überprüft werden kann, indem im System.Diagnostics-Namespace Klassen verwendet werden.  
  
 [Arbeiten mit Bildern mithilfe des Skripttasks](../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)  
 Komprimiert Bilder in das JPEG-Format und erstellt aus ihnen Miniaturbilder, indem im System.Drawing-Namespace Klassen verwendet werden.  
  
 [Suchen installierter Drucker mit dem Skripttask](../extending-packages-scripting-task-examples/finding-installed-printers-with-the-script-task.md)  
 Sucht installierte Drucker, die ein bestimmtes Papierformat unterstützen, indem im System.Drawing.Printing-Namespace Klassen verwendet werden.  
  
 [Senden einer HTML-E-Mail mit dem Skripttask](../extending-packages-scripting-task-examples/sending-an-html-mail-message-with-the-script-task.md)  
 Sendet eine Mail-Nachricht im HTML-Format anstatt im Nur-Text-Format.  
  
 [Arbeiten mit Excel-Dateien mit dem Skripttask](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
 Listet die Arbeitsblätter in einer Excel-Datei auf und überprüft das Vorhandensein eines bestimmten Arbeitsblatts.  
  
 [Senden mit dem Skripttask an eine private Remotemeldungswarteschlange](../extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)  
 Sendet eine Meldung an eine private Remotenachrichten-Warteschlange.  
  
### <a name="other-examples"></a>Andere Beispiele:  
 Die folgenden Themen enthalten ebenfalls Codebeispiele, die mit dem Skripttask verwendet werden können:  
  
 [Verwenden von Variablen im Skripttask](../extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 Fordert vom Benutzer eine Bestätigung an, ob das Paket weiterhin ausgeführt werden soll, basierend auf dem Wert einer Paketvariablen, der die in einer anderen Variablen festgelegte Begrenzung überschreiten kann.  
  
 [Herstellen einer Verbindung zu Datenquellen im Skripttask](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 Ruft eine Verbindung oder Verbindungsinformationen von Verbindungs-Managern ab, die im Paket definiert sind.  
  
 [Auslösen von Ereignissen im Skripttask](../extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 Gibt einen Fehler, eine Warnung oder eine Meldung basierend auf dem Status der Internetverbindung auf dem Server aus.  
  
 [Protokollieren im Skripttask](../extending-packages-scripting/task/logging-in-the-script-task.md)  
 Protokolliert die Anzahl der Elemente, die vom Task zu aktivierten Protokollanbietern verarbeitet wird.  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  
