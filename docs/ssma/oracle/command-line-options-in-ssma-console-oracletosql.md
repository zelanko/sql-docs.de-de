---
description: Befehlszeilenoptionen in der SSMA-Konsole (OracleToSQL)
title: Befehlszeilenoptionen in der SSMA-Konsole (oracledesql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Command Line Options, Help Option
- Command Line Options, SecurePassword Help Option
- Command Line Options, Variable Value File Option
- Command Line Options,Script File Option
ms.assetid: bf4a9313-349e-4ebf-9c89-9f5bb515f9ff
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 1a950ff2e2870519ae7063bfc0df615fd971187b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468839"
---
# <a name="command-line-options-in-ssma-console-oracletosql"></a>Befehlszeilenoptionen in der SSMA-Konsole (OracleToSQL)
Microsoft stellt Ihnen eine robuste Befehlszeilenoption zur Verfügung, mit der Sie SSMA-Aktivitäten ausführen und steuern können. Die nachfolgenden Abschnitte beschreiben die gleichen.  
  
## <a name="command-line-options-in-ssma-console"></a>Befehlszeilenoptionen in der SSMA-Konsole  
Hier werden die Konsolen Befehlsoptionen beschrieben.  
  
Für den Zweck dieses Abschnitts wird der Begriff "Option" auch als "Switch" bezeichnet.  
  
-   Bei den Optionen wird die Groß-/Kleinschreibung nicht beachtet, und es kann entweder mit dem **-** Zeichen ' ' oder ' **/** ' beginnen.  
  
-   Wenn Optionen angegeben werden, ist es obligatorisch, die entsprechenden Optionsparameter anzugeben.  
  
-   Optionsparameter müssen von dem Options Zeichen durch Leerzeichen getrennt werden.  
  
    **Syntax Beispiele:**  
  
    `C:\> SSMAforOracleConsole.EXE -s scriptfile`  
  
    `C:\> SSMAforOracleConsole.EXE -s "C Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \AssessmentReportGenerationSample.xml" -v "C Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \VariableValueFileSample.xml" -c "C Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \ServersConnectionFileSample.xml"`  
  
-   Ordner-oder Dateinamen, die Leerzeichen enthalten, müssen in doppelten Anführungszeichen angegeben werden.  
  
-   Die Ausgabe der Befehlszeilen Einträge und-Fehlermeldungen wird in stdout oder in einer angegebenen Datei gespeichert.  
  
### <a name="script-file-option--sscript"></a>Skriptdatei Option:-s/Skript  
Ein obligatorischer Switch: der Pfad/Name der Skriptdatei gibt das Skript der Befehlssequenzen an, die von SSMA ausgeführt werden.  
  
**Syntax Beispiele:**  
  
`C:\>SSMAforOracleConsole.EXE -s "C Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \ConversionAndDataMigrationSample.xml"`  
  
### <a name="variable-value-file-option--vvariable"></a>Variable value file-Option:-v/Variable  
Diese Datei umfasst Variablen, die in der Skriptdatei verwendet werden. Dies ist ein optionaler Switch. Wenn Variablen nicht in der Variablen Datei deklariert und in der Skriptdatei verwendet werden, generiert die Anwendung einen Fehler und beendet die Konsolen Ausführung.  
  
**Syntax Beispiele:**  
  
-   In mehreren Variablen Wert Dateien definierte Variablen, eventuell eine mit einem Standardwert und eine andere mit einem instanzspezifischen Wert, falls zutreffend. Die letzte in den Befehlszeilen Argumenten angegebene Variablen Datei hat die bevorzugte Einstellung, wenn eine Duplizierung der Variablen vorliegt:  
  
    `C:\>SSMAforOracleConsole.EXE -s`  
  
    `"C:\ Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \ConversionAndDataMigrationSample.xml" -v c:\migration`  
  
    `projects\global_variablevaluefile.xml -v "c:\migrationprojects\instance_variablevaluefile.xml"`  
  
### <a name="server-connection-file-option--cserverconnection"></a>Server Verbindungs Datei (Option):-c/Server Connection  
Diese Datei enthält Server Verbindungsinformationen für jeden Server. Jede Server Definition wird durch eine eindeutige Server-ID identifiziert. Auf die Server-IDs wird in der Skriptdatei für verbindungsbezogene Befehle verwiesen.  
  
Die Server Definition kann ein Teil der Server Verbindungs Datei und/oder der Skriptdatei sein. Die Server-ID in der Skriptdatei hat Vorrang vor der Server Verbindungs Datei, wenn eine Duplizierung der Server-ID vorliegt.  
  
**Syntax Beispiele:**  
  
-   Server-IDs werden in der Skriptdatei verwendet und in einer separaten Server Verbindungs Datei definiert. die Server Verbindungs Datei verwendet Variablen, die in der Variablen Wert Datei definiert sind:  
  
    `C:\>SSMAforOracleConsole.EXE -s "C:\ Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -v`  
  
    `c:\SsmaProjects\myvaluefile1.xml -c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Die Server Definition ist in die Skriptdatei eingebettet:  
  
    `C:\>SSMAforOracleConsole.EXE -s "C:\ Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \ConversionAndDataMigrationSample.xml"`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>XML-Ausgabe Option:-x/xmloutput [xmloutputfile]  
Dieser Befehl wird verwendet, um die Befehlsausgabe Nachrichten in einem XML-Format entweder an die Konsole oder an eine XML-Datei auszugeben.  
  
Für xmloutput stehen zwei Optionen zur Verfügung:  
  
-   Wenn der filePath nach dem xmloutput-Switch bereitgestellt wird, wird die Ausgabe an die Datei umgeleitet.  
  
    **Syntax Beispiel:**  
  
    `C:\>SSMAforOracleConsole.EXE -s`  
  
    `"C:\ Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -x d:\xmloutput\project1output.xml`  
  
-   Wenn nach dem xmloutput-Schalter kein filePath bereitgestellt wird, wird das xmlout in der Konsole angezeigt.  
  
    **Syntax Beispiel:**  
  
    `C:\>SSMAforOracleConsole.EXE -s "C:\ Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -xmloutput`  
  
### <a name="log-file-option--llog"></a>Protokolldatei Option:-l/Log  
Alle SSMA-Vorgänge in der Konsolenanwendung werden in einer Protokolldatei aufgezeichnet. Dies ist ein optionaler Switch. Wenn eine Protokolldatei und ihr Pfad in der Befehlszeile angegeben werden, wird das Protokoll am angegebenen Speicherort generiert. Andernfalls wird Sie an Ihrem Standard Speicherort generiert.  
  
**Syntax Beispiel:**  
  
`C:\>SSMAforOracleConsole.EXE`  
  
`"C:\ Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option--eprojectenvironment"></a>Projekt Umgebungs Ordner Option:-e/projectenvironment  
Dies kennzeichnet den Ordner mit den Projekt Umgebungseinstellungen für das aktuelle SSMA-Projekt. Dieser Schalter ist optional.  
  
**Syntax Beispiel:**  
  
`C:\>SSMAforOracleConsole.EXE -s`  
  
`"C:\ Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option--psecurepassword"></a>Sichere Kenn Wort Option:-p/SecurePassword  
Diese Option gibt das verschlüsselte Kennwort für Serververbindungen an. Dies unterscheidet sich von allen anderen Optionen: die Option führt keines der Skripts aus und unterstützt keine migrationsbezogenen Aktivitäten, sondern hilft bei der Verwaltung der Kenn Wort Verschlüsselung für die Serververbindungen, die im Migrationsprojekt verwendet werden.  
  
Sie können keine andere Option oder kein anderes Kennwort als Befehlszeilenparameter eingeben. Andernfalls führt dies zu einem Fehler. Weitere Informationen finden Sie im Abschnitt Verwalten von Kenn [Wörtern](managing-passwords-oracletosql.md) .  
  
Die folgenden unter Optionen werden für unterstützt `-p/securepassword` :  
  
-   Zum Hinzufügen eines Kennworts zum geschützten Speicher für eine angegebene Server-ID oder für alle Server-IDs, die in der Server Verbindungs Datei definiert sind. Mit der Option-überschreiben (unten) wird das Kennwort aktualisiert, wenn es bereits vorhanden ist:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}` `-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   So entfernen Sie das verschlüsselte Kennwort aus dem geschützten Speicher der angegebenen Server-ID oder für alle Server-IDs:  
  
    `-p/securepassword -r/remove {<server_id> [, ...n] | all}`  
  
-   So zeigen Sie eine Liste der Server-IDs an, für die das Kennwort verschlüsselt ist:  
  
    `-p/securepassword -l/list`  
  
-   , Um die im geschützten Speicher gespeicherten Kenn Wörter in eine verschlüsselte Datei zu exportieren. Diese Datei wird mit dem vom Benutzer angegebenen Passphrase verschlüsselt.  
  
    `-p/securepassword -e/export {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
-   Die verschlüsselte Datei, die zuvor exportiert wurde, wird mit dem vom Benutzer angegebenen Pass-Phrase in den lokalen geschützten Speicher importiert. Nachdem die Datei entschlüsselt wurde, wird Sie in einer neuen Datei gespeichert, die wiederum auf dem lokalen Computer verschlüsselt ist.  
  
    `-p/securepassword -i/import {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
    Mehrere Server-IDs können mithilfe von Komma Trennzeichen angegeben werden.  
  
### <a name="help-option--help"></a>Hilfe Option:-?/Help  
Zeigt die Syntax Zusammenfassung der Optionen der SSMA-Konsole an:  
  
`C:\>SSMAforOracleConsole.EXE -?`  
  
Eine tabellarische Anzeige der Befehlszeilenoptionen der SSMA-Konsole finden Sie in [Anhang-1 &#40;oracleto SQL&#41;](../../ssma/oracle/appendix-1-oracletosql.md).  
  
### <a name="securepassword-help-option--securepassword--help"></a>SecurePassword-Hilfe Option:-SecurePassword-?/Help  
Zeigt die Syntax Zusammenfassung der Optionen der SSMA-Konsole an:  
  
`C:\>SSMAforOracleConsole.EXE -securepassword -?`  
  
Eine tabellarische Anzeige der Befehlszeilenoptionen der SSMA-Konsole finden Sie in [Anhang-1 &#40;oracleto SQL&#41;](../../ssma/oracle/appendix-1-oracletosql.md)  
  
### <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Angeben eines Kennworts oder zum Exportieren/Importieren von Kenn Wörtern finden Sie unter Verwalten von Kenn [Wörtern &#40;oracleto SQL&#41;](../../ssma/oracle/managing-passwords-oracletosql.md).  
  
-   Informationen zum Erstellen von Berichten finden Sie unter [Erstellen von Berichten &#40;oracleto SQL&#41;](../../ssma/oracle/generating-reports-oracletosql.md).  
  
-   Informationen zur Behebung von Problemen in der-Konsole finden Sie unter [Problembehandlung &#40;oracleto SQL&#41;](../../ssma/oracle/troubleshooting-oracletosql.md).  
  
