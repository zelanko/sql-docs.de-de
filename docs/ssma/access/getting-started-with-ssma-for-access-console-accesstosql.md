---
title: Getting Started with SSMA for Access Console (Access Token) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8585ec16-7e0a-483a-b250-adab9b9232a3
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: e9ca0ef87aac60849d114d0e43dd349e063e8c83
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87938510"
---
# <a name="getting-started-with-ssma-for-access-console-accesstosql"></a>Ersten Schritte mit SSMA für die Zugriffs Konsole (Access Token)
In diesem Abschnitt wird die Vorgehensweise zum Starten und Starten der Zugriffs Konsolenanwendung beschrieben. Hier sind auch die Konventionen aufgeführt, die in einem typischen Ausgabefenster der SSMA-Konsole verwendet werden.  
  
## <a name="launching-ssma-console"></a>Starten der SSMA-Konsole  
Verwenden Sie die folgenden Schritte, um die SSMA-Konsolenanwendung zu starten:  
  
1.  Wechseln Sie zu **Start** , und zeigen Sie auf **Alle Programme**.  
  
2.  Klicken Sie auf die Verknüpfung **Eingabeaufforderung für Zugriff SQL Server Migration Assistant** .  
  
    Er zeigt das Menü Verwendung der SSMA-Konsole und `(/? Help)` an, um Ihnen den Einstieg in die Konsolenanwendung zu erleichtern.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Verfahren für die Verwendung der SSMA-Konsole  
Nachdem die Konsole erfolgreich auf Ihrem Windows-System gestartet wurde, können Sie die folgenden Schritte ausführen, um Sie zu bearbeiten:  
  
1.  Konfigurieren Sie die SSMA-Konsole über die Skriptdateien. Weitere Informationen zu diesem Abschnitt finden Sie unter [Erstellen von Skriptdateien &#40;Access Token&#41;](../../ssma/access/creating-script-files-accesstosql.md).  
  
2.  [Erstellen von Variablen Wert Dateien &#40;Access Token&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
  
3.  [Erstellen der Server Verbindungs Dateien &#40;Access Token&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
4.  [Ausführen der SSMA-Konsole &#40;Access Token&#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md) basierend auf Ihren Projektanforderungen  
  
Zusätzliche Funktionen:  
  
1.  [Angeben eines Kennworts](managing-passwords-accesstosql.md) und Exportieren/Importieren dieses Kennworts auf andere Windows-Computer  
  
2.  [Generieren von Berichten](generating-reports-accesstosql.md) zum Anzeigen der detaillierten XML-Ausgabe Berichte für Assessment/Conversion und Datenmigration. Ausführliche Fehlerberichte können auch für Aktualisierungs-und Synchronisierungs Befehle generiert werden.  
  
## <a name="ssma-console-output-conventions"></a>Ausgabe Konventionen der SSMA-Konsole  
Beim Ausführen der SSMA-Skript Befehle und-Optionen zeigt das Konsolenprogramm die Ergebnisse und Meldungen (Informationen, Fehler usw.) an den Benutzer in der-Konsole an oder leitet ggf. eine Umleitung an eine XML-Ausgabedatei. Jeder Nachrichtentyp in der Ausgabe wird durch eine eindeutige Farbe gekennzeichnet. Beispielsweise gibt die Textnachricht in der weißen Farbe Skriptdatei Befehle an. der eine in grüner Farbe stellt eine Eingabeaufforderung für Benutzereingaben dar usw.  
  
![SSMA-Konsolenausgabe](../../ssma/access/media/ssmaconsoleoutput.jpg "SSMA-Konsolenausgabe")  
  
Farb Interpretation der Konsolenausgabe in der folgenden Tabelle:  
  
|Color|BESCHREIBUNG|  
|---------|---------------|  
|Red|Schwerwiegender Fehler während der Ausführung|  
|Grau|Datums-und Zeitstempel, Meldung an den Benutzer|  
|White|Skriptdatei Befehle, Nachrichtentyp|  
|Gelb|Warnung|  
|Grün|Eingabeaufforderung für Benutzereingabe|  
|Cyan|Starten, beenden und Ergebnis eines Vorgangs|  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SQL Server Migration Assistant für den Zugriff](installing-sql-server-migration-assistant-for-access-accesstosql.md)  
  
