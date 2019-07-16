---
title: Verwalten von Kennwörtern (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Password management, importing or exporting encrypted password
- Password management, securing password
ms.assetid: 4ffbc587-ea3f-49ad-bc42-a654f672325e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: eda3f15f0d9ca1cfe04c25bfee5f2ece827e8b83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67909005"
---
# <a name="managing-passwords-mysqltosql"></a>Verwalten von Kennwörtern (MySqlToSql)
In diesem Abschnitt wird zum Schützen von Kennwörter für die Datenbanken und das Verfahren zum Importieren oder exportieren diese auf Servern:  
  
1.  Sichern das Kennwort  
  
2.  Exportieren oder importieren das verschlüsselte Kennwort  
  
## <a name="securing-password"></a>Sichern das Kennwort  
SSMA ermöglicht Ihnen, ein Kennwort, eine Datenbank zu sichern.  
  
Verwenden Sie wie folgt vor, um eine sichere Verbindung zu implementieren:  
  
Geben Sie ein gültiges Kennwort ein, die mit einer der drei folgenden Methoden:  
  
1.  **Löschen Sie Text ein:** Geben Sie das Datenbankkennwort, in der Value-Attribut des Knotens 'Password'. Es befindet sich unter dem Serverknoten für die Definition im Abschnitt "Server" des Server-Verbindungsdatei oder Skriptdatei.  
  
    Kennwörter in Klartext sind nicht sicher. Aus diesem Grund wird die folgende Warnmeldung in der Konsolenausgabe auftreten: *"Server &lt;Server-Id&gt; dient das Kennwort in Klartext nicht sicheren Form-Anwendung SSMA-Konsole bietet eine Option zum Schützen Sie das Kennwort, Verschlüsselung, finden Sie unter Securepassword - Option in SSMA-Hilfedatei für Weitere die Informationen."*  
  
    **Verschlüsselte Kennwörter:** Das angegebene Kennwort ist in diesem Fall in verschlüsselter Form auf dem lokalen Computer im ProtectedStorage.ssma gespeichert.  
  
    -   **Schützen von Kennwörtern**  
  
        -   Führen Sie die `SSMAforMySQLConsole.exe` mit der `-securepassword` und Schalter in die Befehlszeile übergeben den Server-Verbindung oder ein Skript-Datei, die mit dem kennwortknoten im Abschnitt Definition Server hinzufügen.  
  
        -   An der Eingabeaufforderung wird der Benutzer aufgefordert, um das Datenbankkennwort, und bestätigen Sie es.  
  
            Die Server-Definitions-Ids und die entsprechenden verschlüsselte Kennwörter werden in einer Datei auf dem lokalen Computer gespeichert.  
            
            Beispiel 1:
            
                Specify password
                
                C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            Beispiel 2:
            
                C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx
            
    -   **Verschlüsselte Kennwörter entfernen**  
  
        Führen Sie die `SSMAforMySQLConsole.exe` mit der`-securepassword` und `-remove` -Schalter an der Befehlszeile übergeben den Server-Ids, um die verschlüsselten Kennwörter aus der geschützten Speicherdatei vorhanden auf dem lokalen Computer zu entfernen.  
  
        Beispiel:  

            C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -remove all
            C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -remove "source_1,target_1"  
  
    -   **Auflisten von Server-Ids, deren Kennwörter verschlüsselt sind**  
  
        Führen Sie die `SSMAforMySQLConsole.exe` mit der `-securepassword` und `-list` -Schalter an der Befehlszeile aus, um alle Server-Ids auflisten, deren Kennwörter verschlüsselt wurden.  
  
        Beispiel:  
        
            C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -list  
  
    > [!NOTE]  
    > 1.  Das Kennwort als Klartext im Skript oder eine Server-Verbindungsdatei erwähnt haben Vorrang vor das verschlüsselte Kennwort in der gesicherten Datei.  
    > 2.  Wenn kein Kennwort im Abschnitt "Server" die Server-Verbindungsdatei oder die Datei vorhanden ist, oder wenn sie nicht auf dem lokalen Computer gesichert wurden, werden Sie von die Konsole aufgefordert, das Kennwort eingeben.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Exportieren oder importieren verschlüsselte Kennwörter  
Die SSMA-Console-Anwendung können Sie verschlüsselte Datenbankkennwörter in einer Datei auf dem lokalen Computer vorhanden, eine geschützte Datei und umgekehrt zu exportieren. Er hilft bei der Erstellung des Computers verschlüsselte Kennwörter unabhängig. Funktionen zum Exportieren der liest, der Id und Kennwort aus der lokalen geschützten Speicher ab und speichert die Informationen in einer verschlüsselten Datei. Der Benutzer wird aufgefordert, das Kennwort für die sichere Datei eingeben. Stellen Sie sicher, dass das eingegebene Kennwort mindestens 8 Zeichenlänge beträgt. Diese sichere Datei ist auf unterschiedlichen Computern übertragbar. Importfunktionalität, liest der Server-Id und Kennwort aus der gesicherten Datei. Der Benutzer wird aufgefordert, das Kennwort für die sichere Datei einzugeben und fügt die Informationen im lokalen geschützten Speicher hinzu.  
  
Beispiel:  

    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforMySQLConsole.EXE -p -e "MySQLDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
Beispiel:  

    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforMySQLConsole.EXE -p -i "MySQLDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>Siehe auch  
[Executing the SSMA Console ausführen (MySQL)](https://msdn.microsoft.com/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
