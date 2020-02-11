---
title: Getting Started with SSMA for DB2 Console (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f245c017-023e-4880-8721-8908d339525e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: fbb0a90d9cfd628e9251a55de3df8b66a22f1ef7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67989651"
---
# <a name="getting-started-with-ssma--for-db2-console-db2tosql"></a>Getting Started with SSMA for DB2 Console (DB2ToSQL)
In diesem Abschnitt wird das Verfahren zum Starten und Starten der DB2-Konsolenanwendung beschrieben. Hier sind auch die Konventionen aufgeführt, die in einem typischen Ausgabefenster der SSMA-Konsole verwendet werden.  
  
## <a name="launching-ssma-console"></a>Starten der SSMA-Konsole  
Verwenden Sie die folgenden Schritte, um die SSMA-Konsolenanwendung zu starten:  
  
1.  Wechseln Sie zu **Start** , und zeigen Sie auf **Alle Programme**.  
  
2.  Klicken Sie auf die ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verknüpfung Migration Assistant für DB2-Eingabeaufforderung** .  
  
    Er zeigt das Menü Verwendung der SSMA- `(/? Help)`Konsole und an, um Ihnen den Einstieg in die Konsolenanwendung zu erleichtern.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Verfahren für die Verwendung der SSMA-Konsole  
Nachdem die Konsole erfolgreich auf Ihrem Windows-System gestartet wurde, können Sie die folgenden Schritte ausführen, um Sie zu bearbeiten:  
  
1.  Konfigurieren Sie die SSMA-Konsole über die Skriptdateien. Weitere Informationen zu diesem Abschnitt finden Sie unter [Erstellen von Skriptdateien &#40;DB2ToSQL&#41;](../../ssma/db2/creating-script-files-db2tosql.md) .  
  
2.  [Erstellen von Variablen Wert Dateien &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
  
3.  [Erstellen der Server Verbindungs Dateien &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
4.  [Ausführen der SSMA-Konsole &#40;DB2ToSQL&#41;](../../ssma/db2/executing-the-ssma-console-db2tosql.md) basierend auf Ihren Projektanforderungen  
  
Zusätzliche Funktionen:  
  
1.  [Verwalten](https://msdn.microsoft.com/56d546e3-8747-4169-aace-693302667e94) von Kenn Wörtern und Exportieren/Importieren von Kenn Wörtern auf andere Windows-Computer  
  
2.  [Erstellen von Berichten](https://msdn.microsoft.com/69ef5fd9-190d-4c58-8199-b3f77d5e1883) zum Anzeigen der detaillierten XML-Ausgabe Berichte für Assessment/Conversion und Datenmigration. Ausführliche Fehlerberichte können auch für Aktualisierungs-und Synchronisierungs Befehle generiert werden.  
  
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
[Installieren von SSMA für DB2](https://msdn.microsoft.com/79fbe8ea-471b-407a-be2a-4100d9b57c61)  
  
