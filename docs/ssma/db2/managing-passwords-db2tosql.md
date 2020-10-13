---
description: Verwalten von Kenn Wörtern (DB2ToSQL)
title: Verwalten von Kenn Wörtern (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 07/05/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 56d546e3-8747-4169-aace-693302667e94
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: f68af2ae2176ed4860f92a829544c7ff463254e9
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987416"
---
# <a name="managing-passwords-db2tosql"></a>Verwalten von Kenn Wörtern (DB2ToSQL)
In diesem Abschnitt geht es um das Sichern von Daten Bank Kennwörtern und das Verfahren zum Importieren oder Exportieren von Datenbankservern:  
  
1.  Sichern des Kennworts  
  
2.  Exportieren oder importieren verschlüsselter Kenn Wörter  
  
## <a name="securing-password"></a>Sichern des Kennworts  
SSMA ermöglicht Ihnen das Sichern Ihres Kennworts für eine Datenbank.  
  
Verwenden Sie das folgende Verfahren, um eine sichere Verbindung zu implementieren:  
  
Geben Sie ein gültiges Kennwort an, indem Sie eine der folgenden drei Methoden verwenden:  
  
1.  **Klartext löschen:** Geben Sie das Daten Bank Kennwort in das Attribut Wert des Knotens "Password" ein. Sie befindet sich unter dem Knoten Server Definition im Abschnitt Server der Skriptdatei oder der Server Verbindungs Datei.  
  
    Kenn Wörter im Klartext sind nicht sicher. Aus diesem Grund wird in der Konsolenausgabe folgende Warnmeldung angezeigt: *"Server &lt; Server-ID &gt; Kennwort wird in unsicherem Klartext bereitgestellt. die SSMA-Konsolenanwendung bietet eine Option zum Schützen des Kennworts durch Verschlüsselung. Weitere Informationen finden Sie unter der Option"-SecurePassword "in der SSMA-Hilfedatei.*  
  
    **Verschlüsselte Kenn Wörter:** Das angegebene Kennwort wird in diesem Fall in verschlüsselter Form auf dem lokalen Computer in ProtectedStorage. SSMA gespeichert.  
  
    -   **Sichern von Kenn Wörtern**  
  
        -   Führen `SSMAforDB2Console.exe` Sie das mit dem `-securepassword` und den Switch-Schalter in der Befehlszeile aus, und übergeben Sie die Server Verbindung oder die Skriptdatei mit dem Kenn Wort Knoten im Abschnitt Server Definition.  
  
        -   Bei der Eingabeaufforderung wird der Benutzer aufgefordert, das Daten Bank Kennwort einzugeben und zu bestätigen.  
  
            Die Server Definitions-IDs und die zugehörigen verschlüsselten Kenn Wörter werden in einer Datei auf dem lokalen Computer gespeichert.  
            
            Beispiel 1:
            
            ```console
            Specify password
            C:\SSMA\SSMAforDB2Console.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ VariableValueFileSample.xml"
            
            Enter password for server_id 'XXX_1': xxxxxxx
            
            Re-enter password for server_id 'XXX_1': xxxxxxx
            ```
            
            Beispiel 2:
            
            ```console
            C:\SSMA\SSMAforDB2Console.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ VariableValueFileSample.xml" -o
            
            Enter password for server_id 'source_1': xxxxxxx
            
            Re-enter password for server_id 'source_1': xxxxxxx
            
            Enter password for server_id 'target_1': xxxxxxx
            
            Re-enter password for server_id 'target _1': xxxxxxx  
            ```
    
    -   **Entfernen verschlüsselter Kenn Wörter**  
  
        Führen `SSMAforDB2Console.exe` Sie das mit `-securepassword` dem `-remove` aus, und wechseln Sie in der Befehlszeile zum übergeben der Server-IDs, um die verschlüsselten Kenn Wörter aus der geschützten Speicherdatei auf dem lokalen Computer zu entfernen.  
  
        Beispiel:  

        ```console
        C:\SSMA\SSMAforDB2Console.EXE -securepassword -remove all
        C:\SSMA\SSMAforDB2Console.EXE -securepassword -remove "source_1,target_1"
        ```

    -   **Auflisten von Server-IDs, deren Kenn Wörter verschlüsselt sind**  
  
        Führen `SSMAforDB2Console.exe` Sie mit dem `-securepassword` aus `-list` , und wechseln Sie in der Befehlszeile, um alle Server-IDs aufzulisten, deren Kenn Wörter verschlüsselt wurden.  
  
        Beispiel:  

        ```console
        C:\SSMA\SSMAforDB2Console.EXE -securepassword -list
        ```

    > [!NOTE]  
    > 1.  Das Kennwort im Klartext, das in der Skript-oder Server Verbindungs Datei angegeben ist, hat Vorrang vor dem verschlüsselten Kennwort in der gesicherten Datei.  
    > 2.  Wenn im Server Abschnitt der Server Verbindungs Datei oder der Skriptdatei kein Kennwort vorhanden ist oder wenn es nicht auf dem lokalen Computer gesichert wurde, werden Sie von der-Konsole aufgefordert, das Kennwort einzugeben.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Exportieren oder importieren verschlüsselter Kenn Wörter  
Mit der SSMA-Konsolenanwendung können Sie verschlüsselte Daten Bank Kennwörter, die in einer Datei auf dem lokalen Computer vorhanden sind, in eine gesicherte Datei exportieren und umgekehrt. Dies hilft bei der unabhängigen Erstellung der verschlüsselten Kenn Wörter.

Mit der _Export Funktion_ werden die Server-ID und das Kennwort aus dem lokalen geschützten Speicher gelesen. Das System speichert dann die ID und das Kennwort in einer verschlüsselten Datei. Der Benutzer wird aufgefordert, das Kennwort für die gesicherte Datei einzugeben. Stellen Sie sicher, dass das eingegebene Kennwort mindestens 8 Zeichen lang ist. Diese gesicherte Datei ist auf verschiedenen Computern portabel.

Die _Import Funktion_ liest die Server-ID und die Kenn Wort Informationen aus der gesicherten Datei. Der Benutzer wird aufgefordert, das Kennwort für die gesicherte Datei einzugeben, und fügt die Informationen an den lokalen geschützten Speicher an.  

### <a name="export-example"></a>Beispiel für den Export

1. Exportieren Sie das Kennwort.

2. Geben Sie das Kennwort zum Schutz der exportierten Datei ein.

3. Ausführen: &nbsp;`C:\SSMA\SSMAforDB2Console.EXE -securepassword -export all "machine1passwords.file"`

4. Geben Sie das Kennwort zum Schutz der exportierten Datei ein: xxxxxxxx

5. Kennwort bestätigen: xxxxxxxx

6. Ausführen: &nbsp;`C:\SSMA\SSMAforDB2Console.EXE -p -e "DB2DB_1_1,Sql_1" "machine2passwords.file"`

7. Geben Sie das Kennwort zum Schutz der exportierten Datei ein: xxxxxxxx

8. Kennwort bestätigen: xxxxxxxx  

### <a name="import-example"></a>Beispiel importieren

1. Importieren Sie ein verschlüsseltes Kennwort.

2. Geben Sie das Kennwort zum Schutz der importierten Datei ein.

3. Ausführen: &nbsp;`C:\SSMA\SSMAforDB2Console.EXE -securepassword -import all "machine1passwords.file"`

4. Geben Sie das Kennwort ein, um die Server aus der verschlüsselten Datei zu importieren: xxxxxxxx

5. Kennwort bestätigen: xxxxxxxx

6. Ausführen: &nbsp;`C:\SSMA\SSMAforDB2Console.EXE -p -i "DB2DB_1,Sql_1" "machine2passwords.file"`

7. Geben Sie das Kennwort ein, um die Server aus der verschlüsselten Datei zu importieren: xxxxxxxx

8. Kennwort bestätigen: xxxxxxxx

## <a name="see-also"></a>Weitere Informationen  
[Ausführen der SSMA-Konsole](./executing-the-ssma-console-db2tosql.md)  
