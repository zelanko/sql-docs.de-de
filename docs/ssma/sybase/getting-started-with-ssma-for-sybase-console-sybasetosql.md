---
title: Erste Schritte mit SSMA für Sybase-Konsole (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4a94afc188ce7fe1ce758586a78e523908c49b1d
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980642"
---
# <a name="getting-started-with-the-ssma-for-sybase-console-sybasetosql"></a>Erste Schritte mit SSMA für Sybase-Konsole (SybaseToSQL)
Dieser Abschnitt beschreibt das Verfahren zum Starten und erste Schritte mit SSMA für Sybase-Konsolenanwendung. Auch hier aufgeführt werden die Konventionen in einer typischen Ausgabefenster von SSMA-Konsole verwendet.  
  
## <a name="launching-the-ssma-console"></a>Starten der SSMA-Konsole  
Verwenden Sie die folgenden Schritte aus, um die SSMA-Console-Anwendung zu starten:  
  
1.  Wechseln Sie zu starten, und klicken Sie dann nacheinander auf alle Programme.  
  
2.  Klicken Sie auf die **SQL Server Migration Assistant für Sybase-Eingabeaufforderung** Verknüpfung.  
  
    Klicken Sie im Menü der SSMA-Konsole Nutzung angezeigt und `(/? Help)`, damit Sie mit der Konsolenanwendung zu beginnen.  
  
## <a name="using-the-ssma-console"></a>Mithilfe der SSMA-Konsole  
Nachdem Sie die Konsole wurde erfolgreich auf Ihrem Windows-System gestartet wird, können Sie die folgenden Schritte aus, an einem Projekt arbeiten:  
  
1.  Konfigurieren Sie SSMA-Konsole, über die Skriptdateien. Weitere Informationen in diesem Abschnitt finden Sie unter [Skriptdateien erstellen &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
2.  [Erstellen die Variable Value Files &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [Erstellen die Server-Verbindungsdateien &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [Executing the SSMA Console ausführen &#40;SybaseToSQL&#41; ](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) basierend auf den Anforderungen Ihrer Projekte. 
  
Zusätzliche Funktionen:  
  
1.  [Geben Sie ein Kennwort](http://msdn.microsoft.com/9b6a70f9-6840-4140-a059-bb7bd7ccc67c) und Import-/es auf anderen Computern im Fenster.  
  
2.  [Generieren von Berichten](http://msdn.microsoft.com/19278f6a-6d58-4867-9d71-c6228040466e) Ausgabe Berichte für die Bewertung/Konvertierung und Datenmigration detaillierte Xml anzeigen. Sie können auch ausführliche Fehlerberichte für Aktualisierung und Synchronisierung-Befehle generieren.  
  
## <a name="ssma-console-output-conventions"></a>SSMA-Konsole Ausgabe Konventionen  
Beim Ausführen der SSMA-Skript-Befehle und Optionen an, das Konsolenprogramm zeigt die Ergebnisse und Meldungen (Informationen, Fehler usw.) für den Benutzer in der Konsole oder bei Bedarf leitet in eine XML-Ausgabedatei. Jede Art von Nachricht in der Ausgabe wird durch eine eindeutige Farbe gekennzeichnet. Beispielsweise gibt die Textnachricht in Weiß Skriptbefehle für die Datei an; in Grün stellt dar, eine Eingabeaufforderung für Benutzereingaben und So weiter.  
  
![SSMAConsoleOutput_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "SSMAConsoleOutput_Sybase")  
  
Color-Interpretation der Konsolenausgabe wird in der folgenden Tabelle angezeigt:  
  
|Farbe|Description|  
|---------|---------------|  
|Red|Schwerwiegender Fehler während der Ausführung|  
|Grau|Datums- und Zeitstempel, an den Benutzer|  
|White|Datei Skriptbefehle, Nachrichtentyp|  
|Gelb|Warnung|  
|Green|Eingabeaufforderung für Benutzereingaben|  
|Cyan|Start, Ende und Ergebnis eines Vorgangs|  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
