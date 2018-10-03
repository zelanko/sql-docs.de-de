---
title: Verwenden von Updategrams zum Ändern von Daten in SQLXML 4.0 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- data insertions [SQLXML]
- data deletions [SQLXML]
- updating data [SQLXML]
- modifying data [SQLXML]
- OPENXML function
- updategrams [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- modifying databases
- data modifications [SQLXML]
- deleting data
- inserting data
ms.assetid: b8b3b892-cb73-41d0-b945-bce148d81d9b
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f8d1c158b9bdd922deb069e6cc95a71dab0e24a2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650728"
---
# <a name="using-updategrams-to-modify-data-in-sqlxml-40"></a>Verwenden von Updategrams zum Ändern von Daten in SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Sie können ändern (einfügen, aktualisieren oder löschen) eine Datenbank in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aus einem vorhandenen XML-Dokument mithilfe eines Updategrams oder der OPENXML- [!INCLUDE[tsql](../../../includes/tsql-md.md)] Funktion.  
  
 Dieser Abschnitt enthält Informationen über Updategrams und Beispiele für ihre Verwendung.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Einführung in Updategrams &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/introduction-to-updategrams-sqlxml-4-0.md)  
 Stellt grundlegende Informationen und Beispiele für Updategrams bereit.  
  
 [Angeben eines Zuordnungsschemas in einem Updategram &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)  
 Erklärt anhand von Beispielen die Zuordnungsschemas mit Anmerkungen in Updategrams.  
  
 [NULL-Behandlung &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/null-handling-sqlxml-4-0.md)  
 Beschreibt das Angeben von NULL für Element- und Attributwerte.  
  
 [Einfügen von Daten mit XML-Updategrams &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
 Beschreibt anhand von Beispielen das Verwenden von Updategrams zum Einfügen von Daten.  
  
 [Löschen von Daten mit XML-Updategrams &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/deleting-data-using-xml-updategrams-sqlxml-4-0.md)  
 Beschreibt anhand von Beispielen das Verwenden von Updategrams zum Löschen von Daten.  
  
 [Aktualisieren von Daten mit XML-Updategrams &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/updating-data-using-xml-updategrams-sqlxml-4-0.md)  
 Beschreibt anhand von Beispielen das Verwenden von Updategrams zum Ändern vorhandener Daten.  
  
 [Übergeben von Parametern an Updategrams &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md)  
 Beschreibt anhand von Beispielen das Weitergeben von Parametern an Updategrams.  
  
 [Behandeln von Problemen mit der Datenbankparallelität in Updategramms &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/handling-database-concurrency-issues-in-updategrams-sqlxml-4-0.md)  
 Beschreibt die verschiedenen Ebenen des möglichen Schutzes für das Behandeln von Parallelitätsproblemen in Updategrams und stellt Beispiele bereit.  
  
 [Updategram-Beispielanwendungen &#40;SQLXML 4.0&#41;](http://msdn.microsoft.com/library/d2287e10-4007-4ba4-ad84-4e2b6adfede5)  
 Stellt Beispielanwendungen bereit, die Updategrams verwenden.  
  
 [Richtlinien und Einschränkungen von XML-Updategrams &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/guidelines-and-limitations-of-xml-updategrams-sqlxml-4-0.md)  
 Listet einige wichtige Aspekte für das Arbeiten mit Updategrams auf.  
  
  
