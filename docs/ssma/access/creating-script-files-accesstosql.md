---
title: Erstellen von Skriptdateien (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 64dfe192-965c-49d4-a3ea-848fbc5f619f
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 4c7f94672642e0a5d8fa8979dd3972f608519ce5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799358"
---
# <a name="creating-script-files-accesstosql"></a>Erstellen von Skriptdateien (AccessToSQL)
Der erste Schritt vor dem Starten der Anwendung der SSMA-Konsole die Skriptdatei erstellt werden, und bei Bedarf den Wert der Variablen-Datei und die Server-Verbindungsdatei erstellen.  
  
Die Skriptdatei kann viz in drei Abschnitte unterteilt werden..,:  
  
1.  **Config:** ermöglicht es dem Benutzer die Konfigurationsparameter für die Konsolenanwendung festgelegt.  
  
2.  **Server:** ermöglicht es den Benutzer, die Quelle/Ziel-Serverdefinitionen festzulegen. Dies kann auch in einem separaten Server-Verbindungsdatei sein.  
  
3.  **Befehle des Skripts:** ermöglicht es dem Benutzer zum Ausführen von Befehlen der SSMA-Workflow.  
  
Jeder Abschnitt wird unten im Detail beschrieben:  
  
## <a name="configuring-access-console-settings"></a>Konfigurieren der zugriffseinstellungen für die Konsole  
Die Konfigurationen eines Skripts werden in der Skriptdatei für die Konsole angezeigt.  
  
Wenn eines der Elemente im Knoten "Konfiguration" angegeben werden, werden festgelegt als die globale Einstellung d. h. sie gelten für alle Befehle des Skripts. Zu diesen Konfigurationselementen können auch festgelegt werden in jedem Befehl im Skript-Command-Abschnitt, wenn der Benutzer die globale Einstellung überschreiben möchte.  
  
Die vom Benutzer konfigurierbaren Optionen umfassen:  
  
1.  **Ausgabe-Fenster-Anbieter:** Wenn unterdrücken-Messages-Attribut festgelegt ist, auf "true", die zugehörigen Nachrichten werden nicht in der Konsole angezeigt zu erhalten. Attribute werden nachfolgend beschrieben:  
  
    -   Ziel: Gibt an, ob die Ausgabe in eine Datei oder ein "stdout" ausgegeben abrufen muss. Dies ist standardmäßig "false".  
  
    -   Dateiname: der Pfad der Datei (Optional).  
  
    -   Unterdrücken Sie Nachrichten: Meldungen in der Konsole unterdrückt. Dies ist standardmäßig "false".  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <output-window  
  
        suppress-messages="<true/false>"   (optional)  
  
        destination="<file/stdout>"        (optional)  
  
        file-name="<file-name>"            (optional)  
  
       />  
  
    </output-providers>  
    ```  
    *Oder*  
  
    ```xml  
    <…All commands…>  
  
      <output-window  
  
         suppress-messages="<true/false>"   (optional)  
  
         destination="<file/stdout>"        (optional)  
  
         file-name="<file-name>"            (optional)  
  
       />  
  
    </…All commands…>  
    ```  
  
2.  **Data Migration-Verbindungsanbieter:** Dies gibt an, welche Quelle/Ziel-Server wird bei der Migration Daten berücksichtigt werden.  Source-Verwendung – zuletzt verwendete gibt an, dass die zuletzt verwendeten Quellserver für die Datenmigration verwendet wird. Auf ähnliche Weise gibt das Ziel-Verwendung – zuletzt verwendete an, dass der zuletzt verwendeten Zielserver für die Datenmigration verwendet wird. Der Benutzer kann auch auf den Server (Quelle oder Ziel) angeben, mithilfe der Attribute-Quellserver oder Zielserver.  
  
    Nur ein oder anderen angegebenen Attributs kann z. B. verwendet werden:  
  
    - Source-Verwendung – zuletzt verwendete = "True" (Standard) oder die Quellserver = "Source_servername"  
  
    - Ziel-Verwendung – zuletzt verwendete = "True" (Standard) oder Ziel-Server = "Target_servername"  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <data-migration-connection   source-use-last-used="true"  
  
                                   target-server="target_1"/>  
  
    </output-providers>  
    ```  
    *Oder*  
  
    ```xml  
    <migrate-data>  
  
      <data-migration-connection   source-server="source_1"  
  
                                   target-use-last-used="true"/>  
  
    </migrate-data>  
    ```  
  
3.  **Benutzer-Eingabe-Popup:** Dies ermöglicht die Behandlung von Fehlern, wenn die Objekte aus der Datenbank geladen werden. Der Benutzer gibt die Eingabemodi an, und bei einem Fehler die Konsole wird fortgesetzt, wie Benutzer angibt.  
  
    Die Modi sind:  
  
    -   **Bitten Sie Benutzer -** fordert den Benutzer auf continue('yes') oder Fehler auf ("No").  
  
    -   **Fehler:** die Konsole zeigt einen Fehler an und hält die Ausführung.  
  
    -   **weiterhin-** die Konsole, die mit der Ausführung wird fortgesetzt.  
  
    Der Standardmodus ist **Fehler**.  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </output-providers>  
    ```  
    *Oder*  
  
    ```xml  
    <!-- Connect to target database -->  
  
    <connect-target-database server="target_0">  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </connect-target-database>  
    ```  
  
4.  **Verbinden Sie die Anbieter:** Dies ermöglicht dem Benutzer die Einstellungen für die erneute Verbindung bei einem Verbindungsfehler festgelegt. Dies kann für die Quell-und Ziel festgelegt werden.  
  
    Die erneute Verbindung Modi sind:  
  
    -   erneut eine Verbindung herstellen und letzten-verwendet-Server: Wenn die Verbindung nicht aktiv ist, versucht wird, mit dem letzten maximal 5 Mal verwendete Server verbinden.  
  
    -   generiert einen Fehler: Wenn die Verbindung nicht aktiv ist, wird ein Fehler generiert.  
  
    Der Standardmodus ist **generieren einen Fehler**.  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
     <reconnect-manager on-source-reconnect="<reconnect-to-last-used-server/generate-an-error>"  
  
                        on-target-reconnect="<reconnect-to-last-used-server/generate-an-error>"/>  
  
    </output-providers>  
    ```  
    *Oder*  
  
    ```xml  
    <!--synchronization-->  
  
    <synchronize-target>  
  
      <reconnect-manager on-target-reconnect="reconnect-to-last-used-server"/>  
  
    </synchronize-target>  
    ```  
    *Oder*  
  
    ```xml  
    <!--data migration-->  
  
    <migrate-data server="target_0">  
  
      <reconnect-manager  
  
        on-source-reconnect="reconnect-to-last-used-server"  
  
        on-target-reconnect="generate-an-error"/>  
  
    </migrate-data>  
    ```  
  
5.  **Konverter überschreiben-Anbieter:** Dadurch kann der Benutzer aus, um Objekte zu verarbeiten, die bereits auf dem Zielgerät vorhanden sind Metabasis. Die möglichen Aktionen gehören:  
  
    -   Fehler: die Konsole zeigt einen Fehler an und hält die Ausführung.  
  
    -   Überschreiben: überschreibt vorhandene Werte des Objekts. Standardmäßig ist diese Aktion erfolgt.  
  
    -   übersprungen: die Konsole überspringt die Objekte, die bereits vorhanden sind, in der Datenbank  
  
    -   Bitten Sie Benutzer: der Benutzer zur Eingabe aufgefordert ('Ja' / 'no')  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <object-overwrite action="<error|skip|overwrite|ask-user>"/>  
  
    </output-providers>  
    ```  
    *Oder*  
  
    ```xml  
    <convert-schema object-name="ssma.TT1">  
  
      <object-overwrite action="<error|skip|overwrite|ask-user>"/>  
  
    </convert-schema>  
    ```  
  
6.  **Fehlerhafte Voraussetzungen-Anbieter:** Dadurch kann der Benutzer alle erforderlichen Komponenten zu behandeln, die für die Verarbeitung eines Befehls erforderlich sind. Standardmäßig ist der strict-Modus – "false". Wenn sie festgelegt ist, auf "true", eine Ausnahme wird generiert, für die Voraussetzungen erfüllt.  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <prerequisites strict-mode="<true|false>"/>  
  
    </output-providers>  
    ```  
  
7.  **Vorgang zum Beenden:** während des Mid-Vorgangs, wenn der Benutzer klicken Sie dann den Vorgang beenden möchte **"STRG + C"** Hotkey kann verwendet werden. SSMA für Access-Konsole nach Abschluss des Vorgangs warten und beendet die Ausführung der Verwaltungskonsole.  
  
    Wenn der Benutzer die Ausführung dann sofort beenden möchte **"STRG + C"** Tastaturbefehl für abrupten Beendigung der Anwendung SSMA-Konsole erneut gedrückt werden kann.  
  
8.  **Status-Anbieter:** informiert über den Fortschritt der einzelnen Befehle für die Konsole. Dies ist standardmäßig deaktiviert. Die Statusberichte-Attribute umfassen:  
  
    -   off  
  
    -   every - 1 %  
  
    -   alle %2%  
  
    -   alle 5 %  
  
    -   alle 10 %  
  
    -   EVERY - 20 %  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
     <progress-reporting enable="<true|false>"           (optional)  
  
                         report-messages="<true|false>"  (optional)  
  
                         report-progress="every-1%|every-2%|every-5%|every-10%|every-20%|off" (optional)/>  
  
    </output-providers>  
    ```  
    *Oder*  
  
    ```xml  
    <…All commands…>  
  
      <progress-reporting  
  
        enable="<true|false>"              (optional)  
  
        report-messages="<true|false>"     (optional)  
  
        report-progress="every-1%|every-2%|every-5%|every-10%|every-20%|off"     (optional)/>  
  
    </…All commands…>  
    ```  
  
9. **Ausführlichkeit der Protokollierung:** legt Protokollebene Ausführlichkeit. Dies entspricht der Option alle Kategorien auf der Benutzeroberfläche. Standardmäßig ist der Ausführlichkeitsgrad des Protokolls "Error".  
  
    Die Protokollierung auf Serverebene Optionen umfassen:  
  
    -   Schwerwiegender Fehler: Nachrichten, die nur schwerwiegende Fehler protokolliert werden.  
  
    -   Fehler: Es werden nur Meldungen für Fehler und schwerwiegende Fehler protokolliert.  
  
    -   Warnung: alle Ebenen mit Ausnahme von Debug- und Info Nachrichten protokolliert werden.  
  
    -   Info: alle Ebenen außer der Debugmeldungen protokolliert werden.  
  
    -   Debuggen: alle Ebenen der Nachrichten protokolliert.  
  
    > [!NOTE]  
    > Obligatorische Nachrichten werden auf jeder Ebene protokolliert.  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <log-verbosity level="fatal-error/error/warning/info/debug"/>  
  
    </output-providers>  
    ```  
    *Oder*  
  
    ```xml  
    <…All commands…>  
  
      <log-verbosity level="fatal-error/error/warning/info/debug"/>  
  
    </…All commands…>  
    ```  
  
10. **Außerkraftsetzung verschlüsselte Kennwort:** bei "true", das unverschlüsselte Kennwort angegeben im Abschnitt Definition Server, der Server-Verbindungsdatei oder in der Skriptdatei, Außerkraftsetzungen, die das verschlüsselte Kennwort gespeichert, die im Speicher geschützt, wenn vorhanden ist. Wenn kein Kennwort als Klartext angegeben wird, wird der Benutzer aufgefordert, um das Kennwort einzugeben.  
  
    Hier entstehen zwei Fälle:  
  
    1.  Wenn Option zur Außerkraftsetzung ist **"false"**, die Reihenfolge der Suche werden auf geschützten Speicher -&gt;Skript-Datei -&gt;Server Connection-Datei –&gt; Benutzer auffordern.  
  
    2.  Wenn Option zur Außerkraftsetzung ist **"true"**, die Reihenfolge der Suche werden Skript-Datei -&gt;Server Connection-Datei –&gt;Benutzer auffordern.  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <encrypted-password override="<true/false>"/>  
  
    </output-providers>  
    ```  
  
Die Option nicht konfiguriert ist:  
  
-   **Maximale Verbindungswiederherstellungsversuchen:** der Server ist erforderlich, um die Verbindung wiederhergestellt werden, wenn eine bereits hergestellte Verbindung ein auftritt Timeout oder unterbrochen wird aufgrund von Netzwerkfehlern,. Die Versuche der verbindungswiederherstellung dürfen maximal **5** Wiederholungen nach, die die Konsole wird automatisch der verbindungswiederherstellung ausführt. Die Einrichtung der automatischen erneuten Herstellen einer Verbindung reduziert Ihres Aufwands in das Skript erneut ausführen.  
  
## <a name="server-connection-parameters"></a>Server-Verbindungsparameter  
Server-Verbindungsparameter können in der Skriptdatei oder in der Server-Connection-Datei definiert werden. Finden Sie in der [erstellen den Server Connection Files &#40;AccessToSQL&#41; ](../../ssma/access/creating-the-server-connection-files-accesstosql.md) finden Sie weitere Details.  
  
## <a name="script-commands"></a>Skriptbefehle  
Die Skriptdatei enthält eine Sequenz von Workflow-migrationsbefehle in das XML-Format. Die SSMA-Console-Anwendung verarbeitet die Migration in der Reihenfolge die Befehle in der Skriptdatei angezeigt werden.  
  
Zum Beispiel folgt eine typische Datenmigration von einer bestimmten Tabelle in einer Access-Datenbank die Hierarchie der: Datenbank -&gt; Tabelle.  
  
Wenn alle Befehle in der Skriptdatei erfolgreich ausgeführt werden, wird die SSMA-Console-Anwendung beendet, und das Steuerelement an den Benutzer zurückgibt. Den Inhalt einer Skriptdatei sind mehr oder weniger statisch mit Variablen Informationen enthalten, entweder in einem [Variable Value Files](creating-variable-value-files-accesstosql.md) oder in einem separaten Abschnitt innerhalb der Skriptdatei für Variable Werte.  
  
**Beispiel:**  
  
```xml  
<!--Sample of script file commands -->  
  
<ssma-script-file>  
  
  <script-commands>  
  
    <create-new-project project-folder="$project_folder$"  
  
                        project-name="$project_name$"  
  
                        overwrite-if-exists="true"/>  
  
    <connect-source-database server="source_2"/>  
  
    <save-project/>  
  
    <close-project/>  
  
  </script-commands>  
  
</ssma-script-file>  
```  
Vorlagen, bestehend aus 3-Skriptdateien (zum Ausführen von verschiedenen Szenarien), Wert der Variablen, und eine Server-Connection-Datei werden im Ordner "Beispielskripts für die Konsole" von der Produkt-Verzeichnis bereitgestellt:  
  
-   AssessmentReportGenerationSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   VariableValueFileSample.xml  
  
-   ServersConnectionFileSample.xml  
  
Sie können die Vorlagen (Dateien) ausführen, nach dem Ändern der Parameter für Relevanz darin angezeigt.  
  
Vollständige Liste der Befehle des Skripts befinden sich [Executing the SSMA Console ausführen &#40;AccessToSQL&#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="script-file-validation"></a>Skriptvalidierung-Datei  
Benutzer kann ganz einfach überprüfen, sein Skriptdatei anhand der Schemadefinitionsdatei **"A2SSConsoleScriptSchema.xsd"** in den Ordner "Schemas" verfügbar.  
  
## <a name="next-step"></a>Nächster Schritt
Der nächste Schritt in der Konsole ausgeführt wird [erstellen Variable Value Files &#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Erstellen die Variable Value Files &#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
  
