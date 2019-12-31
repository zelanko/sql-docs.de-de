---
title: Richtlinien und Einschränkungen von Update grams (SQLXML)
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9eb717968b191bb7d80f5d68542178bf32734b00
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75241296"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Richtlinien und Einschränkungen von XML-Updategrams (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Wenn Sie XML-Updategrams verwenden, sind folgende Überlegungen zu berücksichtigen:  
  
-   Wenn Sie ein Update Gram für einen Einfügevorgang mit nur einem Paar von ** \<vor>** und ** \<nach>** Blöcken verwenden, kann der ** \<before>** -Block ausgelassen werden. Umgekehrt kann bei einem Löschvorgang der ** \<after->** -Block ausgelassen werden.  
  
-   Wenn Sie ein Update Gram mit mehreren ** \<vor>** und ** \<nach>** Blöcken im ** \<Sync>** -Tag verwenden, müssen beide ** \<vor>** Blöcken und ** \<nach>** Blöcken vor ** \<>** und ** \<nach>** Paaren angegeben werden.  
  
-   Die Updates in einem Updategram werden auf die XML-Sicht angewendet, die vom XML-Schema bereitgestellt wird. Daher müssen Sie für eine erfolgreiche Standardzuordnung den Schemadateinamen im Updategram angeben. Falls der Dateiname nicht bereitgestellt wird, müssen die Element- und Attributnamen mit den Tabellen- und Spaltennamen in der Datenbank übereinstimmen.  
  
-   SQLXML 4.0 setzt voraus, dass alle Spaltenwerte in einem Updategram ausdrücklich im bereitgestellten Schema (XDR oder XSD) zugeordnet werden, um die XML-Sicht für die untergeordneten Elemente zu erstellen. Dieses Verhalten unterscheidet sich von früheren Versionen von SQLXML, die einen Wert für eine Spalte zugelassen haben, die im Schema nicht zugeordnet ist, wenn Sie als Teil des fremd Schlüssels in einer **SQL: Relationship** -Anmerkung impliziert wurde. (Beachten Sie, dass sich diese Änderung nicht auf die Propagierung von Primärschlüsselwerten an untergeordnete Elemente auswirkt, was immer noch für SQLXML 4.0 gilt, wenn für das untergeordnete Element kein Wert ausdrücklich angegeben wird.)  
  
-   Wenn Sie ein Update Gram zum Ändern von Daten in einer binären Spalte (z. b. dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **Image** Datentyp) verwenden, müssen Sie ein Zuordnungsschema angeben [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , in dem der Datentyp (z. b. **SQL: datatype = "Image"**) und der XML-Datentyp (z. b. **dt: Type = "BinHex"** oder **dt: Type =** Die Daten für die binäre Spalte müssen im Update Gram angegeben werden. die im Zuordnungsschema angegebene **SQL: url-encode-** Anmerkung wird vom Update Gram ignoriert.  
  
-   Wenn Sie ein XSD-Schema schreiben und der Wert, den Sie für die **SQL: Relation** -oder **SQL: Field** -Anmerkung angeben, ein Sonderzeichen (z. b. den Tabellennamen "Order Details") enthält, muss dieser Wert in eckige Klammern eingeschlossen werden (z. b. "[Order Details]").  
  
-   Wenn sie Updategrams verwenden, werden Kettenbeziehungen nicht unterstützt. Wenn beispielsweise die Tabellen A und C über eine Kettenbeziehung miteinander verknüpft sind, die Tabelle B verwendet, tritt der folgende Fehler auf, wenn Sie versuchen, das Updategram auszuführen:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Auch wenn Schema und Updategram ansonsten korrekt und gültig sind, tritt dieser Fehler auf, wenn eine Kettenbeziehung vorhanden ist.  
  
-   Updategrams erlauben das Übergeben von **Bildtyp** Daten als Parameter während der Aktualisierung nicht.  
  
-   BLOB-Typen (Binary Large Object) wie **Text/ntext** und Bilder sollten nicht in verwendet werden, ** \<bevor>** in bei der Arbeit mit Update grams blockiert wird, da Sie diese zur Verwendung in der Parallelitäts Steuerung enthalten. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Beispielsweise wird das LIKE-Schlüsselwort in der WHERE-Klausel für den Vergleich zwischen Spalten des **Text** -Datentyps verwendet. Vergleiche schlagen jedoch bei BLOB-Typen fehl, bei denen die Größe der Daten größer als 8K ist.  
  
-   Sonderzeichen in **ntext** -Daten können aufgrund der Einschränkungen beim Vergleich von BLOB-Typen Probleme mit SQLXML 4,0 verursachen. Beispielsweise schlägt die Verwendung von "[serialisierbar]" im ** \<before->** Block eines Update grams bei Verwendung bei der Parallelitäts Prüfung einer Spalte vom Typ " **ntext** " mit der folgenden SQLOLEDB-Fehlerbeschreibung fehl:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberlegungen zu Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
