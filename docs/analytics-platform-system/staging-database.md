---
title: 'Verwenden eine Stagingdatenbank: Parallel Data Warehouse | Microsoft-Dokumentation'
description: SQL Server Parallel Data Warehouse (PDW) verwendet eine Stagingdatenbank, um Daten während des Ladevorgangs vorübergehend zu speichern.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 824ad4dedee0224023f50b6855b2de1e53581304
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960035"
---
# <a name="using-a-staging-database-in-parallel-data-warehouse-pdw"></a>Verwendung einer Stagingdatenbank in Parallel Data Warehouse (PDW)
SQL Server Parallel Data Warehouse (PDW) verwendet eine Stagingdatenbank, um Daten während des Ladevorgangs vorübergehend zu speichern. Standardmäßig verwendet SQL Server PDW die Zieldatenbank als die staging-Datenbank, die Tabellenfragmentierung verursachen kann. Um die Tabellenfragmentierung zu reduzieren, können Sie eine benutzerdefinierte Stagingdatenbank erstellen. Beim Rollback von einem Fehler beim Laden des nicht relevant ist, Sie können auch den Fastappend-Lademodus zur Verbesserung der Leistung durch die temporäre Tabelle überspringen und direkt in die Zieltabelle geladen.  
  
## <a name="StagingDatabase"></a>Grundlagen der Staging-Datenbank  
Ein *Stagingdatenbank* ist eine vom Benutzer erstellte PDW-Datenbank, die Daten speichert vorübergehend, während sie in der Anwendung geladen wird. Wenn eine Stagingdatenbank für ein Auslastungstestergebnis angegeben wird, wird das Gerät kopiert zunächst die Daten in die Stagingdatenbank und kopiert dann die Daten von temporären Tabellen in der staging-Datenbank mit dauerhaften Tabellen in der Zieldatenbank.  
  
Wenn eine Stagingdatenbank für eine Last nicht angegeben ist, wird SQL ServerPDW die temporären Tabellen in der Zieldatenbank erstellt und verwendet sie auf um die geladenen Daten zu speichern, bevor die geladenen Daten in die permanent Ziels Tabellen eingefügt.  
  
Wenn eine Auslastung verwendet die *Fastappend-Modus*, SQL ServerPDW überspringt die Verwendung von temporären Tabellen vollständig und fügt die Daten direkt an die Zieltabelle. Der Fastappend-Modus verbessert die Leistung beim Laden von ELT-Szenarien, in denen Daten in eine Tabelle geladen werden, die die Anwendung macht eine temporäre Tabelle ist. Beispielsweise könnte ein ELT-Prozesses Laden von Daten in eine temporäre Tabelle, Verarbeiten der Daten durch DatenBereinigung und Deduplizierung Informationen und fügen Sie dann die Daten in die Zieltabelle für die Tatsache. In diesem Fall ist es nicht erforderlich für PDW zum ersten Laden der Daten in eine interne temporäre Tabelle vor dem Einfügen der Daten in der Anwendung temporäre Tabelle. Der Fastappend-Modus vermeiden Sie den Schritt für zusätzliche Last, der die Leistung beim Laden wesentlich verbessert. Um den Fastappend-Modus zu verwenden, müssen Sie mit mehreren Transaktionsmodus befindet, verwenden, was bedeutet, dass die Wiederherstellung nach einer fehlerhaften oder abgebrochenen Last durch Ihre eigenen Load-Prozess verarbeitet werden muss.  
  
**Vorteile der Staging-Datenbank**  
  
Der Hauptvorteil einer Stagingdatenbank wird um die Tabellenfragmentierung zu reduzieren. Wenn eine Stagingdatenbank nicht verwendet wird, werden die Daten in temporäre Tabellen in der Zieldatenbank geladen. Wenn Sie temporäre Tabellen erstellt und in der Zieldatenbank gelöscht, werden die Seiten für die temporäre Tabellen und dauerhaften Tabellen verschachtelte. Im Laufe der Zeit Tabellenfragmentierung tritt ein, und beeinträchtigt die Leistung. Im Gegensatz dazu gewährleistet eine Stagingdatenbank, temporäre Tabellen erstellt und in eine separate Datei-Speicherplatz als der dauerhaften Tabellen gelöscht werden.  
  
**Staging-Tabelle Datenbankstrukturen**  
  
Die Speicherstruktur für jede Datenbanktabelle hängt von der Zieltabelle ab.  
  
-   Für das Laden in einen Heap oder gruppierten columnstore-Index ist die staging-Tabelle ein Heap.  
  
-   Für das Laden in einen gruppierten Rowstore-Index ist die staging-Tabelle einen gruppierten Rowstore-Index.  
  
## <a name="Permissions"></a>Berechtigungen  
Erfordert die Berechtigung "erstellen" (zum Erstellen einer temporären Tabelle) für die staging-Datenbank. 

<!-- MISSING LINKS

For more information, see [Grant Permissions to load data](grant-permissions-to-load-data.md).  

-->
  
## <a name="CreatingStagingDatabase"></a>Bewährte Methoden zum Erstellen einer Stagingdatenbank  
  
1.  Es sollte nur eine Stagingdatenbank pro Anwendung vorhanden sein. Die Stagingdatenbank kann alle Lade-Aufträgen für alle Zieldatenbanken freigegeben werden.  
  
2.  Die Größe der Stagingdatenbank wird kundenspezifischen. Zunächst sollte beim ersten Auffüllen die Appliance, die Stagingdatenbank groß genug für die Aufträge der anfängliche Ladevorgang sein. Diese Aufträge laden tendenziell groß sein, da mehrere Lasten gleichzeitig ausgeführt werden können. Nach dem ersten Ladevorgang Aufträge abgeschlossen haben, und das System in der Produktion ist, wird der Größe der einzelnen Ladeauftrag wahrscheinlich kleiner sein. Bei Lasten klein sind, können Sie die Größe der Stagingdatenbank um die Last kleinere gerecht zu reduzieren. Um die Größe zu reduzieren, können Sie die staging-Datenbank löschen und erstellen Sie es erneut mit einer verringerten Zuordnung von Größe, oder Sie können die [ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) Anweisung.  
  
    Wenn Sie die staging-Datenbank zu erstellen, verwenden Sie die folgenden Richtlinien.  
  
    -   Die Größe der replizierten Tabelle sollte sich auf die geschätzte Größe pro Compute-Knoten, der alle replizierten Tabellen aus, die gleichzeitig geladen werden. Die Größe ist in der Regel 25-30 GB.  
  
    -   Die Tabelle mit Größe sollte die geschätzte Größe pro Gerät aller verteilten Tabellen, die gleichzeitig geladen werden.  
  
    -   Die Protokollgröße ähnelt in der Regel die Größe der replizierten Tabelle.  
  
## <a name="Examples"></a>Beispiele für  
  
### <a name="a-create-a-staging-database"></a>A. Erstellen einer Stagingdatenbank 
Das folgende Beispiel erstellt eine Stagingdatenbank, Stagedb, für die Verwendung mit allen Auslastung auf dem Gerät. Angenommen, Sie schätzen, dass die fünf Tabellen Größe repliziert werden 5 GB gleichzeitig geladen werden. Diese Parallelität führt mindestens 25 GB für die Größe der replizierten zuordnen. Angenommen, Sie davon ausgehen, dass sechs Tabellen der Größe 100 verteilt, werden 200, 400, 500, 500 und 550 GB gleichzeitig geladen werden. Diese Parallelität führt mindestens 2 250 GB für die Tabelle mit Größe zuordnen.  
  
```sql  
CREATE DATABASE Stagedb  
WITH (  
  
    AUTOGROW = ON,  
  
    REPLICATED_SIZE = 25 GB,  
  
    DISTRIBUTED_SIZE = 2250 GB,  
  
    LOG_SIZE = 25 GB  
  
);  
```  

<!-- MISSING LINKS
 
## See Also  
[Common metadata query examples](metadata-query-examples.md)  

-->
  
