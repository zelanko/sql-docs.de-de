---
title: Verwenden von Updategrams zum Ändern von Daten in SQLXML 4.0
description: Anzeigen von Informationen und Beispielen zu Update Grams und deren Verwendung zum Ändern von Daten in SQLXML 4,0.
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
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c043425e8db0ce36776e8fec938e3b083d230c9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733652"
---
# <a name="using-updategrams-to-modify-data-in-sqlxml-40"></a>Verwenden von Updategrams zum Ändern von Daten in SQLXML 4.0
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Mithilfe eines Update grams oder der OPENXML-Funktion können Sie eine Datenbank in aus einem vorhandenen XML-Dokument ändern (einfügen, aktualisieren oder löschen) [!INCLUDE[tsql](../../../includes/tsql-md.md)] .  
  
 Dieser Abschnitt enthält Informationen über Updategrams und Beispiele für ihre Verwendung.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Einführung in Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/introduction-to-updategrams-sqlxml-4-0.md)  
 Stellt grundlegende Informationen und Beispiele für Updategrams bereit.  
  
 [Angeben eines Schemas mit Anmerkungen in einem Update Gram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)  
 Erklärt anhand von Beispielen die Zuordnungsschemas mit Anmerkungen in Updategrams.  
  
 [NULL-Behandlung &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/null-handling-sqlxml-4-0.md)  
 Beschreibt das Angeben von NULL für Element- und Attributwerte.  
  
 [Einfügen von Daten mit XML-Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
 Beschreibt anhand von Beispielen das Verwenden von Updategrams zum Einfügen von Daten.  
  
 [Löschen von Daten mit XML-Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/deleting-data-using-xml-updategrams-sqlxml-4-0.md)  
 Beschreibt anhand von Beispielen das Verwenden von Updategrams zum Löschen von Daten.  
  
 [Aktualisieren von Daten mit XML-Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/updating-data-using-xml-updategrams-sqlxml-4-0.md)  
 Beschreibt anhand von Beispielen das Verwenden von Updategrams zum Ändern vorhandener Daten.  
  
 [Übergeben von Parametern an Updategrams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md)  
 Beschreibt anhand von Beispielen das Weitergeben von Parametern an Updategrams.  
  
 [Behandeln von Parallelitäts Problemen in der Datenbank in Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/handling-database-concurrency-issues-in-updategrams-sqlxml-4-0.md)  
 Beschreibt die verschiedenen Ebenen des möglichen Schutzes für das Behandeln von Parallelitätsproblemen in Updategrams und stellt Beispiele bereit.  
  
 [Updategram-Beispielanwendungen &#40;SQLXML 4,0&#41;](https://msdn.microsoft.com/library/d2287e10-4007-4ba4-ad84-4e2b6adfede5)  
 Stellt Beispielanwendungen bereit, die Updategrams verwenden.  
  
 [Richtlinien und Einschränkungen von XML-Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/guidelines-and-limitations-of-xml-updategrams-sqlxml-4-0.md)  
 Listet einige wichtige Aspekte für das Arbeiten mit Updategrams auf.  
  
  
