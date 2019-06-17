---
title: Command Line Options in SSMA Console (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c1f3b3f0-0f3e-4e07-b745-2fbdde85c67e
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: fc8065bcfda3066fae31be982e25f054c07bca3a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62650764"
---
# <a name="command-line-options-in-the-ssma-console-accesstosql"></a>Befehlszeilenoptionen in der SSMA-Konsole (AccessToSQL)
Microsoft bietet Ihnen einen stabilen Satz von Befehlszeilenoptionen zum Ausführen und Steuern von SSMA-Aktivitäten. Die folgenden Abschnitte enthalten zusätzliche Details.  
  
## <a name="command-line-options-in-the-ssma-console"></a>Befehlszeilenoptionen in der SSMA-Konsole  
Hierin beschriebenen sind die Konsole die Befehlsoptionen an.  
  
In diesem Abschnitt wird der Begriff "Option" auch als "Switch" bezeichnet.  
  
Optionen sind nicht in der Groß-/Kleinschreibung beachtet und integritätsdienststatus mit der " **-** 'oder' **/** " Zeichen.  
  
Wenn Optionen angegeben werden, ist es zwingend erforderlich, dass Sie die entsprechende Optionsparameter angeben.  
  
Optionsparameter müssen vom Option Zeichen durch ein Leerzeichen getrennt werden.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
`C:\> SSMAforAccessConsole.EXE -s scriptfile`  
  
`C:\> SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\VariableValueFileSample.xml" -c "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml"`  
  
Ordner oder Datei-Namen mit Leerzeichen müssen in doppelte Anführungszeichen angegeben werden.  
  
Die Ausgabe des Befehlszeilen-Einträge und Fehlermeldungen ist in "stdout" oder in einer angegebenen Datei gespeichert.  
  
### <a name="script-file-option--sscript"></a>Skripterstellung für File-Option:-s bzw. das Skript  
Ein erforderlicher Parameter, gibt der Skript-Datei als Pfad/Name Skripts mit dem Befehlssequenzen SSMA ausgeführt werden soll.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
`C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="variable-value-file-option--vvariable"></a>Variablenwert-File-Option:-v/Variable  
Die Wert der Variablen-Datei umfasst, Variablen, die in der Skriptdatei verwendet wird. Der Schalter ist optional. Wenn Variablen nicht in der Datei deklariert und in der Skriptdatei verwendet, wird die Anwendung generiert einen Fehler und beendet die Ausführung der Verwaltungskonsole.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
-   Variablen, die definiert, die in mehreren Variablenwert-Dateien, z. B. eine mit einem Standardwert und eine mit einem instanzspezifischen-Wert, falls zutreffend. Die letzte Variable-Datei, die in die Befehlszeilenargumente angegeben hat die Einstellung, im Fall eine Duplizierung von Variablen:  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml" -v c:\migration`  
  
    `projects\global_variablevaluefile.xml -v "c:\migrationprojects\instance_variablevaluefile.xml"`  
  
### <a name="server-connection-file-option--cserverconnection"></a>Server-Verbindung-Dateioption: - C/Serverconnection  
Diese Datei enthält die Serververbindungsinformationen für jeden Server. Die Definition jedes Servers wird durch eine eindeutige Server-ID identifiziert. Die Server-IDs werden in der Skriptdatei für die Verbindung-bezogenen Befehlen auf die verwiesen wird.  
  
Server-Definition des Server-Connection-Datei bzw. Skriptdatei angehören. Server-Id in der Skriptdatei hat Vorrang vor den Server-Verbindungsdatei, für den Fall, dass eine Duplizierung der Server-Id vorhanden ist.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
-   Server-IDs werden in der Skriptdatei verwendet. Sie werden in einer separaten Server Connection-Datei definiert. Diese Datei verwendet Variablen, die in den Wert der Variablen-Datei definiert sind:  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -v`  
  
    `c:\SsmaProjects\myvaluefile1.xml -c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Server-Definition wird in der Skriptdatei eingebettet:  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>XML-Ausgabe-Option: - X / Xmloutput [Xmloutputfile]  
Mit diesem Befehl wird für die Ausgabe der Ausgabenachrichten der Befehl in einem XML-Format, entweder auf Konsole oder in eine XML-Datei verwendet.  
  
Es stehen zwei Optionen für Xmloutput, nämlich:  
  
-   Wenn nach dem Wechsel Xmloutput der "FilePath" angegeben wird, wird die Ausgabe an die Datei umgeleitet.  
  
    **Syntaxbeispiel:**  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -x d:\xmloutput\project1output.xml`  
  
-   Wenn nach dem Wechsel Xmloutput keine "FilePath" angegeben wird, wird die Xmlout in der Konsole selbst angezeigt.  
  
    **Syntaxbeispiel:**  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -xmloutput`  
  
### <a name="log-file-option--llog"></a>Melden Sie sich File-Option:-l/Log  
Alle SSMA-Vorgänge in der Konsolenanwendung in einer Protokolldatei aufgezeichnet werden, und der Schalter ist optional. Wenn eine Protokolldatei und den Pfad in der Befehlszeile angegeben werden, wird das Protokoll in der angegebenen Position generiert. Andernfalls wird er an seinem Standardspeicherort generiert.  
  
**Syntaxbeispiel:**  
  
`C:\>SSMAforAccessConsole.EXE`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option--eprojectenvironment"></a>Projekt Umgebung Ordneroption:-e/Projectenvironment  
Dieser optionale Schalter gibt an, der Projektordner für die Einstellungen von Umgebung für das aktuelle SSMA-Projekt.  
  
**Syntaxbeispiel:**  
  
`C:\>SSMAforAccessConsole.EXE -s`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -e c:\SsmaProjects\CommonEnvironment`  
  
||  
|-|  
||  
  
### <a name="secure-password-option--psecurepassword"></a>Secure Password-Option:-p/Securepassword  
Diese Option gibt an, das verschlüsselte Kennwort für Server-Verbindungen. Es unterscheidet sich von allen anderen Optionen ausführen ein Skripts oder nicht bei jeder Migrationsaktivitäten helfen, jedoch bei der Verwaltung hilft kennwortverschlüsselung für das Server-Verbindungen im Migrationsprojekt verwendet.  
  
Sie können keiner anderen Option oder das Kennwort als den Befehlszeilenparameter eingeben. Andernfalls führt dies zu einem Fehler. Weitere Informationen finden Sie unter den [Verwalten von Kennwörtern](managing-passwords-accesstosql.md) Abschnitt.  
  
Unterstützt die folgenden Unteroptionen `-p/securepassword`:  
  
-   So fügen ein Kennwort, oder aktualisieren ein vorhandenes Kennwort ein, auf geschützten Speicher für eine angegebene ID für den Server oder für alle Server-IDs, die in der Server-Connection-Datei definiert:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   So entfernen Sie das verschlüsselte Kennwort aus dem geschützten Speicher, der die angegebene ID oder für alle Server-IDs:  
  
    `-p/securepassword -r/remove {<server_id> [, ...n] | all}`  
  
-   Um eine Liste der Server-IDs anzuzeigen, für die das Kennwort verschlüsselt wird:  
  
    `-p/securepassword -l/list`  
  
-   So exportieren Sie die Kennwörter in geschütztem Speicher auf einer verschlüsselten Datei gespeichert. Diese Datei ist mit benutzerdefinierten-Passphrase verschlüsselt.  
  
    `-p/securepassword -e/export {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
-   Die verschlüsselte Datei, die zuvor exportierte wird in den lokalen geschützten Speicher, die mit der Passphrase benutzerdefinierten importiert. Nachdem die Datei entschlüsselt wurde, werden sie in einer neuen Datei, gespeichert, der wiederum auf dem lokalen Computer verschlüsselt wird.  
  
    `-p/securepassword -i/import {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
    Mehrere Server-IDs können mithilfe von Kommas – als Trennzeichen angegeben werden.  
  
### <a name="help-option--help"></a>Hilfe-Option::? / Help  
Zeigt eine syntaxzusammenfassung der Optionen der SSMA-Konsole:  
  
`C:\>SSMAforAccessConsole.EXE -?`  
  
Eine tabellarische Anzeige der SSMA-Konsole Befehlszeilenoptionen, finden Sie unter [Anhang – 1 &#40;AccessToSQL&#41;](../../ssma/access/appendix-1-accesstosql.md).  
  
### <a name="securepassword-help-option--securepassword--help"></a>SecurePassword Hilfeoption: - Securepassword-? / Help  
Zeigt eine syntaxzusammenfassung der Optionen der SSMA-Konsole:  
  
`C:\>SSMAforAccessConsole.EXE -securepassword -?`  
  
Eine tabellarische Anzeige der SSMA-Konsole Befehlszeilenoptionen, finden Sie unter [Anhang – 1 &#40;AccessToSQL&#41;](../../ssma/access/appendix-1-accesstosql.md)  
  
### <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt hängt davon ab, auf die Anforderungen Ihres Projekts:  
  
1.  Für die Angabe eines Kennworts oder das Exportieren / Importieren von Kennwörtern, finden Sie unter [Verwalten von Kennwörtern &#40;AccessToSQL&#41;](../../ssma/access/managing-passwords-accesstosql.md).  
  
2.  Generieren von Berichten finden Sie unter [Generieren von Berichten &#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
3.  Behandlung von Problemen in der Konsole, finden Sie unter [Problembehandlung &#40;AccessToSQL&#41;](../../ssma/access/troubleshooting-accesstosql.md).  
  
