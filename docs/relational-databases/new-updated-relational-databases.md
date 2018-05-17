---
title: Aktualisiert – Dokumentation zu relationalen Datenbanken | Microsoft-Dokumentation
description: Zeigen Sie Codeausschnitte von aktualisierten Inhalten in der zuletzt geänderten Dokumentation zu relationale Datenbanken an.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: relational-databases
ms.date: 04/28/2018
ms.openlocfilehash: a885befe2411a76dc8c68bf2a7b543a838a52877
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Neu und zuletzt aktualisiert: Dokumentation zu relationalen Datenbanken



Beinahe jeden Tag aktualisiert Microsoft einige der vorhandenen Artikel auf der Dokumentationswebsite [Docs.Microsoft.com](http://docs.microsoft.com/). In diesem Artikel werden Auszüge aus den zuletzt aktualisierten Artikeln wiedergegeben. Links zu den neuen Artikel werden ggf. ebenfalls aufgeführt.

Dieser Artikel wurde im Rahmen eines Programms erstellt, das in regelmäßigen Abständen erneut ausgeführt wird. Gelegentlich kann ein Auszug mit falscher Formatierung oder als Markdown aus dem Quellartikel angezeigt werden. Bilder werden hier nie wiedergegeben.

Neueste Updates werden für den folgenden Datumsbereich und Themenbereich gemeldet:



- *Datumsbereich des Updates:* &nbsp; **03.02.2018** &nbsp; bis &nbsp; **28.04.2018**
- *Themenbereich:* &nbsp; **Relationale Datenbanken**




&nbsp;

## <a name="new-articles-created-recently"></a>Neue Artikel, die vor kurzem erstellt wurden

Die folgenden Links leiten Sie zu den neuen Artikeln weiter, die erst kürzlich erstellt wurden.


1. [Joins (SQL Server)](performance/joins.md)
2. [Unterabfragen (SQL Server)](performance/subqueries.md)
3. [Einrichten der Verteilungsdatenbank für die Replikation in einer Always On-Verfügbarkeitsgruppe](replication/configure-distribution-availability-group.md)
4. [SQL-Datenermittlung und -klassifizierung](security/sql-data-discovery-and-classification.md)
5. [Handbuch zu Transaktionssperren und Zeilenversionsverwaltung](sql-server-transaction-locking-and-row-versioning-guide.md)
6. [sys.dm_os_job_object (Azure SQL-Datenbank)](system-dynamic-management-views/sys-dm-os-job-object-transact-sql.md)
7. [Gespeicherte Systemprozeduren für Filestream und FileTable (Transact-SQL)](system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Aktualisierte Artikel mit Auszügen

In diesem Abschnitt werden die Auszüge der Updates aus den Artikeln dargestellt, die vor Kurzem umfassend aktualisiert wurden.

Die Auszüge hier werden getrennt vom richtigen semantischen Kontext angezeigt. Darüber hinaus wird ein Auszug manchmal getrennt von der wichtigen Markdownsyntax wiedergegeben, die ihn im ursprünglichen Artikel umgibt. Aus diesem Grund sind diese Auszüge nur allgemeine Anleitungen. Anhand dieser Auszüge sollen Sie nur entscheiden können, ob Sie sich die Zeit nehmen und den eigentlichen Artikel besuchen möchten.

Kopieren Sie aus diesem und anderen Gründen auf gar keinen Fall Code aus diesen Auszügen, und gehen Sie bei keinem Textauszug von einer 100-prozentigen Richtigkeit der Informationen aus. Besuchen Sie stattdessen den eigentlichen Artikel.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Kompakte Liste der Artikel, die vor Kurzem aktualisiert wurden

Diese kompakte Liste enthält Links zu den aktualisierten Artikeln, die im Abschnitt Auszüge aufgeführt sind.

1. [Überspringen einer Tabellenspalte mithilfe einer Formatdatei (SQL Server)](#TitleNum_1)
2. [JSON-Daten in SQL Server](#TitleNum_2)
3. [Handbuch zur Architektur der Abfrageverarbeitung](#TitleNum_3)
4. [Tutorial: Prepare SQL Server For Replication - Publisher, Distributor, Subscriber (Tutorial: Vorbereiten von SQL Server auf die Replikation (Verleger, Verteiler und Abonnent))](#TitleNum_4)
5. [Tutorial: Konfigurieren der Replikation zwischen zwei Servern mit kontinuierlicher Verbindung (transaktional)](#TitleNum_5)
6. [Tutorial: Konfigurieren der Replikation zwischen einem Server und mobilen Clients (Mergereplikation)](#TitleNum_6)
7. [Abfragen mit Volltextsuche](#TitleNum_7)
8. [Transparent Data Encryption mit Bring Your Own Key-Unterstützung für Azure SQL-Datenbank und Data Warehouse](#TitleNum_8)
9. [PowerShell und CLI: Aktivieren von Transparent Data Encryption mithilfe eines eigenen Azure Key Vault-Schlüssels](#TitleNum_9)
10. [Über Change Data Capture (SQL Server)](#TitleNum_10)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-use-a-format-file-to-skip-a-table-column-sql-serverimport-exportuse-a-format-file-to-skip-a-table-column-sql-servermd"></a>1. &nbsp; [Überspringen einer Tabellenspalte mithilfe einer Formatdatei (SQL Server)](import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)

*Aktualisiert: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Weiter](#TitleNum_2))

<!-- Source markdown line 221.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 167916d79c5de1e7f13990cb7acc41ceb541b9a7 cb92eb201292294e3397879c98f353fba45f1c1c  (PR=0  ,  Filename=use-a-format-file-to-skip-a-table-column-sql-server.md  ,  Dirpath=docs\relational-databases\import-export\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Verwenden von OPENROWSET(BULK...)**


Um eine XML-Formatdatei zu verwenden, die unter Verwendung von `OPENROWSET(BULK...)` eine Tabellenspalte überspringt, muss eine explizite Liste von Spalten in der Auswahlliste und in der Zieltabelle angegeben werden:

```
    INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)
```

Im folgenden Beispiel werden der Massenrowsetanbieter `OPENROWSET` und die Formatdatei `myTestSkipCol2.xml` verwendet. Die Datendatei `myTestSkipCol2.dat` wird per Massenimport in die `myTestSkipCol` -Tabelle übertragen. Die Anweisung enthält anforderungsgemäß eine explizite Liste der Spalten in der Auswahlliste und in der Zieltabelle.

Führen Sie den folgenden Code in SSMS aus: Aktualisieren Sie die Dateisystempfade für den Speicherort der Beispieldateien auf Ihrem Computer.

```
USE WideWorldImporters;
GO
INSERT INTO myTestSkipCol
  (Col1,Col3)
    SELECT Col1,Col3
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',
      FORMATFILE='C:\myTestSkipCol2.Xml'
       ) as t1 ;
GO
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-json-data-in-sql-serverjsonjson-data-sql-servermd"></a>2. &nbsp; [JSON-Daten in SQL Server](json/json-data-sql-server.md)

*Aktualisiert: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Vorheriger](#TitleNum_1) | [Nächster](#TitleNum_3))

<!-- Source markdown line 145.  ms.author= "jovanpop".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 19e276637a463b412f2c29a84f9fb7d0b0f5fcc5 e2f2e8b4732779b3f24561cc0c4da3a958f4edbb  (PR=0  ,  Filename=json-data-sql-server.md  ,  Dirpath=docs\relational-databases\json\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



JSON-Dokumente enthalten möglicherweise untergeordnete Elemente und hierarchische Daten, die relationalen Standardspalten nicht direkt zugeordnet werden können. Sie können in diesem Fall die JSON-Hierarchie vereinfachen, indem Sie die übergeordnete Entität mit untergeordneten Arrays verknüpfen.

Im folgenden Beispiel weist das zweite Objekt des Arrays untergeordnete Arrays auf, die Fähigkeiten von Personen darstellen (Skills-Array). Jedes untergeordnete Objekt kann mithilfe des zusätzlichen Funktionsaufrufs `OPENJSON` analysiert werden:

```
DECLARE @json NVARCHAR(MAX)
SET @json =
N'[
       { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },
       { "id" : 5,"info": { "name": "Jane", "surname": "Smith", "skills": ["SQL", "C#", "Azure"] }, "dob": "2005-11-04T12:00:00" }
 ]'

SELECT *
FROM OPENJSON(@json)
  WITH (id int 'strict $.id',
        firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',
        age int, dateOfBirth datetime2 '$.dob',
    skills nvarchar(max) '$.skills' as json)
    outer apply openjson( a.skills )
                     with ( skill nvarchar(8) '$' ) as b
```
Das **Skills**-Array wird im ersten `OPENJSON`-Element als das ursprüngliche JSON-Textfragment angegeben und mithilfe des `APPLY`-Operators an eine andere `OPENJSON`-Funktion übergeben. Die zweite `OPENJSON`-Funktion analysiert das JSON-Array und gibt Zeichenfolgenwerte als Rowsets mit nur einer Spalte zurück, die mit dem Ergebnis des ersten `OPENJSON`-Elements verknüpft werden.
Das Ergebnis dieser Abfrage wird in der folgenden Tabelle dargestellt:

**Ergebnisse**

|id|firstName|lastName|age|dateOfBirth|skill|
|--------|---------------|--------------|---------|-----------------|----------|
|2|John|Smith|25|||
|5|Jane|Smith||2005-11-04T12:00:00|SQL|
|5|Jane|Smith||2005-11-04T12:00:00|C#|
|5|Jane|Smith||2005-11-04T12:00:00|Azure|

`OUTER APPLY OPENJSON` verknüpft die Entität auf der ersten Ebene mit dem untergeordneten Array und gibt ein vereinfachtes Resultset zurück. Aufgrund der JOIN-Methode wird die zweite Zeile für jedes Skill-Array wiederholt.




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-query-processing-architecture-guidequery-processing-architecture-guidemd"></a>3. &nbsp; [Leitfaden zur Architektur der Abfrageverarbeitung](query-processing-architecture-guide.md)

*Aktualisiert: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Vorheriger](#TitleNum_2) | [Nächster](#TitleNum_4))

<!-- Source markdown line 34.  ms.author= "jroth".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 96d91b39acdb2f32aaff323e374e92d6f229d241 2c1d2f8585632ada174388399782dc3ed2721dba  (PR=0  ,  Filename=query-processing-architecture-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Rangfolge logischer Operatoren**


Wenn mehr als ein logischer Operator in einer Anweisung verwendet wird, wird `NOT` zuerst ausgewertet, dann `AND` und schließlich `OR`. Arithmetische (und bitweise) Operatoren werden vor logischen Operatoren verarbeitet. Weitere Informationen finden Sie unter „Operator Precedence“ (Operatorrangfolge).

Im folgenden Beispiel ist die Color-Bedingung nur für ProductModel 21 anwendbar und nicht für ProductModel 20, weil `AND` Vorrang gegenüber `OR` hat.

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE ProductModelID = 20 OR ProductModelID = 21
  AND Color = 'Red';
GO
```

Sie können die Bedeutung der Abfrage ändern, indem Sie durch Hinzufügen von Klammern veranlassen, dass der Operator `OR` zuerst ausgewertet wird. Die folgende Abfrage findet nur Produkte unter den Modellen 20 und 21, deren Farbe „red“ (rot) ist.

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE (ProductModelID = 20 OR ProductModelID = 21)
  AND Color = 'Red';
GO
```

Die Verwendung von Klammern kann auch dann empfehlenswert sein, wenn diese nicht unbedingt erforderlich sind, da sie die Übersichtlichkeit von Abfragen verbessern und zudem die Wahrscheinlichkeit von Flüchtigkeitsfehlern verringern, die sich aus der Rangfolge der Operatorenauswertung ergeben. Die Leistung wird durch den Einsatz von Klammern nicht wesentlich beeinträchtigt. Das folgende Beispiel ist leichter zu lesen als das ursprüngliche Beispiel, obwohl sie syntaktisch übereinstimmen:

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE ProductModelID = 20 OR (ProductModelID = 21
  AND Color = 'Red');
GO
```




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-tutorial-prepare-sql-server-for-replication---publisher-distributor-subscriberreplicationtutorial-preparing-the-server-for-replicationmd"></a>4. &nbsp; [Tutorial: Vorbereiten von SQL Server auf die Replikation (Verleger, Verteiler und Abonnent)](replication/tutorial-preparing-the-server-for-replication.md)

*Aktualisiert: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Vorheriger](#TitleNum_3) | [Nächster](#TitleNum_5))

<!-- Source markdown line 56.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6e5caedacff193ce79bdd98708ae1b9dc91f0a8f 9f7af4d3f8b1cffd048db2a5b29fc9e6013f5ed2  (PR=0  ,  Filename=tutorial-preparing-the-server-for-replication.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



- Installieren Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installieren Sie die [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Laden Sie eine [AdventureWorks-Beispieldatenbank](https://github.com/Microsoft/sql-server-samples/releases) herunter. Weitere Informationen zum Wiederherstellen einer Datenbank in SSMS finden Sie unter [Wiederherstellen einer Datenbank](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).

>[!NOTE]
> - Die Replikation wird für SQL Server-Versionen, zwischen denen mehr als zwei Versionen liegen, nicht unterstützt. Weitere Informationen finden Sie unter [In der Replikationstopologie unterstützte SQL-Versionen](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/).
> - In *{hier stehen die eingeschlossenen Inhalte}* muss eine Verbindung mit dem Verleger und dem Abonnenten hergestellt werden. Dazu wird ein Anmeldename verwendet, der Mitglied der festen Serverrolle **sysadmin** ist. Weitere Informationen zur Rolle „sysadmin“ finden Sie unter [Rollen auf Serverebene](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/server-level-roles).


**Geschätzte Dauer: 30 Minuten**

**Erstellen von Windows-Konten für die Replikation**

In diesem Abschnitt erstellen Sie Windows-Konten zum Ausführen von Replikations-Agents. Sie erstellen für die folgenden Agents ein separates Windows-Konto auf dem lokalen Server:

|Agent|Speicherort|Kontoname|
|---------|------------|----------------|
|Momentaufnahme-Agent|Verleger|<*machine_name*>\repl_snapshot|



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-tutorial-configure-replication-between-two-fully-connected-servers-transactionalreplicationtutorial-replicating-data-between-continuously-connected-serversmd"></a>5. &nbsp; [Tutorial: Konfigurieren der Replikation zwischen zwei Servern mit kontinuierlicher Verbindung (transaktional)](replication/tutorial-replicating-data-between-continuously-connected-servers.md)

*Aktualisiert: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Vorheriger](#TitleNum_4) | [Nächster](#TitleNum_6))

<!-- Source markdown line 162.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0d74f984d0ffc01cce0376837e6d94df3c5654d7 4ecf4d724286130927dd43687d6845059af6f9b7  (PR=0  ,  Filename=tutorial-replicating-data-between-continuously-connected-servers.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Erstellen eines Abonnements für die Transaktionsveröffentlichung**

In diesem Abschnitt erfahren Sie, wie Sie einen Abonnenten zu der zuvor erstellten Veröffentlichung hinzufügen. In diesem Tutorial wird ein Remote-Abonnent (NODE2\SQL2016) verwendet, ein Abonnement kann jedoch auch lokal zum Verleger hinzugefügt werden.

**So erstellen Sie das Abonnement**


1.  Stellen Sie in *{hier stehen die eingeschlossenen Inhalte}* eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten und den Ordner **Replikation**.

2.  Klicken Sie im Ordner **Lokale Veröffentlichungen** mit der rechten Maustaste auf die Veröffentlichung **AdvWorksProductTrans**, und wählen Sie anschließend **Neue Abonnements** aus.  Der Assistent für neue Abonnements wird gestartet:

    Neues Abonnement

3.  Wählen Sie auf der Seite „Veröffentlichung“ die Veröffentlichung **AdvWorksProductTrans** und anschließend **Weiter** aus:

    Tran.-Verleger auswählen

4.  Wählen Sie auf der Seite „Speicherort des Verteilungs-Agents“ die Option **Alle Agents auf dem Verteiler ausführen** und anschließend **Weiter** aus.  Weitere Informationen zu Push- und Pullabonnements finden Sie unter [Abonnieren von Veröffentlichungen](https://docs.microsoft.com/sql/relational-databases/replication/subscribe-to-publications):

    Agents auf dem Verteiler ausführen

5.  Wählen Sie auf der Seite „Abonnenten“ die Option **Abonnent hinzufügen** und anschließend in der Dropdownliste **SQL Server-Abonnent hinzufügen** aus, wenn der Name der Abonnenteninstanz nicht angezeigt wird. Dadurch wird das Dialogfeld **Mit Server verbinden** angezeigt. Geben Sie den Namen der Abonnenteninstanz ein, und wählen Sie anschließend **Verbinden** aus.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-tutorial-configure-replication-between-a-server-and-mobile-clients-mergereplicationtutorial-replicating-data-with-mobile-clientsmd"></a>6. &nbsp; [Tutorial: Konfigurieren der Replikation zwischen einem Server und mobilen Clients (Mergereplikation)](replication/tutorial-replicating-data-with-mobile-clients.md)

*Aktualisiert: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Vorheriger](#TitleNum_5) | [Nächster](#TitleNum_7))

<!-- Source markdown line 93.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0eed78dfe83c88358c030539a2b25d11ef5ec2d3 79b2a3f32c940fede94b11ad2a3ef8a00b911a39  (PR=0  ,  Filename=tutorial-replicating-data-with-mobile-clients.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



Die Employee-Tabelle enthält eine OrganizationNode-Spalte vom Datentyp hierarchyid, die nur für die Replikation in SQL 2017 unterstützt wird. Wenn Sie einen Build verwenden, der niedriger als SQL 2017 ist, wird unten auf dem Bildschirm eine Meldung angezeigt, in der Sie darüber informiert werden, dass möglicherweise Daten verloren gehen können, wenn Sie diese Spalte in einer bidirektionalen Replikation verwenden. Diese Meldung kann für dieses Tutorial ignoriert werden. Trotzdem sollte dieser Datentyp nur in einer Produktionsumgebung repliziert werden, wenn Sie den unterstützten Build verwenden. Weitere Informationen zum Replizieren des hierarchyid-Datentyps finden Sie unter [Verwenden von hierarchyid-Spalten in replizierten Tabellen](https://docs.microsoft.com/sql/t-sql/data-types/hierarchyid-data-type-method-reference#using-hierarchyid-columns-in-replicated-tables).


-  Klicken Sie auf der Seite „Tabellenzeilen filtern“ auf **Hinzufügen**, und klicken Sie anschließend auf **Filter hinzufügen**.

-  Klicken Sie im Dialogfeld **Filter hinzufügen** auf **Employee (HumanResources)** unter **Wählen Sie die zu filternde Tabelle aus**. Klicken Sie erst auf die Spalte **LoginID** und dann auf den Pfeil nach rechts, um der WHERE-Klausel der Filterabfrage die Spalte hinzuzufügen, und ändern Sie die WHERE-Klausel wie folgt:

    ```
    WHERE [LoginID] = HOST_NAME()
    ```

    A. Klicken Sie erst auf **Eine Zeile aus dieser Tabelle wird nur an ein Abonnement gesendet** und anschließend auf **OK**:

    Hinzufügen eines Filters



- Klicken Sie erst auf der Seite **Tabellenzeilen filtern** auf **Employee (Human Resources)** (Mitarbeiter (Personalabteilung)), dann auf **Hinzufügen** und anschließend auf **Add Join to Extend the Selected Filter** (Join hinzufügen, um den ausgewählten Filter zu erweitern).

    A. Wählen Sie im Dialogfeld **Join hinzufügen** unter **Verknüpfte Tabelle** den Eintrag **Sales.SalesOrderDetail** aus. Klicken Sie auf **Write the join statement manually** (Joinanweisung manuell schreiben), und schließen Sie den Vorgang wie folgt ab:



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-query-with-full-text-searchsearchquery-with-full-text-searchmd"></a>7. &nbsp; [Abfragen mit Volltextsuche](search/query-with-full-text-search.md)

*Aktualisiert: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Vorheriger](#TitleNum_6) | [Nächster](#TitleNum_8))

<!-- Source markdown line 247.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5ec67b56aa0a6eadadbcfa8b73b6726e75eca2bb 4eb108b202d3dd035a312bac7872cf02bcf31cfa  (PR=0  ,  Filename=query-with-full-text-search.md  ,  Dirpath=docs\relational-databases\search\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Weitere Informationen zu Generierungsbegriffsuchen**


Bei den *Flexionsformen* handelt es sich um die verschiedenen Tempora und Konjugationen eines Verbs oder die Singular- und Pluralformen eines Substantivs.

Suchen Sie z.B. nach der Flexionsform des Worts „drive“. Wenn mehrere Zeilen in der Tabelle die Wörter „drive“, „drives“, „drove“, „driving“ und „driven“ enthalten, werden alle in das Resultset aufgenommen, da jedes dieser Wörter durch Flexion aus dem Wort „drive“ generiert werden kann.

[FREETEXT] und [FREETEXTTABLE] suchen standardmäßig nach den Flexionsformen aller angegebenen Wörter. [CONTAINS] und [CONTAINSTABLE] unterstützen ein optionales `INFLECTIONAL`-Argument.

**Suche nach Synonymen eines bestimmten Worts**


Ein *Thesaurus* definiert vom Benutzer angegebene Synonyme für Ausdrücke. Weitere Informationen zu Thesaurusdateien finden Sie unter [Konfigurieren und Verwalten von Thesaurusdateien für die Volltextsuche].

Wird einem Thesaurus beispielsweise ein Eintrag „{car, automobile, truck, van}“ hinzugefügt, können Sie nach der Thesaurusform des Worts „car“ suchen. Alle Zeilen in der abgefragten Tabelle, die die Wörter „automobile“, „truck“, „van“ oder „car“ enthalten, werden im Resultset angezeigt, weil jedes dieser Wörter zum Synonymerweiterungssatz gehört, der das Wort „car“ enthält.

[FREETEXT] und [FREETEXTTABLE] verwenden standardmäßig den Thesaurus. [CONTAINS] und [CONTAINSTABLE] unterstützen ein optionales `THESAURUS`-Argument.



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-transparent-data-encryption-with-bring-your-own-key-support-for-azure-sql-database-and-data-warehousesecurityencryptiontransparent-data-encryption-byok-azure-sqlmd"></a>8. &nbsp; [Transparent Data Encryption mit Bring Your Own Key-Unterstützung für Azure SQL-Datenbank und Data Warehouse](security/encryption/transparent-data-encryption-byok-azure-sql.md)

*Aktualisiert: 24.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Vorheriger](#TitleNum_7) | [Nächster](#TitleNum_9))

<!-- Source markdown line 110.  ms.author= "aliceku".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9527658848d430bf0148be84474a75b232cbd112 70ed2a129c580962384f808e8526673957f00d2c  (PR=5662  ,  Filename=transparent-data-encryption-byok-azure-sql.md  ,  Dirpath=docs\relational-databases\security\encryption\  ,  MergeCommitSha40=91a9c812739a1c9a6ec9e7b8cda71ee1f5adae3d) -->



**Vorgehensweise: Konfigurieren von Georedundanzen mit Azure Key Vault**


Es ist erforderlich, redundante Azure Key Vaults anhand der vorhandenen oder gewünschten SQL-Datenbank-Failovergruppen oder der aktiven Georedundanzinstanzen zu konfigurieren, um die Hochverfügbarkeit der TDE Protectors für verschlüsselte Datenbanken zu erhalten.  Jeder georeplizierte Server erfordert einen separaten Schlüsseltresor, der sich in derselben Azure-Region wie der Server befinden muss. Wenn es in einer Region zu einem Ausfall kommen sollte, nach dem nicht mehr auf die primäre Datenbank zugegriffen werden kann und ein Failover ausgelöst wird, kann die sekundäre Datenbank einspringen und den sekundären Schlüsseltresor verwenden.

Für georeplizierte Azure SQL-Datenbanken ist die folgende Konfiguration von Azure Key Vault erforderlich:
- Eine primäre Datenbank mit einem Schlüsseltresor in der Region und eine sekundäre Datenbank mit einem Schlüsseltresor in der Region.
- Mindestens eine sekundäre Datenbank ist erforderlich, es werden bis zu vier sekundäre Datenbanken unterstützt.
- Sekundäre Datenbanken von sekundären Datenbanken (Verkettung) werden nicht unterstützt.

Im folgenden Abschnitt werden die Schritte für die Einrichtung und Konfiguration im Detail besprochen.

**Konfigurationsschritte für Azure Key Vault**


- Installieren Sie [PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps?view=azurermps-5.6.0)
- Erstellen Sie zwei Azure-Schlüsseltresore in zwei verschiedenen Regionen, und verwenden Sie [PowerShell zum Aktivieren der Eigenschaft „vorläufiges Löschen“](https://docs.microsoft.com/azure/key-vault/key-vault-soft-delete-powershell) in den Schlüsseltresoren (diese Option ist noch nicht im AKV-Portal verfügbar – wird aber von SQL gefordert).
- Beide Azure-Schlüsseltresore müssen sich in Regionen befinden, die in derselben Azure-Geografie verfügbar sind, damit Schlüssel gesichert und wiederhergestellt werden können.  Wenn zwei Schlüsseltresore in unterschiedlichen Geografien die georedundanten SQL-Anforderungen erfüllen müssen, führen Sie den [BYOK-Prozess](https://docs.microsoft.com/azure/key-vault/key-vault-hsm-protected-keys) durch, der das Importieren eines Schlüssels von einem lokalen HSM ermöglicht.



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-powershell-and-cli-enable-transparent-data-encryption-using-your-own-key-from-azure-key-vaultsecurityencryptiontransparent-data-encryption-byok-azure-sql-configuremd"></a>9. &nbsp; [PowerShell und CLI: Aktivieren von Transparent Data Encryption mithilfe eines eigenen Azure Key Vault-Schlüssels](security/encryption/transparent-data-encryption-byok-azure-sql-configure.md)

*Aktualisiert: 24.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Vorheriger](#TitleNum_8) | [Nächster](#TitleNum_10))

<!-- Source markdown line 196.  ms.author= "aliceku".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a0e00f5701d9a493f503a477c69097ce65aba174 721e8fb856a55ee1e8e9e7fc06036a03adab647b  (PR=5662  ,  Filename=transparent-data-encryption-byok-azure-sql-configure.md  ,  Dirpath=docs\relational-databases\security\encryption\  ,  MergeCommitSha40=91a9c812739a1c9a6ec9e7b8cda71ee1f5adae3d) -->



**Erforderliche Komponenten für die CLI**


- Sie müssen über ein Azure-Abonnement verfügen und Administrator für dieses Abonnement sein.
- [Empfohlen aber optional] Sie sollten ein Hardwaresicherheitsmodul (HSM) oder einen lokalen Schlüsselspeicher zum Erstellen einer lokalen Kopie des Schlüsselmaterials für den TDE-Schutz besitzen.
- CLI 2.0 oder höhere Version. Wie Sie die neueste Version installieren und eine Verbindung mit Ihrem Azure-Abonnement herstellen, können Sie unter [Installieren und Konfigurieren der plattformübergreifenden Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) nachlesen.
- Sie müssen einen Azure Key Vault-Schlüsseltresor und einen Schlüssel für die Verwendung für TDE erstellen.
   - [Manage Key Vault using CLI 2.0 (Verwalten von Key Vault mithilfe der CLI 2.0)](https://docs.microsoft.com/azure/key-vault/key-vault-manage-with-cli2)
   - [Instructions for using a hardware security module (HSM) and Key Vault (Anweisungen zur Verwendung eines Hardwaresicherheitsmodells (HSM) und Key Vault)](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
 - Der Schlüsseltresor muss über folgende Eigenschaft verfügen, um für TDE verwendet werden zu können:
   - [Vorläufiges Löschen](https://docs.microsoft.com/azure/key-vault/key-vault-ovw-soft-delete)
   - [Verwenden des vorläufigen Löschens in Key Vault mit CLI](https://docs.microsoft.com/azure/key-vault/key-vault-soft-delete-cli)
- Der Schlüssel muss über folgende Attribute verfügen, um für TDE verwendet werden zu können:
   - Kein Ablaufdatum
   - Nicht deaktiviert
   - Muss die Operationen *get*, *wrap key* und *unwrap key* ausführen können

**Schritt: Erstellen eines Servers und Zuweisen einer Azure AD-Identität zum Server**

      cli
      # create server (with identity) and database



&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-about-change-data-capture-sql-servertrack-changesabout-change-data-capture-sql-servermd"></a>10. &nbsp; [Über Change Data Capture (SQL Server)](track-changes/about-change-data-capture-sql-server.md)

*Aktualisiert: 17.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Zurück](#TitleNum_9))

<!-- Source markdown line 112.  ms.author= "jroth".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 588bff652adefd719e799e9777a416b70184c5f8 77ebdbb1b98b24054d5c5afbb3f1d40e94d1e6bc  (PR=5574  ,  Filename=about-change-data-capture-sql-server.md  ,  Dirpath=docs\relational-databases\track-changes\  ,  MergeCommitSha40=bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68) -->



**Arbeiten mit Datenbanken und Tabellen bei unterschiedlicher Sortierung**


Sie sollten wissen, was zu beachten ist, wenn eine Datenbank und die Spalten einer Tabelle, die für Change Data Capture (CDC) konfiguriert sind, in unterschiedlicher Reihenfolge sortiert sind. CDC verwendet einen Zwischenspeicher, um Tabellen aufzufüllen. Wenn in einer Tabelle CHAR- oder VARCHAR-Spalten enthalten sind, deren Sortierung von der Datenbanksortierung abweicht, und wenn in diesen Spalten Zeichen enthalten sind, bei denen es sich nicht um ASCII-Zeichen handelt (z.B. Doppelbyte-Zeichensätze), kann CDC möglicherweise die geänderten Daten nicht speichern, damit diese mit den Daten in der Basistabelle übereinstimmen. Dies ist darauf zurückzuführen, dass den Zwischenspeichervariablen keine Sortierungen zugeordnet werden können.

Ziehen Sie einen der folgenden Ansätze in Betracht, um sicherzustellen, dass CDC-Daten mit den Daten in der Basistabelle übereinstimmen:

- Verwenden Sie die Datentypen NCHAR oder NVARCHAR für Spalten, die Daten enthalten, bei denen es sich nicht um ASCII-Daten handelt.

- Stattdessen können Sie auch die Spalten und die Datenbank in derselben Reihenfolge sortieren.

Wenn Sie z.B. über eine Datenbank verfügen, die eine SQL_Latin1_General_CP1_CI_AS-Sortierung verwendet, beachten Sie die folgende Tabelle:

```
CREATE TABLE T1(
     C1 INT PRIMARY KEY,
     C2 VARCHAR(10) collate Chinese_PRC_CI_AI)
```

CDC kann möglicherweise die Binärdaten für die Spalte C2 nicht speichern, da deren Sortierung von dieser Sortierung abweicht (Chinese_PRC_CI_AI). Verwenden Sie NVARCHAR, um dieses Problem zu vermeiden:

```
CREATE TABLE T1(
     C1 INT PRIMARY KEY,
     C2 NVARCHAR(10) collate Chinese_PRC_CI_AI --Unicode data type, CDC works well with this data type)
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Ähnliche Artikel zu neuen oder aktualisierten Artikeln

Dieser Abschnitt enthält sehr ähnliche Artikel für zuletzt aktualisierte Artikel in anderen Themenbereichen innerhalb des gleichen GitHub-Repositorys: [MicrosoftDocs/sql-docs-pr](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Themenbereiche, die *über* neue oder kürzlich aktualisierte Artikel verfügen

- [Neu und aktualisiert (11+6):&nbsp; Dokumente zu &nbsp;**Advanced Analytics für SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Neu und aktualisiert (18+0):&nbsp; Dokumente zu &nbsp;**Analysis Services für SQL**](../analysis-services/new-updated-analysis-services.md)
- [Neu und aktualisiert (218+14):**Dokumente zum**Herstellen einer Verbindung mit SQL](../connect/new-updated-connect.md)
- [Neu und aktualisiert (14+0):&nbsp; Dokumente zur &nbsp;**Datenbank-Engine für SQL**](../database-engine/new-updated-database-engine.md)
- [Neu und aktualisiert (3+2):&nbsp; Dokumente zu &nbsp;**Integration Services für SQL**](../integration-services/new-updated-integration-services.md)
- [Neu und aktualisiert (3+3):&nbsp; Dokumente zu &nbsp;**Linux für SQL**](../linux/new-updated-linux.md)
- [Neu und aktualisiert (7+10):&nbsp; Dokumente zu &nbsp;**relationalen Datenbanken für SQL**](../relational-databases/new-updated-relational-databases.md)
- [Neu und aktualisiert (0+2):&nbsp; Dokumente zu &nbsp;**Reporting Services für SQL**](../reporting-services/new-updated-reporting-services.md)
- [Neu und aktualisiert (1+3):&nbsp; Dokumente zu &nbsp;**SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Neu und aktualisiert (2+3):&nbsp; Dokumente zu &nbsp;**Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Neu und aktualisiert (1+1):&nbsp; Dokumente zu &nbsp;**SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Neu und aktualisiert (5+2):&nbsp; Dokumente zu &nbsp;**SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Neu und aktualisiert (0+2):&nbsp; Dokumente zu &nbsp;**Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Neu + Aktualisiert (1+1):&nbsp; Dokumente zu &nbsp;**Tools für SQL**](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Themenbereiche, die *nicht* über neue oder kürzlich aktualisierte Artikel verfügen

- [Neu und aktualisiert (0+0): Dokumente zum **Analytics Platform System für SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [New + Updated (0+0): **Data Quality Services for SQL** docs (Neu + Aktualisiert (0+0): Data Quality Services für SQL-Dokumente)](../data-quality-services/new-updated-data-quality-services.md)
- [New + Updated (0+0): **Data Mining Extensions (DMX) for SQL** docs (Neu + Aktualisiert (0+0): Data Mining-Erweiterungen (DMX) für SQL)](../dmx/new-updated-dmx.md)
- [New + Updated (0+0): **Master Data Services (MDS) for SQL** docs (Neu + Aktualisiert (0+0): Dokumentation zu Master Data Services (MDS) für SQL)](../master-data-services/new-updated-master-data-services.md)
- [New + Updated (0+0): **Multidimensional Expressions (MDX) for SQL** docs (Neu + Aktualisiert (0+0): Mehrdimensionale Ausdrücke für SQL)](../mdx/new-updated-mdx.md)
- [New + Updated (0+0): **ODBC (Open Database Connectivity) for SQL** docs (Neu + Aktualisiert (0+0): Open Database Connectivity für SQL-Dokumente)](../odbc/new-updated-odbc.md)
- [New + Updated (0+0): **PowerShell for SQL** docs (Neu + Aktualisiert (0+0): PowerShell für SQL-Dokumente)](../powershell/new-updated-powershell.md)
- [New + Updated (0+0): **Samples for SQL** docs (Neu + Aktualisiert (0+0): Beispiele für SQL-Dokumente)](../samples/new-updated-samples.md)
- [New + Updated (0+0): **SQL Server Migration Assistant (SSMA)** docs (Neu + Aktualisiert (0+0): SQL Server Migration Assistant-Dokumente (SSMA))](../ssma/new-updated-ssma.md)
- [New + Updated (0+0): **XQuery for SQL** docs (Neu + Aktualisiert (0+0): XQuery für SQL-Dokumente)](../xquery/new-updated-xquery.md)

