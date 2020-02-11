---
title: Arbeiten mit den Beispiel Konsolen Skriptdateien (mysqltoisql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sample console script files
ms.assetid: 7e6aaa8a-5f5c-414d-9fb8-21e56b9ffaef
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 6dacba33ecbaa7bdeb51d0a31438c3cbdb21969f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67904893"
---
# <a name="working-with-the-sample-console-script-files-mysqltosql"></a>Arbeiten mit den Beispiel Konsolen Skriptdateien (mysqltoisql)
Einige Beispieldateien wurden zusammen mit dem Produkt für die Benutzer Referenz und-Verwendung bereitgestellt. In diesem Abschnitt wird beschrieben, wie Sie diese Skripts problemlos an die Anforderungen der Endbenutzer anpassen können.  
  
## <a name="sample-console-script-files"></a>Beispieldateien für Konsolen Skripts  
Die folgenden Beispiel-Konsolen Skriptdateien, die verschiedene Szenarien abdecken, wurden als Benutzer Verweis bereitgestellt:  
  
-   Serversconnectionfilesample. XML  
  
-   Variablevaluefilesample. XML  
  
-   "Bewermentreportgenerationsample. xml"  
  
-   Sqlstatuementinversionsample. XML  
  
-   "Systemversionanddatamigrationsample. xml"  
  
-   **Serversconnectionfilesample. XML:**  
  
    -   In diesem Beispiel werden die verschiedenen Verbindungs Modi für die Quell-und Zieldatenbank zur Verfügung gestellt, und der Benutzer kann je nach Anforderung einen beliebigen Modus auswählen. Dieses Beispiel enthält die Server Definitionen.  
  
    -   Der Benutzer kann eine Verbindung mit der erforderlichen Datenbank herstellen, indem er einfach die Werte in die erforderlichen Quell-und Zielserver Definitionen ändert. Im Beispiel wurden alle Werte als Variablen Werte bereitgestellt, die in der **Datei variablevaluefilesample. XML**verfügbar sind.  Alle anderen Verbindungsparameter können aus der Verbindungs Datei des Arbeits Servers des Benutzers entfernt werden.  
  
    -   Weitere Informationen zum Herstellen einer Verbindung mit dem Quell-und Zielserver finden Sie unter [Erstellen der Server Verbindungs Dateien &#40;mysqlto SQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md) .  
  
-   **Variablevaluefilesample. XML:** Alle Variablen, die in den Skriptdateien der Beispiel Konsole verwendet wurden `ServersConnectionFileSample.xml` und in dieser Datei sortiert wurden. Um die Beispiel Konsolen Skripts auszuführen, muss der Benutzer einfach die Beispiel Variablen Werte durch benutzerdefinierte Werte ersetzen und diese Datei als zusätzliches Befehlszeilenargument zusammen mit der Skriptdatei übergeben.  
  
    Weitere Informationen zu Variablen Wert Dateien finden Sie unter [Erstellen von Variablen Wert Dateien &#40;mysqlto SQL&#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md).  
  
-   " **Bewermentreportgenerationsample. xml":** In diesem Beispiel kann der Benutzer einen XML-Bewertungsbericht generieren, der vom Benutzer für die Analyse verwendet werden kann, bevor er mit dem konvertieren und Migrieren von Daten beginnt.  
  
    Im `generate-assessment-report` Befehl muss der Benutzer den Variablen Wert (siehe **variablevaluefilesample. XML**) im- `object-name` Attribut auf den Datenbanknamen, der vom Benutzer verwendet wird, zwingend ändern. Abhängig von der Art des angegebenen Objekts muss der `object-type` Wert ebenfalls geändert werden.  
  
    Wenn der Benutzer mehrere Objekte/Datenbanken bewerten muss, kann er mehrere `metabase-object` Knoten angeben, wie im `generate-assessment-report` Beispiel 4 der Beispiel-Konsolen Skriptdatei im Beispiel 4 veranschaulicht.  
  
    Weitere Informationen zum Erstellen von Berichten finden Sie unter [Erstellen von Berichten &#40;mysqldesql&#41;](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
    **Anmerkungen**  
  
    -   Stellen Sie sicher, dass das Befehlszeilenargument der Variablen Wert Datei an die Konsolenanwendung und "variablevaluefilesample. xml" mit den vom Benutzer angegebenen Werten aktualisiert wird.  
  
    -   Stellen Sie sicher, dass das Befehlszeilenargument der Server Verbindungs Datei an die Konsolenanwendung übergeben wird und die Datei "serversconnectionfilesample. xml" mit den korrekten Server Parameterwerten aktualisiert wird.  
  
-   **Sqlstatuementinversionsample. XML:**  
    In diesem Beispiel kann der Benutzer das entsprechende `t-sql` Skript für den Quelldaten Bank `sql` Befehl generieren, der als Eingabe bereitgestellt wird.  
  
    Im `convert-sql-statement` Befehl muss der Benutzer den Variablen Wert (siehe **variablevaluefilesample. XML**) im- `context` Attribut auf den Datenbanknamen, der vom Benutzer verwendet wird, zwingend ändern. Der Benutzer muss auch den `sql` Attribut Wert in den Quelldaten Bank `sql` Befehl ändern, den er zum Konvertieren benötigt.  
  
    Der Benutzer kann auch SQL-Dateien bereitstellen, die konvertiert werden sollen. Dies wurde im Beispiel 4 der `convert-sql-statement` Beispiel Konsolen Skriptdatei des Befehls veranschaulicht.  
  
    > [!NOTE]  
    > Stellen Sie sicher, dass das Befehlszeilenargument der Variablen Wert Datei an die Konsolenanwendung und "variablevaluefilesample. xml" mit den vom Benutzer angegebenen Werten aktualisiert wird.  
  
-   **"Systemversionanddatamigrationsample. xml":**  
     Dieses Beispiel ermöglicht dem Benutzer, eine End-to-End-Migration von der Konvertierung in die Datenmigration durchzuführen. Die Liste der obligatorischen Attributwerte, die geändert werden müssen, ist im folgenden aufgeführt:  
  
    **Befehls Name**  
  
    `map-schema`  
  
    Schema Zuordnung der Quelldatenbank zum Ziel Schema.  
  
    **Attribut**  
  
    -   `source-schema:`Gibt die Quelldatenbank an, die für die Konvertierung erforderlich ist.  
  
    -   `sql-server-schema`: Gibt die Zieldatenbank an, zu der migriert werden soll.  
  
    **Befehls Name**  
  
    `convert-schema`  
  
    1.  Führt eine Schema Konvertierung von der Quelle in das Ziel Schema durch.  
  
    2.  Wenn der Benutzer mehrere Objekte/Datenbanken bewerten muss, kann er mehrere `metabase-object` Knoten angeben, wie im `convert-schema` Beispiel 4 der Beispiel-Konsolen Skriptdatei im Beispiel 4 veranschaulicht.  
  
    **Attribut**  
  
    `object-name`: Geben Sie die Quelldatenbank/den Objektnamen an, der für die Konvertierung erforderlich ist. Stellen Sie sicher, `object-type` dass das entsprechende-Objekt basierend auf dem Objekttyp geändert wird, der im`object-name`  
  
    **Befehls Name**  
  
    `synchronize-target`  
  
    1.  Synchronisiert die Zielobjekte mit der Zieldatenbank.  
  
    2.  Wenn der Benutzer mehrere Objekte/Datenbanken bewerten muss, kann er mehrere `metabase-object` Knoten angeben, wie im `synchronize-target` Beispiel 3 der Beispiel Konsolen Skriptdatei des Befehls dargestellt.  
  
    **Attribut**  
  
    `object-name:`Geben Sie den SQL Server-Datenbank-/Objektnamen an, der erstellt werden soll. Stellen Sie sicher, `object-type` dass das entsprechende-Objekt basierend auf dem Objekttyp geändert wird, der im`object-name`  
  
    **Befehls Name**  
  
    `migrate-data`  
  
    1.  Migriert die Quelldaten zum Ziel.  
  
    2.  Wenn der Benutzer mehrere Objekte/Datenbanken bewerten muss, kann er mehrere `metabase-object` Knoten angeben, wie in `migrate-data` Beispiel 2 der Beispiel-Konsolen Skriptdatei des Befehls veranschaulicht.  
  
    **Attribut**  
  
    `object-name:`Gibt den Namen der Quelldatenbank/-Tabelle an, die für die Migration erforderlich ist. Stellen Sie sicher, `object-type` dass das entsprechende-Objekt basierend auf dem Objekttyp geändert wird, der im`object-name`  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen von Variablen Wert Dateien &#40;mysqlto SQL&#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
[Erstellen der Server Verbindungs Dateien &#40;mysqldesql&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
[Erstellen von Berichten &#40;mysqlto SQL&#41;](../../ssma/mysql/generating-reports-mysqltosql.md)  
  
