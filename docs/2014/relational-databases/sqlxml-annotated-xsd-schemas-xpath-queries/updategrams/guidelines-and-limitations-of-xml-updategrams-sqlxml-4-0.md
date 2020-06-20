---
title: Richtlinien und Einschränkungen von XML-Update grams (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e28f4258aef27403c107158dd13efe5ada02c03
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84996240"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Richtlinien und Einschränkungen von XML-Updategrams (SQLXML 4.0)
  Wenn Sie XML-Updategrams verwenden, sind folgende Überlegungen zu berücksichtigen:  
  
-   Wenn Sie ein Update Gram für einen Einfügevorgang mit nur einem Paar von **\<before>** -und- **\<after>** Blöcken verwenden, **\<before>** kann der-Block ausgelassen werden. Umgekehrt kann der-Block im Falle eines Löschvorgangs **\<after>** ausgelassen werden.  
  
-   Wenn Sie ein Update Gram mit mehreren **\<before>** -und- **\<after>** Blöcken im- **\<sync>** Tag verwenden, müssen sowohl-Blöcke als auch- **\<before>** **\<after>** Blöcke angegeben werden, um **\<before>** -und-Paare zu bilden **\<after>** .  
  
-   Die Updates in einem Updategram werden auf die XML-Sicht angewendet, die vom XML-Schema bereitgestellt wird. Daher müssen Sie für eine erfolgreiche Standardzuordnung den Schemadateinamen im Updategram angeben. Falls der Dateiname nicht bereitgestellt wird, müssen die Element- und Attributnamen mit den Tabellen- und Spaltennamen in der Datenbank übereinstimmen.  
  
-   SQLXML 4.0 setzt voraus, dass alle Spaltenwerte in einem Updategram ausdrücklich im bereitgestellten Schema (XDR oder XSD) zugeordnet werden, um die XML-Sicht für die untergeordneten Elemente zu erstellen. Dieses Verhalten unterscheidet sich von früheren Versionen von SQLXML, die es zuließen, dass ein Wert für eine Spalte nicht im Schema zugeordnet war, wenn er als Teil eines Fremdschlüssels in einer `sql:relationship`-Anmerkung impliziert wurde. (Beachten Sie, dass sich diese Änderung nicht auf die Propagierung von Primärschlüsselwerten an untergeordnete Elemente auswirkt, was immer noch für SQLXML 4.0 gilt, wenn für das untergeordnete Element kein Wert ausdrücklich angegeben wird.)  
  
-   Wenn Sie ein Update Gram zum Ändern von Daten in einer binären Spalte (z. b. dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` Datentyp) verwenden, müssen Sie ein Zuordnungsschema bereitstellen, in dem der Datentyp (z. b. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `sql:datatype="image"` ) und der XML-Datentyp (z. b. `dt:type="binhex"` oder `dt:type="binbase64` ) angegeben werden müssen. Die Daten für die binäre Spalte müssen im Updategram angegeben werden. Die `sql:url-encode`-Anmerkung, die im Zuordnungsschema angegeben wird, wird vom Updategram ignoriert.  
  
-   Wenn Sie ein XSD-Schema erstellen und der Wert, den Sie für die `sql:relation`- oder die `sql:field`-Anmerkung erstellen ein Sonderzeichen enthält, wie zum Beispiel ein Leerzeichen (etwa im Tabellennamen "Details Bestellung"), muss dieser Wert in Klammern eingeschlossen werden (beispielsweise, "[Details Bestellung]").  
  
-   Wenn sie Updategrams verwenden, werden Kettenbeziehungen nicht unterstützt. Wenn beispielsweise die Tabellen A und C über eine Kettenbeziehung miteinander verknüpft sind, die Tabelle B verwendet, tritt der folgende Fehler auf, wenn Sie versuchen, das Updategram auszuführen:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Auch wenn Schema und Updategram ansonsten korrekt und gültig sind, tritt dieser Fehler auf, wenn eine Kettenbeziehung vorhanden ist.  
  
-   Updategrams erlauben nicht das Weitergeben von Daten vom Typ `image` als Parameter während eines Updates.  
  
-   BLOB-Typen (Binary Large Object) wie `text/ntext` und-Bilder sollten beim Arbeiten mit Update grams nicht im-Block verwendet werden, da diese in der Parallelitäts **\<before>** Steuerung enthalten sind. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Das gilt zum Beispiel für das LIKE-Schlüsselwort in der WHERE-Klausel zwischen Spalten des `text`-Datentyps. Vergleiche schlagen allerdings für BLOB-Typen fehl, deren Datengröße 8 K übersteigt.  
  
-   Sonderzeichen in `ntext`-Daten können aufgrund der Einschränkungen beim Vergleich von BLOB-Typen Probleme mit SQLXML 4.0 verursachen. Beispielsweise schlägt die Verwendung von "[serialisierbar]" im **\<before>** Block eines Update grams bei Verwendung bei der Parallelitäts Prüfung einer Spalte vom `ntext` Typ mit der folgenden SQLOLEDB-Fehlerbeschreibung fehl:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberlegungen zu Update grams &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
