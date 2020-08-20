---
description: Erste Schritte mit der SSMA-Konsole für MySQL (MySqlToSql)
title: Getting Started with SSMA for MySQL Console (mysqldesql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- MySQL Console, launching console
- MySQL Console, output conventions
ms.assetid: 218d502c-059f-4d48-9aea-61e553d74303
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 9eba640bc529487772510e06a7c66210be3e43a9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463439"
---
# <a name="getting-started-with-ssma-for-mysql-console-mysqltosql"></a>Erste Schritte mit der SSMA-Konsole für MySQL (MySqlToSql)
In diesem Abschnitt wird das Verfahren zum Starten von und ersten Schritten mit der MySQL-Konsolenanwendung beschrieben. Hier sind auch die Konventionen aufgeführt, die in einem typischen Ausgabefenster der SSMA-Konsole verwendet werden.  
  
## <a name="launching-ssma-console"></a>Starten der SSMA-Konsole  
Verwenden Sie die folgenden Schritte, um die SSMA-Konsolenanwendung zu starten:  
  
1.  Wechseln Sie zu **Start** , und zeigen Sie auf **Alle Programme**.  
  
2.  Klicken Sie auf die Verknüpfung **SQL Server Migration Assistant für MySQL-Eingabeaufforderung** .  
  
    Er zeigt das Menü Verwendung der SSMA-Konsole und `(/? Help)` an, um Ihnen den Einstieg in die Konsolenanwendung zu erleichtern.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Verfahren für die Verwendung der SSMA-Konsole  
Nachdem die Konsole erfolgreich auf Ihrem Windows-System gestartet wurde, können Sie die folgenden Schritte ausführen, um Sie zu bearbeiten:  
  
1.  Konfigurieren Sie die SSMA-Konsole über die Skriptdateien. Weitere Informationen zu diesem Abschnitt finden Sie unter [Erstellen von Skriptdateien &#40;mysqltoisql&#41;](../../ssma/mysql/creating-script-files-mysqltosql.md) .  
  
2.  [Erstellen von Variablen Wert Dateien &#40;mysqlto SQL&#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
  
3.  [Erstellen der Server Verbindungs Dateien &#40;mysqldesql&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
4.  [Ausführen der SSMA-Konsole &#40;mysqltosql&#41;](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md) basierend auf Ihren Projektanforderungen  
  
Zusätzliche Funktionen:  
  
1.  [Sichern von Kennwort](managing-passwords-mysqltosql.md) und Exportieren/Importieren dieses Kennworts auf andere Windows-Computer  
  
2.  [Generieren von Berichten](generating-reports-mysqltosql.md) zum Anzeigen der detaillierten XML-Ausgabe Berichte für Assessment/Conversion und Datenmigration. Ausführliche Fehlerberichte können auch für Aktualisierungs-und Synchronisierungs Befehle generiert werden.  
  
## <a name="ssma-console-output-conventions"></a>Ausgabe Konventionen der SSMA-Konsole  
Beim Ausführen der SSMA-Skript Befehle und-Optionen zeigt das Konsolenprogramm die Ergebnisse und Meldungen (Informationen, Fehler usw.) an den Benutzer in der-Konsole an oder leitet ggf. eine Umleitung an eine XML-Ausgabedatei. Jeder Nachrichtentyp in der Ausgabe wird durch eine eindeutige Farbe gekennzeichnet. Beispielsweise gibt die Textnachricht in der weißen Farbe Skriptdatei Befehle an. der eine in grüner Farbe stellt eine Eingabeaufforderung für Benutzereingaben dar usw.  
  
![SSMAConsoleOutput_MySQL](../../ssma/mysql/media/ssmaconsoleoutput_mysql.jpg "SSMAConsoleOutput_MySQL")  
  
Farb Interpretation der Konsolenausgabe in der folgenden Tabelle:  
  
|Color|BESCHREIBUNG|  
|---------|---------------|  
|Red|Schwerwiegender Fehler während der Ausführung|  
|Grau|Datums-und Zeitstempel, Meldung an den Benutzer|  
|White|Skriptdatei Befehle, Nachrichtentyp|  
|Gelb|Warnung|  
|Grün|Eingabeaufforderung für Benutzereingabe|  
|Cyan|Starten, beenden und Ergebnis eines Vorgangs|  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für MySQL](installing-ssma-for-mysql-mysqltosql.md)  
  
