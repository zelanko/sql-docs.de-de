---
title: Command Line Options in SSMA Console (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 237354e9-25c4-4386-9d1f-ca0618d4a9a0
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8419990abe0870d248ad403fc4d802b1775fe3f1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678958"
---
# <a name="command-line-options-in-ssma-console-db2tosql"></a>Command Line Options in SSMA Console (DB2ToSQL)
Microsoft bietet Ihnen eine stabile Set-Optionen über die Befehlszeile auszuführen und zu steuern von SSMA-Aktivitäten. Die folgenden Abschnitte enthalten Informationen identisch.  
  
## <a name="command-line-options-in-ssma-console"></a>Befehlszeilenoptionen in der SSMA-Konsole  
Hierin beschriebenen sind die Konsole die Befehlsoptionen an.  
  
In diesem Abschnitt wird der Begriff "Option" auch als "Switch" bezeichnet.  
  
Optionen Groß-/Kleinschreibung nicht und kann entweder mit starten "**-**'oder'**/**" Zeichen.  
  
Wenn Optionen angegeben werden, ist es erforderlich, um die entsprechende Optionsparameter angeben.  
  
Optionsparameter müssen vom Option Zeichen durch ein Leerzeichen getrennt werden.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
`C:\> SSMAforDB2Console.EXE -s scriptfile`  
  
`C:\> SSMAforDB2Console.EXE -s “C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \AssessmentReportGenerationSample.xml” –v “C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \VariableValueFileSample.xml” –c “C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ServersConnectionFileSample.xml”`  
  
Ordner oder Datei-Namen mit Leerzeichen müssen in doppelte Anführungszeichen angegeben werden.  
  
Die Ausgabe der Befehlszeile Einträge und Fehlermeldungen werden in "stdout" oder in einer angegebenen Datei gespeichert.  
  
### <a name="script-file-option-sscript"></a>Skript-Datei-Option: – s bzw. das Skript mit  
Ein erforderlicher Parameter, gibt der Skript-Datei als Pfad/Name Skripts mit dem Befehlssequenzen SSMA ausgeführt werden soll.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
`C:\>SSMAforDB2Console.EXE –s “C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml”`  
  
### <a name="variable-value-file-option-vvariable"></a>Variable-Wert-Dateioption: – V/variable  
Diese Datei umfasst, Variablen, die in der Skriptdatei verwendet wird. Dies ist ein Optionaler Schalter. Wenn Variablen nicht in der Datei deklariert und in der Skriptdatei verwendet, wird die Anwendung generiert einen Fehler und beendet die Ausführung der Verwaltungskonsole.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
-   Variablen, die in mehreren Variablenwert-Dateien, z. B. eine mit einem Standardwert und eine mit einer bestimmten Instanz-Wert bei Bedarf definiert. Die letzte Variable-Datei, die in die Befehlszeilenargumente angegeben hat die Einstellung, im Fall eine Duplizierung von Variablen:  
  
    `C:\>SSMAforDB2Console.EXE -s`  
  
    `“C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml” –v c:\migration`  
  
    `projects\global_variablevaluefile.xml –v “c:\migrationprojects\instance_variablevaluefile.xml”`  
  
### <a name="server-connection-file-option-cserverconnection"></a>Server-Verbindung-Dateioption: – c/serverconnection  
Diese Datei enthält die Serververbindungsinformationen für jeden Server. Die Definition jedes Servers wird durch eine eindeutige Server-ID identifiziert. Die Server-IDs auf die verwiesen wird in der Skriptdatei für die Verbindung Befehle.  
  
Server-Definition des Server-Connection-Datei bzw. Skriptdatei angehören. Server-Id in der Skriptdatei hat Vorrang vor den Server-Verbindungsdatei, für den Fall, dass eine Duplizierung der Server-Id vorhanden ist.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
-   Server-IDs werden in der Skriptdatei verwendet und sie in einer separaten Server Connection-Datei definiert sind, Server-Verbindungsdatei verwendet Variablen, die in den Wert der Variablen-Datei definiert sind:  
  
    `C:\>SSMAforDB2Console.EXE –s “C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml”  –v`  
  
    `c:\SsmaProjects\myvaluefile1.xml –c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Server-Definition wird in der Skriptdatei eingebettet:  
  
    `C:\>SSMAforDB2Console.EXE –s “C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml”`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>XML-Ausgabe-Option: - X / Xmloutput [Xmloutputfile]  
Mit diesem Befehl wird für die Ausgabe der Ausgabenachrichten der Befehl in einem XML-Format, entweder auf Konsole oder in eine XML-Datei verwendet.  
  
Es gibt zwei Optionen zur Xmloutput, viz..,:  
  
-   Wenn der "FilePath", nach dem Wechsel Xmloutput angegeben wird wird die Ausgabe an die Datei umgeleitet.  
  
    **Syntaxbeispiel:**  
  
    `C:\>SSMAforDB2Console.EXE –s`  
  
    `“C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml”  –x d:\xmloutput\project1output.xml`  
  
-   Wenn keine "FilePath", nach dem Wechsel Xmloutput angegeben wird wird die Xmlout in der Konsole selbst angezeigt.  
  
    **Syntaxbeispiel:**  
  
    `C:\>SSMAforDB2Console.EXE –s “C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml”  –xmloutput`  
  
### <a name="log-file-option-llog"></a>Option für die Protokolldatei: – l/log  
Alle SSMA-Vorgänge in der Konsolenanwendung abrufen in einer Protokolldatei aufgezeichnet. Dies ist ein Optionaler Schalter. Wenn eine Protokolldatei und den Pfad in der Befehlszeile angegeben werden, wird das Protokoll in der angegebenen Position generiert. Andernfalls wird er an seinem Standardspeicherort generiert.  
  
**Syntaxbeispiel:**  
  
`C:\>SSMAforDB2Console.EXE`  
  
`“C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml”  –l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option-eprojectenvironment"></a>Projekt-Umgebung Ordneroption: – e/projectenvironment  
Dies bedeutet der Projektordner für die Einstellungen von Umgebung für das aktuelle SSMA-Projekt. Dieser Schalter ist optional.  
  
**Syntaxbeispiel:**  
  
`C:\>SSMAforDB2Console.EXE –s`  
  
`“C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml”  –e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option-psecurepassword"></a>Secure Password-Option: – p/securepassword  
Diese Option gibt an, das verschlüsselte Kennwort für Server-Verbindungen. Es unterscheidet sich von allen anderen Optionen: die Option weder führt alle Skripts noch Migrationsaktivitäten erleichtert jedoch kennwortverschlüsselung für das Server-Verbindungen im Migrationsprojekt verwendet bei der Verwaltung hilft.  
  
Sie können keiner anderen Option oder das Kennwort als den Befehlszeilenparameter eingeben. Andernfalls führt dies zu einem Fehler. Weitere Informationen finden Sie in der [Verwalten von Kennwörtern](http://msdn.microsoft.com/56d546e3-8747-4169-aace-693302667e94) Abschnitt.  
  
Die folgenden untergeordneten Optionen werden unterstützt, für die `–p/securepassword`:  
  
-   Zum Hinzufügen von Kennwort geschützten Speicher ab, für eine angegebene ID für den Server oder für alle Server-IDs, die in der Server-Connection-Datei definiert. Die - Option, die unten angegebenen Aktualisierungen des Kennworts überschreiben, sofern bereits vorhanden:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}` `-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   So entfernen Sie das verschlüsselte Kennwort aus dem geschützten Speicher, der die angegebene ID oder für alle Server-IDs:  
  
    `–p/securepassword –r/remove {<server_id> [, …n] | all}`  
  
-   Um eine Liste der Server-IDs anzuzeigen, für die das Kennwort verschlüsselt wird:  
  
    `–p/securepassword –l/list`  
  
-   So exportieren Sie die Kennwörter in geschütztem Speicher auf einer verschlüsselten Datei gespeichert. Diese Datei ist mit benutzerdefinierten-Passphrase verschlüsselt.  
  
    `–p/securepassword –e/export {<server-id> [, …n] | all} <encrypted-password -file>`  
  
-   Die verschlüsselte Datei, die zuvor exportierte wird in den lokalen geschützten Speicher, die mit der Passphrase benutzerdefinierten importiert. Nachdem die Datei entschlüsselt wurde, werden sie in einer neuen Datei, gespeichert, der wiederum auf dem lokalen Computer verschlüsselt wird.  
  
    `–p/securepassword –i/import {<server-id> [, …n] | all} <encrypted-password -file>`  
  
    Mehrere Server-IDs können mithilfe von Kommas – als Trennzeichen angegeben werden.  
  
### <a name="help-option-help"></a>Hilfeoption::? / Help  
Zeigt eine syntaxzusammenfassung der Optionen der SSMA-Konsole:  
  
`C:\>SSMAforDB2Console.EXE -?`  
  
Eine tabellarische Anzeige der SSMA-Konsole über die Befehlszeilenoptionen, finden Sie unter [Anhang – 1 &#40;DB2ToSQL&#41;](../../ssma/db2/appendix-1-db2tosql.md).  
  
### <a name="securepassword-help-option-securepassword--help"></a>SecurePassword Hilfeoption: – Securepassword-? / Help  
Zeigt eine syntaxzusammenfassung der Optionen der SSMA-Konsole:  
  
`C:\>SSMAforDB2Console.EXE -securepassword -?`  
  
Eine tabellarische Anzeige der SSMA-Konsole über die Befehlszeilenoptionen, finden Sie unter [Anhang – 1 &#40;DB2ToSQL&#41;](../../ssma/db2/appendix-1-db2tosql.md)  
  
### <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt hängt davon ab, auf die Anforderungen Ihres Projekts:  
  
1.  Für die Angabe eines Kennworts oder das Exportieren / Importieren von Kennwörtern, finden Sie unter [Verwalten von Kennwörtern &#40;DB2ToSQL&#41;](../../ssma/db2/managing-passwords-db2tosql.md).  
  
2.  Generieren von Berichten finden Sie unter [Generieren von Berichten &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md).  
  
3.  Behandlung von Problemen in der Konsole, finden Sie unter [Problembehandlung &#40;DB2ToSQL&#41;](../../ssma/db2/troubleshooting-db2tosql.md).  
  
