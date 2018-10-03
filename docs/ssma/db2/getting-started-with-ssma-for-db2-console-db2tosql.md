---
title: Erste Schritte mit SSMA für DB2-Konsole (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f245c017-023e-4880-8721-8908d339525e
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 472f830f41c5cc9d250a26b8e2612b7c0a6b68b9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728763"
---
# <a name="getting-started-with-ssma--for-db2-console-db2tosql"></a>Erste Schritte mit SSMA für DB2-Konsole (DB2ToSQL)
Dieser Abschnitt beschreibt die Vorgehensweise zum Starten, und beginnen Sie mit der DB2-Konsolenanwendung. Auch aufgeführt ist, werden die Konventionen in diesem Dokument, in einer typischen Ausgabefenster von SSMA-Konsole verwendet.  
  
## <a name="launching-ssma-console"></a>Starten SSMA-Konsole  
Verwenden Sie die folgenden Schritte aus, um die SSMA-Console-Anwendung zu starten:  
  
1.  Wechseln Sie zu **starten** und zeigen Sie auf **Programme**.  
  
2.  Klicken Sie auf die  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migrations-Assistent für die DB2-Eingabeaufforderung** Verknüpfung.  
  
    Klicken Sie im Menü der SSMA-Konsole Nutzung angezeigt und `(/? Help)`, damit Sie mit der Konsolenanwendung zu beginnen.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Verfahren für die Verwendung der SSMA-Konsole  
Nach dem die Konsole wurde erfolgreich auf Ihrem Windows-System gestartet wird, können Sie die folgenden Schritte aus, an einem Projekt arbeiten:  
  
1.  Konfigurieren Sie SSMA-Konsole, über die Skriptdateien. Weitere Informationen in diesem Abschnitt finden Sie unter [Skriptdateien erstellen &#40;DB2ToSQL&#41; ](../../ssma/db2/creating-script-files-db2tosql.md) .  
  
2.  [Erstellen die Variable Value Files &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
  
3.  [Erstellen die Server-Verbindungsdateien &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
4.  [Executing the SSMA Console ausführen &#40;DB2ToSQL&#41; ](../../ssma/db2/executing-the-ssma-console-db2tosql.md) basierend auf Ihrer Projekt-Anforderungen  
  
Zusätzliche Funktionen:  
  
1.  [Verwalten von Kennwörtern](http://msdn.microsoft.com/56d546e3-8747-4169-aace-693302667e94) und exportieren / importieren Sie es auf anderen Computern im Fenster  
  
2.  [Generieren von Berichten](http://msdn.microsoft.com/69ef5fd9-190d-4c58-8199-b3f77d5e1883) Ausgabe Berichte für die Bewertung /conversion und Datenmigration detaillierte Xml anzeigen. Ausführliche Berichte können auch für Aktualisierung und Synchronisierung Befehle generiert werden.  
  
## <a name="ssma-console-output-conventions"></a>SSMA-Konsole Ausgabe Konventionen  
Beim Ausführen der SSMA-Skript-Befehle und Optionen an, das Konsolenprogramm zeigt die Ergebnisse und Meldungen (Informationen, Fehler usw.) für den Benutzer in der Konsole oder ggf. umgeleitet werden, um eine XML-Ausgabedatei. Jede Art von Nachricht in der Ausgabe wird durch eine eindeutige Farbe gekennzeichnet. Beispielsweise gibt die Textnachricht in Weiß Skriptbefehle für die Datei an; in Grün stellt dar, eine Eingabeaufforderung für Benutzereingaben und So weiter.  
  
![SSMA-konsolenausgabe_oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "SSMA-konsolenausgabe_oracle")  
  
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
[Installieren von SSMA für DB2](http://msdn.microsoft.com/79fbe8ea-471b-407a-be2a-4100d9b57c61)  
  
