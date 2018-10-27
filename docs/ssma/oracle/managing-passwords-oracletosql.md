---
title: Verwalten von Kennwörtern (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Managing Passwords in Oracle, Exporting or Importing Encrypted Password
- Managing passwords in Oracle, Securing Password
ms.assetid: 8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 903fd6b9af4bc363f5f37ea353ab9ddeb93e347c
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50099414"
---
# <a name="managing-passwords-oracletosql"></a>Verwalten von Kennwörtern (OracleToSQL)
In diesem Abschnitt wird zum Schützen von Kennwörter für die Datenbanken und das Verfahren zum Importieren oder exportieren diese auf Servern:  
  
1.  Sichern das Kennwort  
  
2.  Exportieren oder importieren das verschlüsselte Kennwort  
  
## <a name="securing-password"></a>Sichern das Kennwort  
SSMA ermöglicht Ihnen, ein Kennwort, eine Datenbank zu sichern.  
  
Verwenden Sie wie folgt vor, um eine sichere Verbindung zu implementieren:  
  
Geben Sie ein gültiges Kennwort ein, die mit einer der drei folgenden Methoden:  
  
1.  **Klartext:** Geben Sie das Datenbankkennwort, in der Value-Attribut des Knotens 'Password'. Es befindet sich unter dem Serverknoten für die Definition im Abschnitt "Server" des Server-Verbindungsdatei oder Skriptdatei.  
  
    Kennwörter in Klartext sind nicht sicher. Aus diesem Grund tritt die folgende Warnmeldung in der Konsolenausgabe: *"Server &lt;Server-Id&gt; Kennwort dient als nicht sicheren Klartext, SSMA-Console-Anwendung eine Option zum Schutz bietet der das Kennwort, Verschlüsselung, informieren Sie sich – Securepassword Option in der SSMA-Hilfedatei für Weitere Informationen."*  
  
    **Verschlüsselte Kennwörter:** das angegebene Kennwort ist, wird in diesem Fall in verschlüsselter Form auf dem lokalen Computer im ProtectedStorage.ssma gespeichert.  
  
    -   **Schützen von Kennwörtern**  
  
        -   Führen Sie die `SSMAforOracleConsole.exe` mit der `–securepassword` und Schalter in die Befehlszeile übergeben den Server-Verbindung oder ein Skript-Datei, die mit dem kennwortknoten im Abschnitt Definition Server hinzufügen.  
  
        -   An der Eingabeaufforderung wird der Benutzer aufgefordert, um das Datenbankkennwort, und bestätigen Sie es.  
  
            Die Server-Definitions-Ids und die entsprechenden verschlüsselte Kennwörter werden in einer Datei auf dem lokalen Computer gespeichert.  
            
            Beispiel 1:  
            
                Specify password
                
                C:\SSMA\SSMAforOracleConsole.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            Beispiel 2:
            
                C:\SSMA\SSMAforOracleConsole.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
    
    -   **Verschlüsselte Kennwörter entfernen**  
  
        Führen Sie die `SSMAforOracleConsole.exe` mit der`–securepassword` und `–remove` -Schalter an der Befehlszeile übergeben den Server-Ids, um die verschlüsselten Kennwörter aus der geschützten Speicherdatei vorhanden auf dem lokalen Computer zu entfernen.  
        
        Beispiel:  
        
            C:\SSMA\SSMAforOracleConsole.EXE –securepassword –remove all
            C:\SSMA\SSMAforOracleConsole.EXE –securepassword –remove "source_1,target_1"  
  
    -   **Auflisten von Server-Ids, deren Kennwörter verschlüsselt sind**  
  
        Führen Sie die `SSMAforOracleConsole.exe` mit der `–securepassword` und `–list` -Schalter an der Befehlszeile aus, um alle Server-Ids auflisten, deren Kennwörter verschlüsselt wurden.  
  
        Beispiel:  
        
            C:\SSMA\SSMAforOracleConsole.EXE –securepassword –list  
  
    > [!NOTE]  
    > 1.  Das Kennwort als Klartext im Skript oder eine Server-Verbindungsdatei erwähnt haben Vorrang vor das verschlüsselte Kennwort in der gesicherten Datei.  
    > 2.  Wenn kein Kennwort im Abschnitt "Server" die Server-Verbindungsdatei oder die Datei vorhanden ist, oder wenn sie nicht auf dem lokalen Computer gesichert wurden, werden Sie von die Konsole aufgefordert, das Kennwort eingeben.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Exportieren oder importieren verschlüsselte Kennwörter  
Die SSMA-Console-Anwendung können Sie verschlüsselte Datenbankkennwörter in einer Datei auf dem lokalen Computer vorhanden, eine geschützte Datei und umgekehrt zu exportieren. Er hilft bei der Erstellung des Computers verschlüsselte Kennwörter unabhängig. Funktionen zum Exportieren der liest, der Id und Kennwort aus der lokalen geschützten Speicher ab und speichert die Informationen in einer verschlüsselten Datei. Der Benutzer wird aufgefordert, das Kennwort für die sichere Datei eingeben. Stellen Sie sicher, dass das eingegebene Kennwort mindestens 8 Zeichenlänge beträgt. Diese sichere Datei ist auf unterschiedlichen Computern übertragbar. Importfunktionalität, liest der Server-Id und Kennwort aus der gesicherten Datei. Der Benutzer wird aufgefordert, das Kennwort für die sichere Datei einzugeben und fügt die Informationen im lokalen geschützten Speicher hinzu.  
  
Beispiel:  

    Export password
    
    Enter password for protecting the exported file C:\SSMA\SSMAforOracleConsole.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE –p –e "OracleDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
Beispiel:  

    Import an encrypted password
    
    Enter password for protecting the imported file C:\SSMA\SSMAforOracleConsole.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE –p –i "OracleDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>Siehe auch  
[Executing the SSMA Console ausführen (Oracle)](http://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
