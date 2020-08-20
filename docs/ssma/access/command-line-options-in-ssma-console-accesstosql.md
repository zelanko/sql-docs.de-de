---
description: Befehlszeilenoptionen in der SSMA-Konsole (accesstosql)
title: Befehlszeilenoptionen in der SSMA-Konsole (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c1f3b3f0-0f3e-4e07-b745-2fbdde85c67e
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 7e0baa3982fd6b123a4cce29aaada1d78478fd46
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497804"
---
# <a name="command-line-options-in-the-ssma-console-accesstosql"></a>Befehlszeilenoptionen in der SSMA-Konsole (accesstosql)
Microsoft bietet Ihnen einen robusten Satz von Befehlszeilenoptionen zum Ausführen und Steuern von SSMA-Aktivitäten. In den folgenden Abschnitten finden Sie weitere Details.  
  
## <a name="command-line-options-in-the-ssma-console"></a>Befehlszeilenoptionen in der SSMA-Konsole  
Hier werden die Konsolen Befehlsoptionen beschrieben.  
  
Für den Zweck dieses Abschnitts wird der Begriff "Option" auch als "Switch" bezeichnet.  
  
Bei den Optionen wird die Groß-/Kleinschreibung nicht beachtet, und Sie kann entweder mit dem **-** Zeichen ' ' oder ' ' beginnen **/** .  
  
Wenn Optionen angegeben werden, ist es obligatorisch, die entsprechenden Optionsparameter anzugeben.  
  
Optionsparameter müssen von dem Options Zeichen durch Leerzeichen getrennt werden.  
  
**Syntax Beispiele:**  
  
`C:\> SSMAforAccessConsole.EXE -s scriptfile`  
  
`C:\> SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\VariableValueFileSample.xml" -c "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml"`  
  
Ordner-oder Dateinamen, die Leerzeichen enthalten, müssen in doppelten Anführungszeichen angegeben werden.  
  
Die Ausgabe der Befehlszeilen Einträge und der Fehlermeldungen wird in stdout oder in einer angegebenen Datei gespeichert.  
  
### <a name="script-file-option--sscript"></a>Skriptdatei Option:-s/Skript  
Ein obligatorischer Switch: der Pfad/Name der Skriptdatei gibt das Skript der Befehlssequenzen an, die von SSMA ausgeführt werden.  
  
**Syntax Beispiele:**  
  
`C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="variable-value-file-option--vvariable"></a>Variable value file-Option:-v/Variable  
Die Variablen Wert Datei umfasst Variablen, die in der Skriptdatei verwendet werden. Der Schalter ist optional. Wenn Variablen nicht in der Variablen Datei deklariert und in der Skriptdatei verwendet werden, generiert die Anwendung einen Fehler und beendet die Konsolen Ausführung.  
  
**Syntax Beispiele:**  
  
-   In mehreren Variablen Wert Dateien definierte Variablen, eventuell eine mit einem Standardwert und eine andere mit einem instanzspezifischen Wert, falls zutreffend. Die letzte in den Befehlszeilen Argumenten angegebene Variablen Datei hat die bevorzugte Einstellung, wenn eine Duplizierung der Variablen vorliegt:  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml" -v c:\migration`  
  
    `projects\global_variablevaluefile.xml -v "c:\migrationprojects\instance_variablevaluefile.xml"`  
  
### <a name="server-connection-file-option--cserverconnection"></a>Server Verbindungs Datei (Option):-c/Server Connection  
Diese Datei enthält Server Verbindungsinformationen für jeden Server. Jede Server Definition wird durch eine eindeutige Server-ID identifiziert. Auf die Server-IDs wird in der Skriptdatei für verbindungsbezogene Befehle verwiesen.  
  
Die Server Definition kann ein Teil der Server Verbindungs Datei und/oder der Skriptdatei sein. Die Server-ID in der Skriptdatei hat Vorrang vor der Server Verbindungs Datei, wenn eine Duplizierung der Server-ID vorliegt.  
  
**Syntax Beispiele:**  
  
-   Server-IDs werden in der Skriptdatei verwendet. Sie werden in einer separaten Server Verbindungs Datei definiert. Diese Datei verwendet Variablen, die in der Variablen Wert Datei definiert sind:  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -v`  
  
    `c:\SsmaProjects\myvaluefile1.xml -c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Die Server Definition ist in die Skriptdatei eingebettet:  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>XML-Ausgabe Option:-x/xmloutput [xmloutputfile]  
Dieser Befehl wird verwendet, um die Befehlsausgabe Nachrichten in einem XML-Format entweder an die Konsole oder an eine XML-Datei auszugeben.  
  
Für xmloutput stehen zwei Optionen zur Verfügung:  
  
-   Wenn der filePath nach dem xmloutput-Schalter bereitgestellt wird, wird die Ausgabe an die Datei umgeleitet.  
  
    **Syntaxbeispiel:**  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -x d:\xmloutput\project1output.xml`  
  
-   Wenn nach dem xmloutput-Schalter kein filePath bereitgestellt wird, wird das xmlout in der Konsole angezeigt.  
  
    **Syntaxbeispiel:**  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -xmloutput`  
  
### <a name="log-file-option--llog"></a>Protokolldatei Option:-l/Log  
Alle SSMA-Vorgänge in der Konsolenanwendung werden in einer Protokolldatei aufgezeichnet, und der Schalter ist optional. Wenn eine Protokolldatei und ihr Pfad in der Befehlszeile angegeben werden, wird das Protokoll am angegebenen Speicherort generiert. Andernfalls wird Sie an Ihrem Standard Speicherort generiert.  
  
**Syntaxbeispiel:**  
  
`C:\>SSMAforAccessConsole.EXE`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option--eprojectenvironment"></a>Projekt Umgebungs Ordner Option:-e/projectenvironment  
Dieser optionale Schalter gibt den Ordner für die Projekt Umgebungseinstellungen für das aktuelle SSMA-Projekt an.  
  
**Syntaxbeispiel:**  
  
`C:\>SSMAforAccessConsole.EXE -s`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option--psecurepassword"></a>Sichere Kenn Wort Option:-p/SecurePassword  
Diese Option gibt das verschlüsselte Kennwort für Serververbindungen an. Dies unterscheidet sich von allen anderen Optionen dahin, dass kein Skript oder Hilfe in migrationsbezogenen Aktivitäten ausgeführt wird, sondern die Kenn Wort Verschlüsselung für die Serververbindungen, die im Migrationsprojekt verwendet werden, unterstützt wird.  
  
Sie können keine andere Option oder kein anderes Kennwort für den Befehlszeilenparameter eingeben. Andernfalls führt dies zu einem Fehler. Weitere Informationen finden Sie im Abschnitt [Verwalten](managing-passwords-accesstosql.md) von Kenn Wörtern.  
  
Die folgenden unter Optionen werden für unterstützt `-p/securepassword` :  
  
-   Zum Hinzufügen eines Kennworts oder zum Aktualisieren eines vorhandenen Kennworts auf geschützten Speicher für eine angegebene Server-ID oder für alle Server-IDs, die in der Server Verbindungs Datei definiert sind:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
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
  
`C:\>SSMAforAccessConsole.EXE -?`  
  
Eine tabellarische Anzeige der Befehlszeilenoptionen der SSMA-Konsole finden Sie in [Anhang-1 &#40;accesstosql&#41;](../../ssma/access/appendix-1-accesstosql.md).  
  
### <a name="securepassword-help-option--securepassword--help"></a>SecurePassword-Hilfe Option:-SecurePassword-?/Help  
Zeigt die Syntax Zusammenfassung der Optionen der SSMA-Konsole an:  
  
`C:\>SSMAforAccessConsole.EXE -securepassword -?`  
  
Eine tabellarische Anzeige der Befehlszeilenoptionen der SSMA-Konsole finden Sie in [Anhang-1 &#40;accesstosql&#41;](../../ssma/access/appendix-1-accesstosql.md)  
  
### <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt hängt von Ihren Projektanforderungen ab:  
  
1.  Informationen zum Angeben eines Kennworts oder zum Exportieren/Importieren von Kenn Wörtern finden Sie unter Verwalten von Kenn [Wörtern &#40;accesstosql&#41;](../../ssma/access/managing-passwords-accesstosql.md).  
  
2.  Informationen zum Erstellen von Berichten finden Sie unter [Erstellen von Berichten &#40;Access Token&#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
3.  Informationen zur Behebung von Problemen in der-Konsole finden Sie unter [Problembehandlung &#40;Access Token&#41;](../../ssma/access/troubleshooting-accesstosql.md).  
  
