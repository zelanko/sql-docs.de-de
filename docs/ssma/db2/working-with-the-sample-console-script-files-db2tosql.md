---
title: Arbeiten mit der Konsole Beispielskriptdateien (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5c3080c3-d074-4f99-a5f5-219ebeddc474
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: ca2a595eb57d01554aa8389b002fcd6f8422b9da
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086171"
---
# <a name="working-with-the-sample-console-script-files-db2tosql"></a>Arbeiten mit der Konsole Beispielskriptdateien (DB2ToSQL)
Einige Beispieldateien wurden für die Benutzer-Verweis und die Verwendung zusammen mit dem Produkt bereitgestellt. Dieser Abschnitt beschreibt die Möglichkeit, diese Skripts entsprechend die Anforderungen der Endbenutzer leicht anpassen.  
  
## <a name="sample-console-script-files"></a>Beispielskriptdateien der Konsole  
Referenz für den Benutzer haben die folgenden Konsole beispielskriptdateien für verschiedene Szenarien bereitgestellt wurde:  
  
-   ServersConnectionFileSample.xml  
  
-   VariableValueFileSample.xml  
  
-   AssessmentReportGenerationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
1.  **ServersConnectionFileSample.xml:**  
  
    -   In diesem Beispiel gibt die verschiedenen Modi der Verbindung verfügbar, mit der Quelle und Ziel-Datenbank und der Benutzer kann einem anderen Modus gemäß der Anforderung auswählen. Dieses Beispiel enthält die Serverdefinitionen.  
  
    -   Der Benutzer kann einfach die Werte ändern, um die erforderlichen Quell- und Ziel-Serverdefinitionen mit der erforderlichen Datenbank verbinden. Im Beispiel alle Werte wurde bereitgestellt, z.B. Variablenwerte, die in verfügbar sind die **VariableValueFileSample.xml**.  Alle anderen Verbindungsparameter können aus der Verbindung des Benutzers arbeiten Serverdatei entfernt werden.  
  
    -   Weitere Informationen zum Herstellen einer Verbindung mit der Quelle und Ziel-Server finden Sie unter [erstellen den Server Connection Files &#40;DB2ToSQL&#41; ](../../ssma/db2/creating-the-server-connection-files-db2tosql.md) .  
  
2.  **VariableValueFileSample.xml:** Alle Variablen, die in der Beispielkonsole verwendet wurden, Skriptdateien und `ServersConnectionFileSample.xml` haben in dieser Datei sortiert wurden. Werte mit Benutzer definiert, welche und übergeben Sie diese Datei als ein zusätzliches Befehlszeilenargument zusammen mit der Skriptdatei, zum Ausführen der Beispiel-Console-Skripts, die der Benutzer hat die Variable Beispiel einfach zu ersetzen.  
  
    Weitere Informationen zu der Datei mit Variablen Werten, finden Sie unter [erstellen Variable Value Files &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md).  
  
3.  **AssessmentReportGenerationSample.xml:** In diesem Beispiel kann der Benutzer ein XML-Bewertungsbericht generieren, die verwendet kann vom Benutzer für die Analyse, bevor er beginnt, konvertieren und Migrieren von Daten.  
  
    In der `generate-assessment-report` Befehl, der Benutzer hat den Wert den Variablen Zwischenschritte ändern (finden Sie unter **VariableValueFileSample.xml**) in der `object-name` -Attribut auf die Datenbank Namen an, von dem Benutzer verwendet wird. Je nach Art des Objekts angegeben wird die `object-type` Wert müssen auch geändert werden.  
  
    Wenn der Benutzer verfügt über mehrere Objekte bewerten / er Datenbanken können angeben, mehrere `metabase-object` Knoten wie in der `generate-assessment-report` des Befehls Beispiel 4 von der Konsole-Beispielskriptdatei.  
  
    Weitere Informationen zum Erstellen von Berichten finden Sie unter [Generieren von Berichten &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md).  
  
    **Hinweise:**  
  
    Sicherstellen, dass der Wert der Variablen Befehlszeilenargument-Datei an die Konsolenanwendung übergeben wird und VariableValueFileSample.xml wird mit den angegebenen Benutzer aktualisiert Werte.  
  
    Stellen Sie sicher, dass Befehlszeilenargument für Server Connection-Datei an die Konsolenanwendung übergeben wird und die ServersConnectionFileSample.xml mit Parameterwerten für die richtigen Server aktualisiert wird.  
  
4.  **SqlStatementConversionSample.xml:** In diesem Beispiel kann der Benutzer die entsprechenden generieren `t-sql` Skript für die Quelldatenbank `sql` Befehls als Eingabe.  
  
    In der `convert-sql-statement` Befehl, der Benutzer hat den Wert den Variablen Zwischenschritte ändern (finden Sie unter **VariableValueFileSample.xml**) in der `context` -Attribut auf den Namen der Datenbank, die von dem Benutzer verwendet wird. Der Benutzer benötigen Sie auch so ändern Sie die `sql` -Attributwert auf die Quelldatenbank `sql` -Befehl, der er konvertiert werden müssen.  
  
    Der Benutzer bieten auch Sql-Dateien konvertiert werden. Dies wurde veranschaulicht, der `convert-sql-statement` des Befehls Beispiel 4 von der Konsole-Beispielskriptdatei.  
  
    > [!NOTE]  
    > Sicherstellen, dass der Wert der Variablen Befehlszeilenargument-Datei an die Konsolenanwendung übergeben wird und VariableValueFileSample.xml wird mit den angegebenen Benutzer aktualisiert Werte.  
  
5.  **ConversionAndDataMigrationSample.xml:** In diesem Beispiel kann der Benutzer eine End-to-End-Migration von der Konvertierung in die Datenmigration ausführen. Die Liste der erforderlichen Attributwerte, die sie ändern müssen, ist im folgenden aufgeführt:  
  
    |Befehlsname|Beschreibung|Attribut|  
    |----------------|---------------|-------------|  
    |`map-schema`|Schemazuordnung der Quelldatenbank mit dem Zielschema.|`source-schema:` Gibt an, die Quelldatenbank, die erforderlich sind, konvertiert werden soll.<br /><br />`sql-server-schema`: Gibt die Zieldatenbank, die für die Migration|  
    |`convert-schema`|Führt die schemakonvertierung aus der Quelle in das Zielschema.<br /><br />Wenn der Benutzer verfügt über mehrere Objekte bewerten / er Datenbanken können angeben, mehrere `metabase-object` Knoten wie in der `convert-schema` des Befehls Beispiel 4 von der Konsole-Beispielskriptdatei.|`object-name`: Geben Sie die Quelldatenbank / Objektnamen Sie, die erforderlich sind, konvertiert werden soll. Sicherstellen, dass die entsprechenden `object-type` basierend auf dem Typ des Objekts, das im angegebenen geändert wird die `object-name`|  
    |`synchronize-target`|Synchronisiert die Zielobjekte mit der Zieldatenbank an.<br /><br />Wenn der Benutzer verfügt über mehrere Objekte bewerten / er Datenbanken können angeben, mehrere `metabase-object` Knoten wie in der `synchronize-target` des Befehls Beispiel 3 von der Konsole-Beispielskriptdatei.|`object-name:` Geben Sie die Sql Server-Datenbank / Objektnamen Sie, die erforderlich sind, erstellt werden. Sicherstellen, dass die entsprechenden `object-type` basierend auf dem Typ des Objekts, das im angegebenen geändert wird die `object-name`|  
    |`migrate-data`|Werden die Quelldaten zum Ziel migriert.<br /><br />Wenn der Benutzer verfügt über mehrere Objekte bewerten / er Datenbanken können angeben, mehrere `metabase-object` Knoten wie in der `migrate-data` des Befehls Beispiel 2 von der Konsole-Beispielskriptdatei.|`object-name:` Gibt an, die Quelldatenbank / Tabellen an, der migriert werden muss. Sicherstellen, dass die entsprechenden `object-type` basierend auf dem Typ des Objekts, das im angegebenen geändert wird die `object-name`|  
  
## <a name="see-also"></a>Siehe auch  
[Erstellen die Variable Value Files &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
[Erstellen die Server-Verbindungsdateien &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
[Generieren von Berichten &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md)  
  
