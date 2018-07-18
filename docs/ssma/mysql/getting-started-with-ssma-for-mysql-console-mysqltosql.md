---
title: Erste Schritte mit SSMA für MySQL Console (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- MySQL Console, launching console
- MySQL Console, output conventions
ms.assetid: 218d502c-059f-4d48-9aea-61e553d74303
caps.latest.revision: 23
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8f33769bee5c8d6d9e134eb9dd5dcf8549d651cb
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983082"
---
# <a name="getting-started-with-ssma-for-mysql-console-mysqltosql"></a>Erste Schritte mit SSMA für MySQL Console (MySQLToSQL))
Dieser Abschnitt beschreibt die Vorgehensweise zum Starten, und beginnen Sie mit der MySQL-Konsolenanwendung. Auch aufgeführt ist, werden die Konventionen in diesem Dokument, in einer typischen Ausgabefenster von SSMA-Konsole verwendet.  
  
## <a name="launching-ssma-console"></a>Starten SSMA-Konsole  
Verwenden Sie die folgenden Schritte aus, um die SSMA-Console-Anwendung zu starten:  
  
1.  Wechseln Sie zu **starten** und zeigen Sie auf **Programme**.  
  
2.  Klicken Sie auf die **SQL Server Migration Assistant für MySQL-Eingabeaufforderung** Verknüpfung.  
  
    Klicken Sie im Menü der SSMA-Konsole Nutzung angezeigt und `(/? Help)`, damit Sie mit der Konsolenanwendung zu beginnen.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Verfahren für die Verwendung der SSMA-Konsole  
Nach dem die Konsole wurde erfolgreich auf Ihrem Windows-System gestartet wird, können Sie die folgenden Schritte aus, an einem Projekt arbeiten:  
  
1.  Konfigurieren Sie SSMA-Konsole, über die Skriptdateien. Weitere Informationen in diesem Abschnitt finden Sie unter [Skriptdateien erstellen &#40;MySQLToSQL&#41; ](../../ssma/mysql/creating-script-files-mysqltosql.md) .  
  
2.  [Erstellen die Variable Value Files &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
  
3.  [Erstellen die Server-Verbindungsdateien &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
4.  [Executing the SSMA Console ausführen &#40;MySQLToSQL&#41; ](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md) basierend auf Ihrer Projekt-Anforderungen  
  
Zusätzliche Funktionen:  
  
1.  [Sichern das Kennwort](http://msdn.microsoft.com/4ffbc587-ea3f-49ad-bc42-a654f672325e) und exportieren / importieren Sie es auf anderen Computern im Fenster  
  
2.  [Generieren von Berichten](http://msdn.microsoft.com/1c0202e8-546d-4cb3-a37f-1d2e35d53839) Ausgabe Berichte für die Bewertung /conversion und Datenmigration detaillierte Xml anzeigen. Ausführliche Berichte können auch für Aktualisierung und Synchronisierung Befehle generiert werden.  
  
## <a name="ssma-console-output-conventions"></a>SSMA-Konsole Ausgabe Konventionen  
Beim Ausführen der SSMA-Skript-Befehle und Optionen an, das Konsolenprogramm zeigt die Ergebnisse und Meldungen (Informationen, Fehler usw.) für den Benutzer in der Konsole oder ggf. umgeleitet werden, um eine XML-Ausgabedatei. Jede Art von Nachricht in der Ausgabe wird durch eine eindeutige Farbe gekennzeichnet. Beispielsweise gibt die Textnachricht in Weiß Skriptbefehle für die Datei an; in Grün stellt dar, eine Eingabeaufforderung für Benutzereingaben und So weiter.  
  
![SSMAConsoleOutput_MySQL](../../ssma/mysql/media/ssmaconsoleoutput_mysql.jpg "SSMAConsoleOutput_MySQL")  
  
Color-Interpretation der Konsolenausgabe in der folgenden Tabelle:  
  
|Farbe|Description|  
|---------|---------------|  
|Red|Schwerwiegender Fehler während der Ausführung|  
|Grau|Datums- und Zeitstempel, an den Benutzer|  
|White|Datei Skriptbefehle, Nachrichtentyp|  
|Gelb|Warnung|  
|Green|Eingabeaufforderung für Benutzereingaben|  
|Cyan|Start, Ende und das Ergebnis eines Vorgangs|  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für MySQL](http://msdn.microsoft.com/e89b45bd-59c1-4d23-8bd7-3dafc1947448)  
  
