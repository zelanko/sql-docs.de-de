---
description: Ersten Schritte mit SSMA für die Sybase-Konsole (sybasedesql)
title: Ersten Schritte mit SSMA für die Sybase-Konsole (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: e59cb5565ca518dc927f29e684401bf8fc6d5822
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418316"
---
# <a name="getting-started-with-the-ssma-for-sybase-console-sybasetosql"></a>Ersten Schritte mit SSMA für die Sybase-Konsole (sybasedesql)
In diesem Abschnitt wird das Verfahren zum Starten von und ersten Schritten mit SSMA für die Sybase-Konsolenanwendung beschrieben. Auch hier sind die Konventionen aufgeführt, die in einem typischen Ausgabefenster der SSMA-Konsole verwendet werden.  
  
## <a name="launching-the-ssma-console"></a>Starten der SSMA-Konsole  
Verwenden Sie die folgenden Schritte, um die SSMA-Konsolenanwendung zu starten:  
  
1.  Wechseln Sie zu Start, und zeigen Sie dann auf alle Programme.  
  
2.  Klicken Sie auf den **SQL Server Migration Assistant für die Sybase-Eingabe** Aufforderungs Verknüpfung.  
  
    Er zeigt das Menü Verwendung der SSMA-Konsole und `(/? Help)` an, um Ihnen den Einstieg in die Konsolenanwendung zu erleichtern.  
  
## <a name="using-the-ssma-console"></a>Verwenden der SSMA-Konsole  
Nachdem die Konsole erfolgreich auf Ihrem Windows-System gestartet wurde, können Sie die folgenden Schritte ausführen, um Sie zu bearbeiten:  
  
1.  Konfigurieren Sie die SSMA-Konsole über die Skriptdateien. Weitere Informationen zu diesem Abschnitt finden Sie unter [Erstellen von Skriptdateien &#40;sybasetoisql&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
2.  [Erstellen von Variablen Wert Dateien &#40;sybasedesql&#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [Erstellen der Server Verbindungs Dateien &#40;sybasedesql&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [Das Ausführen der SSMA-Konsole &#40;sybasetosql-&#41;](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) basierend auf Ihren Projektanforderungen. 
  
Zusätzliche Funktionen:  
  
1.  [Geben Sie ein Kennwort](managing-passwords-sybasetosql.md) an, und exportieren/importieren Sie es auf andere Windows-Computer.  
  
2.  [Generieren Sie Berichte](generating-reports-sybasetosql.md) , um die detaillierten XML-Ausgabe Berichte für die Bewertung/Konvertierung und Datenmigration anzuzeigen. Sie können auch ausführliche Fehlerberichte für Aktualisierungs-und Synchronisierungs Befehle generieren.  
  
## <a name="ssma-console-output-conventions"></a>Ausgabe Konventionen der SSMA-Konsole  
Beim Ausführen der SSMA-Skript Befehle und-Optionen zeigt das Konsolenprogramm die Ergebnisse und Meldungen (Informationen, Fehler usw.) an den Benutzer in der-Konsole an oder leitet ggf. eine Umleitung an eine XML-Ausgabedatei ein. Jeder Nachrichtentyp in der Ausgabe wird durch eine eindeutige Farbe gekennzeichnet. Beispielsweise gibt die Textnachricht in der weißen Farbe Skriptdatei Befehle an. der eine in grüner Farbe stellt eine Eingabeaufforderung für Benutzereingaben dar usw.  
  
![SSMAConsoleOutput_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "SSMAConsoleOutput_Sybase")  
  
In der folgenden Tabelle wird die Farb Interpretation der Konsolenausgabe angezeigt:  
  
|Color|BESCHREIBUNG|  
|---------|---------------|  
|Red|Schwerwiegender Fehler während der Ausführung|  
|Grau|Datums-und Zeitstempel, Meldung an den Benutzer|  
|White|Skriptdatei Befehle, Nachrichtentyp|  
|Gelb|Warnung|  
|Grün|Eingabeaufforderung für Benutzereingabe|  
|Cyan|Starten, beenden und Ergebnis eines Vorgangs|  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für SAP ASE &#40;sybasedesql&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
