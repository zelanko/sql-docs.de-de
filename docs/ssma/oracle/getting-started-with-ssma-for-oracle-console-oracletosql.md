---
title: Getting Started with SSMA for Oracle Console (oracledesql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle Console, Console Output Conventions
- Oracle Console, Launching Console
ms.assetid: 667a5e4a-6848-4973-a72d-1287f64718ac
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 25cd6eb9c811548e6300c944c65c5530185d46e8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264502"
---
# <a name="getting-started-with-ssma--for-oracle-console-oracletosql"></a>Erste Schritte mit der SSMA-Konsole für Oracle (OracleToSQL)
In diesem Abschnitt wird das Verfahren zum Starten und Starten der Oracle-Konsolenanwendung beschrieben. Hier sind auch die Konventionen aufgeführt, die in einem typischen Ausgabefenster der SSMA-Konsole verwendet werden.  
  
## <a name="launching-ssma-console"></a>Starten der SSMA-Konsole  
Verwenden Sie die folgenden Schritte, um die SSMA-Konsolenanwendung zu starten:  
  
1.  Wechseln Sie zu **Start** , und zeigen Sie auf **Alle Programme**.  
  
2.  Klicken Sie auf die ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verknüpfung Migration Assistant für Oracle-Eingabeaufforderung** .  
  
    Er zeigt das Menü Verwendung der SSMA- `(/? Help)`Konsole und an, um Ihnen den Einstieg in die Konsolenanwendung zu erleichtern.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Verfahren für die Verwendung der SSMA-Konsole  
Nachdem die Konsole erfolgreich auf Ihrem Windows-System gestartet wurde, können Sie die folgenden Schritte ausführen, um Sie zu bearbeiten:  
  
1.  Konfigurieren Sie die SSMA-Konsole über die Skriptdateien. Weitere Informationen zu diesem Abschnitt finden Sie unter [Erstellen von Skriptdateien &#40;oracleto SQL&#41;](../../ssma/oracle/creating-script-files-oracletosql.md) .  
  
2.  [Erstellen von Variablen Wert Dateien &#40;oracleto SQL-&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
3.  [Erstellen der Server Verbindungs Dateien &#40;oracleto SQL-&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
4.  [Ausführen der SSMA-Konsole &#40;oracletosql-&#41;](../../ssma/oracle/executing-the-ssma-console-oracletosql.md) basierend auf Ihren Projektanforderungen  
  
Zusätzliche Funktionen:  
  
1.  [Angeben eines Kennworts](managing-passwords-oracletosql.md) und Exportieren/Importieren dieses Kennworts auf andere Windows-Computer  
  
2.  [Generieren von Berichten](generating-reports-oracletosql.md) zum Anzeigen der detaillierten XML-Ausgabe Berichte für Assessment/Conversion und Datenmigration. Ausführliche Fehlerberichte können auch für Aktualisierungs-und Synchronisierungs Befehle generiert werden.  
  
## <a name="ssma-console-output-conventions"></a>Ausgabe Konventionen der SSMA-Konsole  
Beim Ausführen der SSMA-Skript Befehle und-Optionen zeigt das Konsolenprogramm die Ergebnisse und Meldungen (Informationen, Fehler usw.) an den Benutzer in der-Konsole an oder leitet ggf. eine Umleitung an eine XML-Ausgabedatei. Jeder Nachrichtentyp in der Ausgabe wird durch eine eindeutige Farbe gekennzeichnet. Beispielsweise gibt die Textnachricht in der weißen Farbe Skriptdatei Befehle an. der eine in grüner Farbe stellt eine Eingabeaufforderung für Benutzereingaben dar usw.  
  
![SSMA-Konsolenausgabe_Oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "SSMA-Konsolenausgabe_Oracle")  
  
Farb Interpretation der Konsolenausgabe in der folgenden Tabelle:  
  
|Color|BESCHREIBUNG|  
|---------|---------------|  
|Red|Schwerwiegender Fehler während der Ausführung|  
|Grau|Datums-und Zeitstempel, Meldung an den Benutzer|  
|Weiß|Skriptdatei Befehle, Nachrichtentyp|  
|Gelb|Warnung|  
|Grün|Eingabeaufforderung für Benutzereingabe|  
|Cyan|Starten, beenden und Ergebnis eines Vorgangs|  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für Oracle](installing-ssma-for-oracle-oracletosql.md)  
  
