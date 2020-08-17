---
description: Verwalten von Kenn Wörtern (accesstosql)
title: Verwalten von Kenn Wörtern (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 07/01/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b099d0f9-dd37-4c87-8b6f-ed0177881ea4
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: dc47389afdd9b8241a0d06960baf592639daa6cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88372856"
---
# <a name="managing-passwords-accesstosql"></a>Verwalten von Kenn Wörtern (accesstosql)
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
  
        -   Führen `SSMAforAccessConsole.exe` Sie das mit dem `-securepassword` und den Switch-Schalter in der Befehlszeile aus, und übergeben Sie die Server Verbindung oder die Skriptdatei mit dem Kenn Wort Knoten im Abschnitt Server Definition.  
  
        -   Bei der Eingabeaufforderung wird der Benutzer aufgefordert, das Daten Bank Kennwort einzugeben und zu bestätigen.  
  
            Die Server Definitions-IDs und die zugehörigen verschlüsselten Kenn Wörter werden in einer Datei auf dem lokalen Computer gespeichert.  

            &nbsp;

            _Beispiel 1:_
            
            Kennwort angeben

            ```console
            C:\SSMA\SSMAforAccessConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml"
            ```

            Kennwort für server_id ' XXX_1 ' eingeben: XXXXXXX
                
            Kennwort für server_id ' XXX_1 ' erneut eingeben: XXXXXXX  

            &nbsp;

            _Beispiel 2:_

            ```console
            C:\SSMA\SSMAforAccessConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml" -o
            ```

            Kennwort für server_id ' source_1 ' eingeben: XXXXXXX
                
            Kennwort für server_id ' source_1 ' erneut eingeben: XXXXXXX
                
            Kennwort für server_id ' target_1 ' eingeben: XXXXXXX
                
            Kennwort für server_id "Ziel _1" erneut eingeben: XXXXXXX  
  
    -   **Entfernen verschlüsselter Kenn Wörter**  
  
        Führen `SSMAforAccessConsole.exe` Sie das mit `-securepassword` dem `-remove` aus, und wechseln Sie in der Befehlszeile zum übergeben der Server-IDs, um die verschlüsselten Kenn Wörter aus der geschützten Speicherdatei auf dem lokalen Computer zu entfernen.  

        ```console
        C:\SSMA\SSMAforAccessConsole.EXE -securepassword -remove all
        C:\SSMA\SSMAforAccessConsole.EXE -securepassword -remove "source_1,target_1"
        ```
  
    -   **Auflisten von Server-IDs, deren Kenn Wörter verschlüsselt sind**  
  
        Führen Sie die SSMAforAccessConsole.exe mit dem aus `-securepassword` `-list` , und wechseln Sie in der Befehlszeile, um alle Server-IDs aufzulisten, deren Kenn Wörter verschlüsselt wurden.  

        ```console
        C:\SSMA\SSMAforAccessConsole.EXE -securepassword -list
        ```
  
    > [!NOTE]  
    > 1.  Das Kennwort im Klartext, das in der Skript-oder Server Verbindungs Datei angegeben ist, hat Vorrang vor dem verschlüsselten Kennwort in der gesicherten Datei.  
    > 2.  Wenn im Server Abschnitt der Server Verbindungs Datei oder der Skriptdatei kein Kennwort vorhanden ist oder wenn es nicht auf dem lokalen Computer gesichert wurde, werden Sie von der-Konsole aufgefordert, das Kennwort einzugeben.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Exportieren oder importieren verschlüsselter Kenn Wörter  
Mit der SSMA-Konsolenanwendung können Sie verschlüsselte Daten Bank Kennwörter, die in einer Datei auf dem lokalen Computer vorhanden sind, in eine gesicherte Datei exportieren und umgekehrt. Dies hilft bei der unabhängigen Erstellung der verschlüsselten Kenn Wörter. Die Export Funktion liest die Server-ID und das Kennwort aus dem lokalen geschützten Speicher und speichert die Informationen in einer verschlüsselten Datei. Der Benutzer wird aufgefordert, das Kennwort für die gesicherte Datei einzugeben. Stellen Sie sicher, dass das eingegebene Kennwort mindestens 8 Zeichen lang ist. Diese gesicherte Datei ist auf verschiedenen Computern portabel. Die Import Funktion liest die Server-ID und die Kenn Wort Informationen aus der gesicherten Datei. Der Benutzer wird aufgefordert, das Kennwort für die gesicherte Datei einzugeben, und fügt die Informationen an den lokalen geschützten Speicher an.  

### <a name="export-password"></a>Kennwort exportieren

1. Kennwort zum Schutz der exportierten Datei eingeben

2. `C:\SSMA\SSMAforAccessConsole.EXE -securepassword -export all "machine1passwords.file"`

3. Geben Sie das Kennwort zum Schutz der exportierten Datei ein: xxxxxxxx

4. Bestätigen Sie das Kennwort: xxxxxxxx

5. `C:\SSMA\SSMAforAccessConsole.EXE -p -e "AccessDB_1_1,Sql_1" "machine2passwords.file"`

6. Geben Sie das Kennwort zum Schutz der exportierten Datei ein: xxxxxxxx

7. Bestätigen Sie das Kennwort: xxxxxxxx  

### <a name="import-an-encrypted-password"></a>Importieren eines verschlüsselten Kennworts

1. Kennwort zum Schutz der importierten Datei eingeben

2. `C:\SSMA\SSMAforAccessConsole.EXE -securepassword -import all "machine1passwords.file"`

3. Kennwort eingeben, um die Server aus der verschlüsselten Datei zu importieren: xxxxxxxx

4. Bestätigen Sie das Kennwort: xxxxxxxx

5. `C:\SSMA\SSMAforAccessConsole.EXE -p -i "AccessDB_1,Sql_1" "machine2passwords.file"`

6. Kennwort eingeben, um die Server aus der verschlüsselten Datei zu importieren: xxxxxxxx

7. Bestätigen Sie das Kennwort: xxxxxxxx  

## <a name="see-also"></a>Weitere Informationen  
[Ausführen der SSMA-Konsole (Zugriff)](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
