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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 953fc5b7c203faa8fa6a9820993a3d0fd7a7de40
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66014827"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Richtlinien und Einschränkungen von XML-Updategrams (SQLXML 4.0)
  Wenn Sie XML-Updategrams verwenden, sind folgende Überlegungen zu berücksichtigen:  
  
-   Wenn Sie ein Update Gram für einen Einfügevorgang mit nur einem Paar von ** \<vor>** und ** \<nach>** Blöcken verwenden, kann der ** \<before>** -Block ausgelassen werden. Umgekehrt kann bei einem Löschvorgang der ** \<after->** -Block ausgelassen werden.  
  
-   Wenn Sie ein Update Gram mit mehreren ** \<vor>** und ** \<nach>** Blöcken im ** \<Sync>** -Tag verwenden, müssen beide ** \<vor>** Blöcken und ** \<nach>** Blöcken vor ** \<>** und ** \<nach>** Paaren angegeben werden.  
  
-   Die Updates in einem Updategram werden auf die XML-Sicht angewendet, die vom XML-Schema bereitgestellt wird. Daher müssen Sie für eine erfolgreiche Standardzuordnung den Schemadateinamen im Updategram angeben. Falls der Dateiname nicht bereitgestellt wird, müssen die Element- und Attributnamen mit den Tabellen- und Spaltennamen in der Datenbank übereinstimmen.  
  
-   SQLXML 4.0 setzt voraus, dass alle Spaltenwerte in einem Updategram ausdrücklich im bereitgestellten Schema (XDR oder XSD) zugeordnet werden, um die XML-Sicht für die untergeordneten Elemente zu erstellen. Dieses Verhalten unterscheidet sich von früheren Versionen von SQLXML, die es zuließen, dass ein Wert für eine Spalte nicht im Schema zugeordnet war, wenn er als Teil eines Fremdschlüssels in einer `sql:relationship`-Anmerkung impliziert wurde. (Beachten Sie, dass sich diese Änderung nicht auf die Propagierung von Primärschlüsselwerten an untergeordnete Elemente auswirkt, was immer noch für SQLXML 4.0 gilt, wenn für das untergeordnete Element kein Wert ausdrücklich angegeben wird.)  
  
-   Wenn Sie ein Update Gram zum Ändern von Daten in einer binären Spalte (z. b. dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` Datentyp) verwenden, müssen Sie ein Zuordnungsschema bereit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellen, in dem der Datentyp (z. b. `sql:datatype="image"`) und der XML `dt:type="binhex"` - `dt:type="binbase64`Datentyp (z. b. oder) angegeben werden müssen. Die Daten für die binäre Spalte müssen im Updategram angegeben werden. Die `sql:url-encode`-Anmerkung, die im Zuordnungsschema angegeben wird, wird vom Updategram ignoriert.  
  
-   Wenn Sie ein XSD-Schema erstellen und der Wert, den Sie für die `sql:relation`- oder die `sql:field`-Anmerkung erstellen ein Sonderzeichen enthält, wie zum Beispiel ein Leerzeichen (etwa im Tabellennamen "Details Bestellung"), muss dieser Wert in Klammern eingeschlossen werden (beispielsweise, "[Details Bestellung]").  
  
-   Wenn sie Updategrams verwenden, werden Kettenbeziehungen nicht unterstützt. Wenn beispielsweise die Tabellen A und C über eine Kettenbeziehung miteinander verknüpft sind, die Tabelle B verwendet, tritt der folgende Fehler auf, wenn Sie versuchen, das Updategram auszuführen:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Auch wenn Schema und Updategram ansonsten korrekt und gültig sind, tritt dieser Fehler auf, wenn eine Kettenbeziehung vorhanden ist.  
  
-   Updategrams erlauben nicht das Weitergeben von Daten vom Typ `image` als Parameter während eines Updates.  
  
-   BLOB-Typen (Binary Large Object) `text/ntext` , wie-und-Bilder, sollten nicht in verwendet werden, ** \<bevor>** in beim Arbeiten mit Update grams verwendet wird, da Sie diese zur Verwendung in der Parallelitäts Steuerung enthalten. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Das gilt zum Beispiel für das LIKE-Schlüsselwort in der WHERE-Klausel zwischen Spalten des `text`-Datentyps. Vergleiche schlagen allerdings für BLOB-Typen fehl, deren Datengröße 8 K übersteigt.  
  
-   Sonderzeichen in `ntext`-Daten können aufgrund der Einschränkungen beim Vergleich von BLOB-Typen Probleme mit SQLXML 4.0 verursachen. Beispielsweise schlägt die Verwendung von "[serialisierbar]" im ** \<before->** Block eines Update grams bei Verwendung in der Parallelitäts Prüfung einer Spalte vom `ntext` Typ mit der folgenden SQLOLEDB-Fehlerbeschreibung fehl:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberlegungen zu Update grams &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
