---
title: Erstellen von Skriptdateien (oracledesql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Script File Creation, Configuring Oracle Console Settings
- Script File Creation, Non-Configurable option
- Script File Creation, Script File Validation
ms.assetid: 55e5bc68-3040-4f07-bb00-0408a17c9821
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: a4ee7047e2c517f05f311bf4e842f8f4c64ca8fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264240"
---
# <a name="creating-script-files-oracletosql"></a>Erstellen von Skriptdateien (OracleToSQL)
Der erste Schritt vor dem Starten der SSMA-Konsolenanwendung besteht darin, die Skriptdatei zu erstellen und bei Bedarf die Variablen Wert Datei und die Server Verbindungs Datei zu erstellen.  
  
Die Skriptdatei kann in drei Abschnitte unterteilt werden: Viz..,:  
  
1.  **config:** Ermöglicht dem Benutzer das Festlegen der Konfigurationsparameter für die Konsolenanwendung.  
  
2.  **Server:** Ermöglicht dem Benutzer das Festlegen der Quell-/zielserverdefinitionen. Dies kann sich auch in einer separaten Server Verbindungs Datei befinden.  
  
3.  **Skript-Befehle:** Ermöglicht dem Benutzer das Ausführen von SSMA-Workflow Befehlen.  
  
Jeder Abschnitt wird im folgenden ausführlich beschrieben:  
  
## <a name="configuring-oracle-console-settings"></a>Konfigurieren von Oracle-Konsolen Einstellungen  
Die Konfigurationen eines Skripts werden in der Konsolen Skriptdatei angezeigt.  
  
Wenn eines der Elemente im Konfigurations Knoten angegeben wird, werden diese als globale Einstellung festgelegt, d. h., Sie sind für alle Skript Befehle anwendbar. Diese Konfigurationselemente können auch in jedem Befehl im Abschnitt Skript Befehl festgelegt werden, wenn der Benutzer die globale Einstellung überschreiben möchte.  
  
Die vom benutzerkonfigurierbaren Optionen umfassen:  
  
1.  **Ausgabefenster Anbieter:** Wenn das Attribut "Unterdrückung-Messages" auf "true" festgelegt ist, werden die Befehls spezifischen Nachrichten nicht in der Konsole angezeigt. Die Beschreibung des Attributs ist unten angegeben:  
  
    -   Destination: gibt an, ob die Ausgabe in einer Datei oder einem stdout gedruckt werden muss. Der Standardwert ist false.  
  
    -   Dateiname: der Pfad der Datei (optional).  
  
    -   unterdrücken-Messages: unterdrückt Meldungen in der Konsole. Dies ist standardmäßig ' false '.  
  
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
    *noch*  
  
    ```xml  
    <...All commands...>  
  
      <output-window  
  
         suppress-messages="<true/false>"   (optional)  
  
         destination="<file/stdout>"        (optional)  
  
         file-name="<file-name>"            (optional)  
  
       />  
  
    </...All commands...>  
    ```  
  
2.  **Verbindungsanbieter für Daten Migration:** Hiermit wird angegeben, welcher Quell-/Zielserver für die Datenmigration in Erwägung gezogen werden soll.  Quelle-Use-Last-used gibt an, dass der zuletzt verwendete Quell Server für die Datenmigration verwendet wird. Entsprechend gibt Target-Use-Last-used an, dass der zuletzt verwendete Zielserver für die Datenmigration verwendet wird. Der Benutzer kann auch den Server (Quelle oder Ziel) mithilfe der Attribute Quell Server oder Zielserver angeben.  
  
    Es kann nur ein oder das andere angegebene Attribut verwendet werden, d. h.:  
  
    -   Source-Use-Last-used = "true" (Standard) oder Source-Server = "source_servername"  
  
    -   Target-Use-Last-used = "true" (Standard) oder Target-Server = "target_servername"  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <data-migration-connection source-use-last-used="true"  
  
                                 target-server="<target-server-unique-name>"/>  
  
    </output-providers>  
    ```  
    *noch*  
  
    ```xml  
    <migrate-data>  
  
      <data-migration-connection   source-server="<source-server-unique-name>"  
  
                                   target-use-last-used="true"/>  
  
    </migrate-data>  
    ```  
  
3.  **Benutzereingabe-Popup:** Dies ermöglicht die Behandlung von Fehlern, wenn die Objekte aus der Datenbank geladen werden. Der Benutzer stellt die Eingabemodi bereit, und bei einem Fehler wird die-Konsole fortgesetzt, wenn der Benutzer angibt.  
  
    Die Modi umfassen Folgendes:  
  
    -   **Ask-user-** Fordert den Benutzer auf, den Vorgang fortzusetzen ("yes") oder einen Fehler ("Nein").  
  
    -   **Fehler-** In der Konsole wird ein Fehler angezeigt, und die Ausführung wird angehalten.  
  
    -   **fortfahren:** Die Konsole wird mit der Ausführung fortgesetzt.  
  
    Der Standardmodus ist **Fehler**.  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </output-providers>  
    ```  
    *noch*  
  
    ```xml  
    <!-- Connect to target database -->  
  
    <connect-target-database server="<target-server-unique-name>">  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </connect-target-database>  
    ```  
  
4.  **Anbieter für erneute Verbindungs Herstellung:** Dies ermöglicht es dem Benutzer, die Einstellungen für die erneute Verbindungs Herstellung bei Verbindungsfehlern festzulegen. Dies kann sowohl für Quell-als auch für Zielserver festgelegt werden.  
  
    Die Modi für die erneute Verbindung lauten wie folgt:  
  
    -   Verbindung-to-Last-used-Server: Wenn die Verbindung nicht aktiv ist, wird versucht, die Verbindung mit dem letzten Server, der höchstens fünfmal verwendet wird, wiederherzustellen.  
  
    -   Generate-an-error: Wenn die Verbindung nicht aktiv ist, wird ein Fehler generiert.  
  
    Der Standardmodus ist " **Generate-an-error**".  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <reconnect-manager on-source-reconnect="<reconnect-to-last-used-server/generate-an-error>"  
  
                         on-target-reconnect="<reconnect-to-last-used-server/generate-an-error>"/>  
  
    </output-providers>  
    ```  
    *noch*  
  
    ```xml  
    <!--synchronization-->  
  
    <synchronize-target>  
  
      <reconnect-manager on-target-reconnect="reconnect-to-last-used-server"/>  
  
    </synchronize-target>  
    ```  
    *noch*  
  
    ```xml  
    <!--data migration-->  
  
    <migrate-data server="<target-server-unique-name>">  
  
      <reconnect-manager  
  
        on-source-reconnect="reconnect-to-last-used-server"  
  
        on-target-reconnect="generate-an-error"/>  
  
    </migrate-data>  
    ```  
  
5.  **Konverterüberschreibungs Anbieter:** Dadurch kann der Benutzer Objekte verarbeiten, die bereits in der zielmetabase vorhanden sind. Folgende Aktionen sind möglich:  
  
    -   Fehler: in der Konsole wird ein Fehler angezeigt, und die Ausführung wird angehalten.  
  
    -   Überschreiben: überschreibt vorhandene Objektwerte. Diese Aktion wird standardmäßig ausgeführt.  
  
    -   Skip: die Konsole überspringt die Objekte, die bereits in der Datenbank vorhanden sind.  
  
    -   Ask-user: fordert den Benutzer zur Eingabe auf (' yes '/' No ')  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <object-overwrite action="<error/skip/overwrite/ask-user>"/>  
  
    </output-providers>  
    ```  
    *noch*  
  
    ```xml  
    <convert-schema object-name="<object-name>">  
  
      <object-overwrite action="<error/skip/overwrite/ask-user>"/>  
  
    </convert-schema>  
    ```  
  
6.  Anbieter für erforderliche Komponenten **fehlgeschlagen:** Dies ermöglicht es dem Benutzer, alle Voraussetzungen zu erfüllen, die für die Verarbeitung eines Befehls erforderlich sind. Standardmäßig ist der Strict-Modus ' false '. Wenn er auf "true" festgelegt ist, wird eine Ausnahme generiert, damit die Voraussetzungen nicht erfüllt werden.  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <prerequisites strict-mode="<true/false>"/>  
  
    </output-providers>  
    ```  
  
7.  **Vorgang beendet:** Wenn der Benutzer während der Mitte des Vorgangs den Vorgang abbrechen möchte, kann der Hotkey **"STRG + C"** verwendet werden. SSMA für die Oracle-Konsole wartet auf den Abschluss des Vorgangs und beendet die Konsolen Ausführung.  
  
    Wenn der Benutzer die Ausführung sofort beenden möchte, kann der Hotkey **"STRG + C"** erneut zum abrupten Beenden der SSMA-Konsolenanwendung gedrückt werden.  
  
8.  **Fortschritts Anbieter:** Informiert den Fortschritt der einzelnen Konsolenbefehle. Diese Einstellung ist standardmäßig deaktiviert. Die Attribute für die Fortschritts Berichterstattung umfassen Folgendes:  
  
    -   aus  
  
    -   Alle-1%  
  
    -   Alle-2%  
  
    -   Alle-5%  
  
    -   Alle-10%  
  
    -   alle-20%  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <progress-reporting enable="<true/false>"            (optional)  
  
                          report-messages="<true/false>"   (optional)  
  
                          report-progress="every-1%/every-2%/every-5%/every-10%/every-20%/off" (optional)/>  
  
    </output-providers>  
    ```  
    *noch*  
  
    ```xml  
    <...All commands...>  
  
      <progress-reporting  
  
        enable="<true/false>"            (optional)  
  
        report-messages="<true/false>"   (optional)  
  
        report-progress="every-1%/every-2%/every-5%/every-10%/every-20%/off"     (optional)/>  
  
    </...All commands...>  
    ```  
  
9. Ausführlichkeit der Protokollierung **:** Legt den ausführlichkeits Grad für das Protokoll fest. Dies entspricht der Option Alle Kategorien in der Benutzeroberfläche. Standardmäßig ist der ausführlichkeits Grad des Protokolls "Error".  
  
    Die Optionen auf Protokollierungsebene umfassen Folgendes:  
  
    -   Schwerwiegender Fehler: nur schwerwiegende Fehlermeldungen werden protokolliert.  
  
    -   Fehler: nur Fehler-und schwerwiegende Fehlermeldungen werden protokolliert.  
  
    -   Warnung: alle Ebenen mit Ausnahme von Debug-und Info-Nachrichten werden protokolliert.  
  
    -   Info: alle Ebenen außer Debugmeldungen werden protokolliert.  
  
    -   Debug: alle protokollierten Nachrichten Ebenen.  
  
    > [!NOTE]  
    > Obligatorische Nachrichten werden auf jeder Ebene protokolliert.  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <log-verbosity level="fatal-error/error/warning/info/debug"/>  
  
    </output-providers>  
    ```  
    *noch*  
  
    ```xml  
    <...All commands...>  
  
      <log-verbosity level="fatal-error/error/warning/info/debug"/>  
  
    </...All commands...>  
    ```  
  
10. **Verschlüsseltes Kennwort überschreiben:** Wenn "true", wird das im Server Definitions Abschnitt der Server Verbindungs Datei oder in der Skriptdatei angegebene Klartext überschrieben, sofern vorhanden, das verschlüsselte Kennwort, das im geschützten Speicher gespeichert ist. Wenn im Klartext kein Kennwort angegeben ist, wird der Benutzer zur Eingabe des Kennworts aufgefordert.  
  
    Es treten zwei Fälle auf:  
  
    1.  Wenn die Außerkraftsetzungs Option auf **false**gesetzt ist, wird die Such Reihenfolge durch&gt;den Benutzer geschützt&gt; &gt;.  
  
    2.  Wenn die Überschreibungs Option **true**ist, ist die Reihenfolge der Suche ein&gt;Skript für die Datei&gt;-Server-Verbindungs Datei.  
  
    **Beispiel:**  
  
    ```xml  
    <output-providers>  
  
      <encrypted-password override="<true/false>"/>  
  
    </output-providers>  
    ```  
  
Die Option kann nicht konfiguriert werden:  
  
-   **Maximale Anzahl von erneuten Verbindungs versuchen:** Wenn eine festgelegte Verbindung aufgrund eines Netzwerk Fehlers ausfällt oder unterbrochen wird, muss der Server erneut verbunden werden. Die Versuche der erneuten Verbindung sind maximal **5** Wiederholungen zulässig, danach wird die Verbindung automatisch wieder hergestellt. Die Funktion der automatischen erneuten Verbindungs Herstellung reduziert den Aufwand für das erneute Ausführen des Skripts.  
  
## <a name="server-connection-parameters"></a>Server Verbindungsparameter  
Server Verbindungsparameter können in der Skriptdatei oder in der Server Verbindungs Datei definiert werden. Weitere Informationen finden Sie im Abschnitt [Erstellen der Server Verbindungs Dateien &#40;oracledesql&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md) .  
  
## <a name="script-commands"></a>Skriptbefehle  
Die Skriptdatei enthält eine Sequenz von Migrations Workflow Befehlen im XML-Format. Die SSMA-Konsolenanwendung verarbeitet die Migration in der Reihenfolge der Befehle, die in der Skriptdatei angezeigt werden.  
  
Beispielsweise folgt eine typische Datenmigration einer bestimmten Tabelle in einer Oracle-Datenbank der Hierarchie von: Schema-&gt; Table.  
  
Wenn alle Befehle in der Skriptdatei erfolgreich ausgeführt werden, wird die SSMA-Konsolenanwendung beendet, und das Steuerelement wird an den Benutzer zurückgegeben. Der Inhalt einer Skriptdatei ist mehr oder weniger statisch und enthält Variablen Informationen, die entweder in einer [Datei zum Erstellen von Variablen Werten &#40;oracletosql&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md) oder in einem separaten Abschnitt in der Skriptdatei für Variablen Werte enthalten sind.  
  
**Beispiel:**  
  
```xml  
<!--Sample of script file commands -->  
  
<ssma-script-file>  
  
  <script-commands>  
  
    <create-new-project project-folder="<project-folder>"  
  
                        project-name="<project-name>"  
  
                        overwrite-if-exists="<true/false>"/>  
  
    <connect-source-database server="<source-server-unique-name>"/>  
  
    <save-project/>  
  
    <close-project/>  
  
  </script-commands>  
  
</ssma-script-file>  
```  
Vorlagen, die aus 3 Skriptdateien (zum Ausführen verschiedener Szenarios), einer Variablen Wert Datei und einer Server Verbindungs Datei bestehen, werden im Beispiel Ordner der Konsolen Skripts des Produkt Verzeichnisses bereitgestellt:  
  
-   "Bewermentreportgenerationsample. xml"  
  
-   "Systemversionanddatamigrationsample. xml"  
  
-   Sqlstatuementinversionsample. XML  
  
-   Variablevaluefilesample. XML  
  
-   Serversconnectionfilesample. XML  
  
Sie können die Vorlagen (Dateien) ausführen, nachdem Sie die darin angezeigten Parameter für Relevanz geändert haben.  
  
Eine komplette Liste der Skript Befehle finden Sie unter [Ausführen der SSMA-Konsole &#40;oracleto SQL&#41;](../../ssma/oracle/executing-the-ssma-console-oracletosql.md)  
  
## <a name="script-file-validation"></a>Überprüfung der Skriptdatei  
Der Benutzer kann seine Skriptdatei problemlos anhand der Schema Definitionsdatei **"O2SSConsoleScriptSchema. xsd"** überprüfen, die im Ordner "Schemas" verfügbar ist.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt beim Betrieb der Konsole ist das [Erstellen von Variablen Wert Dateien &#40;oracleto SQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen von Variablen Wert Dateien &#40;oracleto SQL-&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
