---
title: Verwenden einer Stagingdatenbank
description: SQL Server parallele Data Warehouse (PDW) verwendet eine Stagingdatenbank, um Daten während des Ladevorgangs temporär zu speichern.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: dcd7f95833695cc5f9f791d83a6221c35e88f58e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400281"
---
# <a name="using-a-staging-database-in-parallel-data-warehouse-pdw"></a>Verwenden einer Stagingdatenbank parallel Data Warehouse (PDW)
SQL Server parallele Data Warehouse (PDW) verwendet eine Stagingdatenbank, um Daten während des Ladevorgangs temporär zu speichern. Standardmäßig verwendet SQL Server PDW die Zieldatenbank als Stagingdatenbank, was eine Tabellen Fragmentierung verursachen kann. Um die Tabellen Fragmentierung zu reduzieren, können Sie eine benutzerdefinierte Stagingdatenbank erstellen. Wenn das Rollback eines Lade Fehlers kein Problem ist, können Sie den vom fastappend Lademodus-Lade Modus verwenden, um die Leistung zu verbessern, indem Sie die temporäre Tabelle überspringen und direkt in die Ziel Tabelle laden.  
  
## <a name="StagingDatabase"></a>Grundlagen zu Staging  
Eine *Stagingdatenbank* ist eine vom Benutzer erstellte PDW-Datenbank, in der Daten temporär gespeichert werden, während Sie in die Appliance geladen werden. Wenn eine Stagingdatenbank für eine Last angegeben wird, kopiert die Appliance zuerst die Daten in die Stagingdatenbank und kopiert dann die Daten aus den temporären Tabellen in der Stagingdatenbank in dauerhafte Tabellen in der Zieldatenbank.  
  
Wenn für eine Last keine Stagingdatenbank angegeben wird, werden die temporären Tabellen in der Zieldatenbank von SQL serverpdw erstellt und zum Speichern der geladenen Daten verwendet, bevor die geladenen Daten in die permanenten Ziel Tabellen eingefügt werden.  
  
Wenn eine Auslastung den *vom fastappend Lademodus-Modus*verwendet, überspringt SQL serverpdw die Verwendung temporärer Tabellen und fügt die Daten direkt an die Ziel Tabelle an. Der vom fastappend Lademodus-Modus verbessert die Ladeleistung für ELT-Szenarien, in denen Daten in eine Tabelle geladen werden, bei der es sich um eine temporäre Tabelle aus der Anwendungsperspektive handelt. Ein ELT-Prozess könnte z. b. Daten in eine temporäre Tabelle laden, die Daten durch bereinigen und debugping verarbeiten und dann die Daten in die Ziel-Fakten Tabelle einfügen. In diesem Fall ist es nicht erforderlich, dass PDW zuerst die Daten in eine interne temporäre Tabelle lädt, bevor die Daten in die temporäre Tabelle der Anwendung eingefügt werden. Der vom fastappend Lademodus-Modus vermeidet den zusätzlichen Lade Schritt, der die Ladeleistung erheblich verbessert. Um den vom fastappend Lademodus-Modus zu verwenden, müssen Sie den Modus für mehrere Transaktionen verwenden. Dies bedeutet, dass die Wiederherstellung von einer fehlerhaften oder abgebrochenen Last durch ihren eigenen Ladevorgang verarbeitet werden muss.  
  
**Vorteile der Stagingdatenbank**  
  
Der Hauptvorteil einer Stagingdatenbank ist die Reduzierung der Tabellen Fragmentierung. Wenn keine Stagingdatenbank verwendet wird, werden die Daten in temporäre Tabellen in der Zieldatenbank geladen. Wenn temporäre Tabellen erstellt und in der Zieldatenbank abgelegt werden, werden die Seiten für die temporären Tabellen und die permanenten Tabellen überlappend. Im Laufe der Zeit erfolgt die Tabellen Fragmentierung, und die Leistung wird beeinträchtigt. Im Gegensatz dazu stellt eine Stagingdatenbank sicher, dass temporäre Tabellen erstellt und in einem separaten Datei Bereich abgelegt werden, als die permanenten Tabellen.  
  
**Staging von Datenbanktabellen-Strukturen**  
  
Die Speicherstruktur für jede Datenbanktabelle hängt von der Ziel Tabelle ab.  
  
-   Für Ladevorgänge in einen Heap oder einen gruppierten columnstore--Index ist die Stagingtabelle ein Heap.  
  
-   Bei Ladevorgängen in einen gruppierten rowstore-Index ist die Stagingtabelle ein gruppierter rowstore-Index.  
  
## <a name="Permissions"></a>Berechtigungen  
Erfordert die CREATE-Berechtigung (zum Erstellen einer temporären Tabelle) für die Stagingdatenbank. 

<!-- MISSING LINKS

For more information, see [Grant Permissions to load data](grant-permissions-to-load-data.md).  

-->
  
## <a name="CreatingStagingDatabase"></a>Bewährte Methoden zum Erstellen einer Stagingdatenbank  
  
1.  Es darf nur eine Stagingdatenbank pro Appliance vorhanden sein. Die Stagingdatenbank kann von allen Lade Aufträgen für alle Ziel Datenbanken gemeinsam genutzt werden.  
  
2.  Die Größe der Stagingdatenbank ist kundenspezifisch. Anfänglich sollte die Stagingdatenbank beim ersten Auffüllen der Appliance groß genug sein, um die anfänglichen Lade Aufträge aufzunehmen. Diese Lade Aufträge sind tendenziell sehr groß, da gleichzeitig mehrere Ladungen auftreten können. Nachdem die anfänglichen Lade Aufträge abgeschlossen sind und sich das System in der Produktion befindet, ist die Größe der einzelnen Lade Aufträge wahrscheinlich kleiner. Wenn die Auslastung gering ist, können Sie die Größe der Stagingdatenbank reduzieren, um die geringeren Lade Größen zu erfüllen. Um die Größe zu verringern, können Sie die Stagingdatenbank löschen und erneut mit geringeren Größen Zuweisungen erstellen, oder Sie können die [ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) -Anweisung verwenden.  
  
    Verwenden Sie beim Erstellen der Stagingdatenbank die folgenden Richtlinien.  
  
    -   Die Größe der replizierten Tabelle sollte der geschätzten Größe (pro Computeknoten) aller replizierten Tabellen sein, die gleichzeitig geladen werden. Die Größe beträgt in der Regel 25-30 GB.  
  
    -   Die Größe der verteilten Tabelle sollte die geschätzte Größe (pro Appliance) aller verteilten Tabellen sein, die gleichzeitig geladen werden.  
  
    -   Die Protokoll Größe ähnelt in der Regel der replizierten Tabellengröße.  
  
## <a name="Examples"></a>Beispiele  
  
### <a name="a-create-a-staging-database"></a>A. Erstellen einer Stagingdatenbank 
Im folgenden Beispiel wird eine Stagingdatenbank, stagedb, für die Verwendung mit allen Ladevorgängen auf dem Gerät erstellt. Angenommen, Sie schätzen, dass fünf replizierte Tabellen mit einer Größe von jeweils 5 GB gleichzeitig geladen werden. Diese Parallelität führt zu einer Zuordnung von mindestens 25 GB für die replizierte Größe. Angenommen, Sie schätzen, dass sechs verteilte Tabellen der Größen 100, 200, 400, 500, 500 und 550 GB gleichzeitig geladen werden. Diese Parallelität führt zu einer Zuordnung von mindestens 2250 GB für die verteilte Tabellengröße.  
  
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
  
