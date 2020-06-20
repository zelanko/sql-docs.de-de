---
title: Konfigurieren und Verwalten von Thesaurusdateien für die Volltextsuche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], configuring
- thesaurus [full-text search]
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67f0a5af7be4f41ce33692e5f28ad5adf676980c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997639"
---
# <a name="configure-and-manage-thesaurus-files-for-full-text-search"></a>Konfigurieren und Verwalten von Thesaurusdateien für die Volltextsuche
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kann bei Volltextabfragen ein Thesaurus verwendet werden, um nach Synonymen der vom Benutzer angegebenen Begriffe zu suchen. Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Thesaurus* definiert Synonyme für eine bestimmte Sprache. Systemadministratoren können zwei Formen von Synonymen definieren: Erweiterungssätze und Ersetzungssätze. Indem Sie einen Thesaurus entwickeln, der genau auf Ihre Volltextdaten abgestimmt ist, können Sie den Bereich der Volltextabfragen für diese Daten effektiv erweitern. Der Thesaurusvergleich erfolgt für alle [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) - und [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) -Abfragen sowie für alle [CONTAINS](/sql/t-sql/queries/contains-transact-sql) - und [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) -Abfragen, in denen die FORMSOF THESAURUS-Klausel angegeben ist.  
  
##  <a name="basic-tasks-for-setting-up-a-thesaurus-file"></a><a name="tasks"></a>Grundlegende Aufgaben zum Einrichten einer Thesaurusdatei  
 Bevor bei Volltextsuchabfragen auf der Serverinstanz nach Synonymen in einer bestimmten Sprache gesucht werden kann, müssen Sie Thesauruszuordnungen (Synonyme) für diese Sprache definieren. Jeder Thesaurus muss manuell konfiguriert werden, um Folgendes zu definieren:  
  
-   Einstellung für diakritische Zeichen  
  
     Bei einem bestimmten Thesaurus sind alle Suchmuster entweder sensibel oder nicht für diakritische Zeichen wie z. b. Tilde ( **~** ), akute Akzente (**??**) oder Umlaut (**??**). (das heißt, Unterscheidung nach *Akzent* oder *Akzent*). Nehmen Sie beispielsweise an, dass Sie das Muster "CAF?" angeben. das in einer Volltextabfrage durch andere Muster ersetzt werden soll. Wenn der Thesaurus keine Unterscheidung nach Akzent hat, ersetzt die Volltextsuche die Muster "CAF?". und „cafe“. Wenn der Thesaurus nach Akzent unterscheidet, ersetzt die Volltextsuche nur das Muster "CAF?". Standardmäßig wird bei einem Thesaurus nicht nach Akzent unterschieden.  
  
-   Erweiterungssatz  
  
     Ein Erweiterungssatz enthält eine Gruppe von Synonymen wie "writer", "author" und "journalist", die bei einer Volltextabfrage ausgetauscht werden. Abfragen, die eine Übereinstimmung für ein beliebiges Synonym in einem Erweiterungssatz enthalten, werden erweitert, um jedes andere Synonym im Erweiterungssatz einzubeziehen.  
  
     Weitere Informationen finden Sie unter "XML-Struktur eines Erweiterungssatzes" weiter unten in diesem Thema.  
  
-   Ersetzungssatz  
  
     Ein Ersetzungssatz enthält ein durch einen Substitutionssatz zu ersetzendes Textmuster. Ein Beispiel dafür finden Sie im Abschnitt "XML-Struktur eines Ersetzungssatzes" weiter unten in diesem Thema.  
  
  
##  <a name="initial-content-of-the-thesaurus-files"></a><a name="initial_thesaurus_files"></a>Ursprünglicher Inhalt der Thesaurusdateien  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt einen Satz von XML-Thesaurusdateien bereit, und zwar eine für jede unterstützte Sprache. Diese Dateien sind im Wesentlichen leer. Sie enthalten nur die XML-Hauptstruktur, die alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Thesaurusdateien aufweisen, sowie einen auskommentierten Beispielthesaurus.  
  
 Alle im Lieferumfang von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthaltenen Thesaurusdateien enthalten folgenden XML-Code:  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
  
##  <a name="location-of-the-thesaurus-files"></a><a name="location"></a>Speicherort der Thesaurusdateien  
 Der Standardspeicherort der Thesaurusdateien lautet folgendermaßen:  
  
 *<SQL_Server_data_files_path>* \mssql12. mssqlserver\mssql\ftdata\  
  
 Dieser Standardspeicherort enthält die folgenden Dateien:  
  
-   Sprachspezifische Thesaurusdateien  
  
     Beim Setup werden am oben genannten Speicherort leere Thesaurusdateien installiert. Für jede unterstützte Sprache wird eine separate Datei bereitgestellt. Ein Systemadministrator kann diese Dateien anpassen.  
  
     Die Standarddateinamen der Thesaurusdateien haben das folgende Format:  
  
     ' ts ' + \<three-letter language-abbreviation> + '. xml '  
  
     Der Name der Thesaurusdatei für eine bestimmte Sprache ist in der Registrierung im folgenden Wert angegeben: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<Instanzname>\MSSearch\\<Sprachcode>.  
  
-   Die globale Thesaurusdatei  
  
     Eine leere globale Thesaurusdatei mit dem Namen „tsGlobal.xml“.  
  
 Sie können den Speicherort und den Namen einer Thesaurusdatei ändern, indem Sie den zugehörigen Registrierungsschlüssel ändern. Der Speicherort der Thesaurusdatei für jede einzelne Sprache ist im folgenden Wert in der Registrierung angegeben:  
  
 HKLM/Software/Microsoft/Microsoft SQL Server/ \<instance name> /MSSearch/Language/ \<language-abbreviation> /TsaurusFile  
  
 Die globale Thesaurusdatei entspricht der neutralen Sprache mit LCID 0. Dieser Wert kann nur von Administratoren geändert werden.  
  
  
##  <a name="how-queries-use-thesaurus-files"></a><a name="how_queries_use_tf"></a>Verwenden von Thesaurusdateien in Abfragen  
 Für jede Thesaurusabfrage wird zuerst ein sprachspezifischer Thesaurus und dann der globale Thesaurus verwendet. Zuerst wird die sprachspezifische Datei gesucht und (falls erforderlich) zur Verarbeitung geladen. Die Abfrage wird um die durch die Erweiterungssatz- und Ersetzungssatz-Regeln in der Thesaurusdatei angegebenen Synonyme erweitert. Anschließend werden diese Schritte für den globalen Thesaurus wiederholt. Wenn für einen Begriff in der sprachspezifischen Thesaurusdatei bereits eine Übereinstimmung gefunden wurde, werden die globalen Synonyme des Begriffs ignoriert.  
  
  
##  <a name="understanding-the-structure-of-a-thesaurus-file"></a><a name="structure"></a>Grundlegendes zur Struktur einer Thesaurusdatei  
 Jede Thesaurusdatei definiert einen XML-Container, dessen ID `Microsoft Search Thesaurus` lautet, sowie einen Kommentar, `<!--` … `-->`, der einen Beispielthesaurus enthält. Der Thesaurus wird in einem- \<thesaurus> Element definiert, das Beispiele für die untergeordneten Elemente enthält, die die Einstellung für diakritische Zeichen, Erweiterungs Sätze und Ersetzungs Sätze wie folgt definieren:  
  
-   XML-Struktur der Einstellung für diakritische Zeichen  
  
     Die Einstellung eines Thesaurus für diakritische Zeichen wird in einem einzelnen <diacritics_sensitive>-Element angegeben. Dieses Element enthält einen ganzzahligen Wert, der die Unterscheidung nach Akzent folgendermaßen steuert:  
  
    |Einstellung für diakritische Zeichen|Wert|XML|  
    |------------------------|-----------|---------|  
    |keine Unterscheidung nach Akzent|0|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |Unterscheidung nach Akzent|1|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  Diese Einstellung kann nur ein einziges Mal in der Datei vorgenommen werden und gilt für alle Suchmuster in der Datei. Diese Einstellung kann nicht für einzelne Muster angegeben werden.  
  
-   XML-Struktur eines Erweiterungssatzes  
  
     Jeder Erweiterungssatz ist in ein \<expansion>-Element eingeschlossen. Innerhalb dieses Elements geben Sie eine oder mehrere Substitutionen in einem \<sub>-Element an. Im Erweiterungssatz können Sie eine Gruppe von Substitutionen angeben, die Synonyme zueinander sind.  
  
     Sie können beispielsweise den expansion-Abschnitt bearbeiten, um die Substitutionen "writer", "author" und "journalist" als Synonyme zu behandeln. Volltextsuchabfragen, die Übereinstimmungen in einer Substitution enthalten, werden erweitert, um alle weiteren im Erweiterungssatz angegebenen Substitutionen einzubeziehen. Wenn Sie daher im vorherigen Beispiel eine FORMS OF THESAURUS- oder eine FREETEXT-Abfrage nach dem Wort "author" ausführen, gibt die Volltextsuche auch Suchergebnisse zurück, die die Wörter "writer" und "journalist" enthalten.  
  
     Der Erweiterungssatzabschnitt für das oben genannte Beispiel würde wie folgt aussehen:  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   XML-Struktur eines Ersetzungssatzes  
  
     Jeder Ersetzungssatz ist in ein \<replacement>-Element eingeschlossen. Innerhalb dieses Elements können Sie ein oder mehrere Muster in einem \<pat>-Element und keine oder beliebig viele Substitutionen in \<sub>-Elementen (einem pro Synonym) angeben. Sie können ein durch einen Substitutionssatz zu ersetzendes Muster angeben. Muster und Substitutionen können ein Wort oder eine Wortfolge enthalten. Wenn für ein Muster keine Substitution angegeben wird, ist die Wirkung dieselbe, als würde das Muster aus der Benutzerabfrage entfernt.  
  
     Angenommen, Sie möchten, dass Abfragen nach "Win8" (das Muster) durch "Windows Server 2012" oder "Windows 8.0" (die Substitutionen) ersetzt werden. Wenn Sie eine Volltextabfrage nach "Win8" ausführen, gibt die Volltextsuche nur Suchergebnisse zurück, die "Windows Server 2012" oder "Windows 8.0" enthalten. Sie gibt keine Ergebnisse zurück, die "Win8" enthalten. Dies liegt daran, dass das Muster "Win8" durch die Muster "Windows Server 2012" und "Windows 8.0" "ersetzt" wurde.  
  
     Der Ersetzungssatzabschnitt für das oben genannte Beispiel würde wie folgt aussehen:  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     Wenn zwei Ersetzungssätze mit ähnlichen Mustern für die Übereinstimmung verwendet werden, hat der längere der beiden Vorrang. Wenn Sie beispielsweise eine FORMS OF THESAURUS-Abfrage nach "Internet Explorer online community" ausführen und die folgenden Ersetzungssätze haben, hat der "Internet Explorer"-Ersetzungssatz Vorrang vor dem "Internet"-Ersetzungssatz. Die Abfrage wird demzufolge als "IE online community" oder "IE 9 online community" verarbeitet.  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     und  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
  
##  <a name="working-with-thesaurus-files"></a><a name="working_with_thesaurus_files"></a>Arbeiten mit Thesaurusdateien  
 **So bearbeiten Sie eine Thesaurusdatei**  
  
-   [Bearbeiten einer Thesaurusdatei](#editing)  
  
 **So laden Sie eine aktualisierte Thesaurusdatei**  
  
-   [sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql)  
  
 **So zeigen Sie das Tokenisierungsergebnis einer Kombination aus Wörtertrennung, Thesaurus und Stoplisten an**  
  
-   [sys. dm_fts_parser &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="editing-a-thesaurus-file"></a><a name="editing"></a>Bearbeiten einer Thesaurusdatei  
 Der Thesaurus für eine bestimmte Sprache kann durch Bearbeiten der zugehörigen Thesaurusdatei (einer XML-Datei) konfiguriert werden. Beim Setup werden leere Thesaurusdateien installiert, die nur den \<xml> Container und ein auskommentiertes Beispiel \<thesaurus> Element enthalten. Damit voll Text Such Abfragen, bei denen nach Synonymen gesucht wird, ordnungsgemäß funktionieren, müssen Sie ein tatsächliches \<thesaurus> Element erstellen, das eine Gruppe von Synonymen definiert. Sie können zwei Formen von Synonymen definieren, nämlich Erweiterungssätze und Ersetzungssätze.  
  
 **Einschränkungen für Thesaurusdateien**  
  
 Beim Bearbeiten einer Thesaurusdatei gelten die folgenden Einschränkungen:  
  
-   Nur Systemadministratoren können Thesaurusdateien aktualisieren, ändern und löschen.  
  
-   Wenn Sie Thesaurusdateien mithilfe von Text-Editor-Tools bearbeiten, müssen die Dateien im Unicode-Format gespeichert und Bytereihenfolgemarken (Byte Order Marks, BOMs) angegeben werden.  
  
-   Thesauruseinträge dürfen nicht leer sein oder eine Wörtertrennung zu einer leeren Zeichenfolge aufweisen.  
  
-   Ausdrücke in der Thesaurusdatei dürfen aus höchstens 512 Zeichen bestehen.  
  
-   Ein Thesaurus darf in den \<sub>-Einträgen von Erweiterungssätzen und in den \<pat>-Elementen von Ersetzungssätzen keine doppelten Einträge enthalten.  
  
 **Empfehlungen für Thesaurusdateien**  
  
 Einträge in der Thesaurusdatei sollten keine Sonderzeichen enthalten. Dies wird deshalb empfohlen, weil die Wörtertrennung auf Sonderzeichen sehr fein reagiert. Wenn ein Thesauruseintrag Sonderzeichen enthält, kann die Verwendung der Wörtertrennung in Kombination mit diesem Eintrag schwer erkennbare Auswirkungen auf das Verhalten einer Volltextabfrage haben.  
  
 Es wird empfohlen, in \<sub>-Einträgen keine Stoppwörter zu verwenden, da Stoppwörter im Volltextindex ausgelassen werden. Abfragen werden erweitert, um die \<sub>-Einträge in einer Thesaurusdatei einzubeziehen, und wenn ein \<sub>-Eintrag Stoppwörter enthält, nimmt die Abfrage unnötigerweise an Größe zu.  
  
#### <a name="to-edit-a-thesaurus-file"></a>So bearbeiten Sie eine Thesaurusdatei  
  
1.  Öffnen Sie die Thesaurusdatei in Editor.  
  
2.  Wenn Sie die Thesaurusdatei zum ersten Mal bearbeiten, entfernen Sie die folgenden Kommentarzeilen am Anfang bzw. Ende der Datei:  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  Fügen Sie einen Ersetzungs- oder Erweiterungssatz hinzu, ändern oder löschen Sie ihn.  
  
4.  Speichern Sie die Datei, und schließen Sie Editor.  
  
5.  Verwenden Sie [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) , um den Inhalt der Thesaurusdatei in tempdb zu laden, und geben Sie den Gebietsschemabezeichner (LCID) an, der der Sprache der Thesaurusdatei entspricht. So lautet z. B. für die englische Thesaurusdatei "tsenu.xml" der LCID 1033.  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enthält &#40;Transact-SQL-&#41;](/sql/t-sql/queries/contains-transact-sql)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql)   
 [FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql)   
 [Volltextsuche](full-text-search.md)  
  
  
