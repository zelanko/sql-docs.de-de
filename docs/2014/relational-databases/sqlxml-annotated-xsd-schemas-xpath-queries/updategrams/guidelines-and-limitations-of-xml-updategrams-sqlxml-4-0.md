---
title: Richtlinien und Einschränkungen von XML-Updategrams (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a146124df2d215532b3da4b85a3a36123de2786f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52754722"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Richtlinien und Einschränkungen von XML-Updategrams (SQLXML 4.0)
  Wenn Sie XML-Updategrams verwenden, sind folgende Überlegungen zu berücksichtigen:  
  
-   Bei Verwendung ein Updategrams für einen Einfügevorgang mit nur ein einzelnes Paar von  **\<vor >** und  **\<nach >** Blöcke, die  **\<vor >** Block kann ausgelassen werden. Im Gegensatz dazu bei einem Löschvorgang der  **\<nach >** Block kann ausgelassen werden.  
  
-   Bei Verwendung ein Updategrams mit mehreren  **\<vor >** und  **\<nach >** , freigegebene Blöcke in der  **\<Sync >** zu markieren, beide  **\<vor >** Blöcke und  **\<nach >** Blöcke müssen angegeben werden, um Formular  **\<vor >** und  **\<nach >** Paare.  
  
-   Die Updates in einem Updategram werden auf die XML-Sicht angewendet, die vom XML-Schema bereitgestellt wird. Daher müssen Sie für eine erfolgreiche Standardzuordnung den Schemadateinamen im Updategram angeben. Falls der Dateiname nicht bereitgestellt wird, müssen die Element- und Attributnamen mit den Tabellen- und Spaltennamen in der Datenbank übereinstimmen.  
  
-   SQLXML 4.0 setzt voraus, dass alle Spaltenwerte in einem Updategram ausdrücklich im bereitgestellten Schema (XDR oder XSD) zugeordnet werden, um die XML-Sicht für die untergeordneten Elemente zu erstellen. Dieses Verhalten unterscheidet sich von früheren Versionen von SQLXML, die es zuließen, dass ein Wert für eine Spalte nicht im Schema zugeordnet war, wenn er als Teil eines Fremdschlüssels in einer `sql:relationship`-Anmerkung impliziert wurde. (Beachten Sie, dass sich diese Änderung nicht auf die Propagierung von Primärschlüsselwerten an untergeordnete Elemente auswirkt, was immer noch für SQLXML 4.0 gilt, wenn für das untergeordnete Element kein Wert ausdrücklich angegeben wird.)  
  
-   Wenn Sie ein Updategram verwenden, um Daten in einer binären Spalte zu ändern (z. B. die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` -Datentyp), müssen Sie ein Zuordnungsschema, in dem Angeben der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp (z. B. `sql:datatype="image"`) und den XML-Datentyp (z. B. `dt:type="binhex"`oder `dt:type="binbase64`) muss angegeben werden. Die Daten für die binäre Spalte müssen im Updategram angegeben werden. Die `sql:url-encode`-Anmerkung, die im Zuordnungsschema angegeben wird, wird vom Updategram ignoriert.  
  
-   Wenn Sie ein XSD-Schema erstellen und der Wert, den Sie für die `sql:relation`- oder die `sql:field`-Anmerkung erstellen ein Sonderzeichen enthält, wie zum Beispiel ein Leerzeichen (etwa im Tabellennamen "Details Bestellung"), muss dieser Wert in Klammern eingeschlossen werden (beispielsweise, "[Details Bestellung]").  
  
-   Wenn sie Updategrams verwenden, werden Kettenbeziehungen nicht unterstützt. Wenn beispielsweise die Tabellen A und C über eine Kettenbeziehung miteinander verknüpft sind, die Tabelle B verwendet, tritt der folgende Fehler auf, wenn Sie versuchen, das Updategram auszuführen:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Auch wenn Schema und Updategram ansonsten korrekt und gültig sind, tritt dieser Fehler auf, wenn eine Kettenbeziehung vorhanden ist.  
  
-   Updategrams erlauben nicht das Weitergeben von Daten vom Typ `image` als Parameter während eines Updates.  
  
-   Binary large Object (BLOB) Typen wie zum Beispiel `text/ntext` und Images sollten nicht verwendet werden, der  **\<vor >** -block in bei der Verwendung von Updategrams verwendet wird, da auf diese Weise für die Verwendung in der parallelitätssteuerung eingeschlossen werden. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Das gilt zum Beispiel für das LIKE-Schlüsselwort in der WHERE-Klausel zwischen Spalten des `text`-Datentyps. Vergleiche schlagen allerdings für BLOB-Typen fehl, deren Datengröße 8 K übersteigt.  
  
-   Sonderzeichen in `ntext`-Daten können aufgrund der Einschränkungen beim Vergleich von BLOB-Typen Probleme mit SQLXML 4.0 verursachen. Z. B. die Verwendung von "[Serializable]" in der  **\<vor >** -Block eines Updategrams, die bei der Verwendung in der parallelitätsprüfung einer Spalte vom `ntext` Typ mit der folgenden SQLOLEDB-fehlerbeschreibung fehl:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsüberlegungen zu Updategramms &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
