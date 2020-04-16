---
title: XQuery-Sprachreferenz (SQL Server) | Microsoft Docs
description: Erfahren Sie mehr über die XQuery-Sprache für SQL Server, und zeigen Sie eine vollständige Sprachreferenz an.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
helpviewer_keywords:
- XQuery
- XQuery, about XQuery
- xml data type [SQL Server], XQuery
- XML [SQL Server], XQuery
- queries [XML in SQL Server], XQuery
ms.assetid: 8a69344f-2990-4357-8160-cb26aac95b91
author: rothja
ms.author: jroth
ms.openlocfilehash: 35a1418e416e32ab5b8dc9647c4a9aa24700b624
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388615"
---
# <a name="xquery-language-reference-sql-server"></a>XQuery-Sprachreferenz (SQL Server)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../includes/tsql-md.md)]unterstützt eine Teilmenge der XQuery-Sprache, die zum Abfragen des **XML-Datentyps** verwendet wird. Diese XQuery-Implementierung orientiert sich am Arbeitsentwurf für XQuery (Juli 2004). Diese Sprache wird zurzeit vom W3C (World Wide Web Consortium) unter Mitwirkung aller großen Datenbankhersteller und Microsoft entwickelt. Da die W3C-Spezifikationen möglicherweise überarbeitet werden, bevor eine W3C-Empfehlung ausgesprochen wird, kann sich diese Implementierung von der endgültigen Empfehlung unterscheiden. Dieses Thema beschreibt die Semantik und Syntax der Teilmenge von XQuery, die in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt wird.  
  
 Weitere Informationen finden Sie in der [W3C XQuery 1.0-Sprachspezifikation](https://go.microsoft.com/fwlink/?LinkId=48846).  
  
 XQuery ist eine Sprache, die strukturierte oder halbstrukturierte XML-Daten abfragen kann. Mit der **xml-Datentypunterstützung,** die [!INCLUDE[ssDE](../includes/ssde-md.md)]im bereitgestellt wird, können Dokumente in einer Datenbank gespeichert und dann mithilfe von XQuery abgefragt werden.  
  
 XQuery basiert auf der vorhandenen XPath-Abfragesprache. Dieser wurde Unterstützung für bessere Iteration, bessere Sortierergebnisse und eine Funktion zum Erstellen des erforderlichen XML hinzugefügt. XQuery wird auf der Grundlage des XQuery-Datenmodells ausgeführt. Dabei handelt es sich um eine Abstraktion von XML-Dokumenten und die XQuery-Ergebnisse, die typisiert oder nicht typisiert sein können. Die Typinformationen basieren auf den von der W3C XML-Schemasprache bereitgestellten Typen. Wenn keine Typisierungsinformationen verfügbar sind, behandelt XQuery die Daten so, als wären sie nicht typisiert. XPath, Version 1.0, verarbeitet XML auf ähnliche Weise.  
  
 Um eine XML-Instanz abzufragen, die in einer Variablen oder Spalte des **XML-Typs** gespeichert ist, verwenden Sie die [xml Data Type Methods](../t-sql/xml/xml-data-type-methods.md). Sie können z. B. eine Variable des **XML-Typs** deklarieren und abfragen, indem Sie die **query()-Methode** des **XML-Datentyps** verwenden.  
  
```sql
DECLARE @x xml  
SET @x = '<ROOT><a>111</a></ROOT>'  
SELECT @x.query('/ROOT/a')  
```  
  
 Im folgenden Beispiel wird die Abfrage für die Spalte Anweisungen des **XML-Typs** in der Tabelle ProductModel in der AdventureWorks-Datenbank angegeben.  
  
```sql
SELECT Instructions.query('declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Die XQuery enthält die `declare namespace``AWMI=...`Namespacedeklaration `/AWMI:root/AWMI:Location[@LocationID=10]`, und den Abfrageausdruck , .  
  
 Beachten Sie, dass xQuery für die Spalte Instructions vom **Xml-Typ** angegeben wird. Die [query()-Methode](../t-sql/xml/query-method-xml-data-type.md) des XML-Datentyps wird verwendet, um die XQuery anzugeben.  
  
 Die folgende Tabelle enthält die verwandten Themen, die das Verständnis der Implementierung von XQuery in [!INCLUDE[ssDE](../includes/ssde-md.md)] vertiefen sollen.  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[XML-Daten &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)|Erläutert die Unterstützung für den [!INCLUDE[ssDE](../includes/ssde-md.md)] **XML-Datentyp**in der und die Methoden, die Sie für diesen Datentyp verwenden können. Der **XML-Datentyp** bildet das Eingabe-XQuery-Datenmodell, auf dem die XQuery-Ausdrücke ausgeführt werden.|  
|[XML-Schemaauflistungen &#40;SQL Server&#41;](../relational-databases/xml/xml-schema-collections-sql-server.md)|Beschreibt, wie die in einer Datenbank gespeicherten XML-Instanzen typisiert werden können. Dies bedeutet, dass Sie der **XML-Typspalte** eine XML-Schemaauflistung zuordnen können. Alle in der Spalte gespeicherten Instanzen werden in der Auflistung anhand des Schemas überprüft und typisiert und stellen die Typinformationen für XQuery bereit.|  
|||  
  
> [!NOTE]  
>  Die Organisation dieses Abschnitts basiert auf der Arbeitsentwurfspezifikation für XQuery des World Wide Web Consortium (W3C). Einige der in diesem Abschnitt bereitgestellten Diagramme stammen aus dieser Spezifikation. In diesem Abschnitt wird die Microsoft XQuery-Implementierung mit der W3C-Spezifikation verglichen, es werden die Unterschiede zwischen XQuery und W3C beschrieben und die nicht unterstützten W3C-Funktionen genannt. Die W3C-Spezifikation [http://www.w3.org/TR/2004/WD-xquery-20040723](https://go.microsoft.com/fwlink/?LinkId=48846)ist verfügbar unter .  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[XQuery-Grundlagen](../xquery/xquery-basics.md)|Stellt eine grundlegende Übersicht über die XQuery-Konzepte und die Auswertung von Ausdrücken (statischer und dynamischer Kontext), die Atomarmachung, effektive boolesche Werte, das XQuery-Typsystem, Sequenztypzuordnung und Fehlerbehandlung zur Verfügung.|  
|[XQuery-Ausdrücke](../xquery/xquery-expressions.md)|Beschreibt primäre XQuery-Ausdrücke, path-Ausdrücke, sequence-Ausdrücke, arithmetische Vergleiche und logische Ausdrücke, die XQuery-Erstellung, FLWOR-Ausdrücke, bedingte und quantifizierte Ausdrücke sowie verschiedene Ausdrücke für Sequenztypen.|  
|[Module und Prologs &#40;XQuery&#41;](../xquery/modules-and-prologs-xquery.md)|Beschreibt den XQuery-Prolog.|  
|[XQuery-Funktionen für den xml-Datentyp](../xquery/xquery-functions-against-the-xml-data-type.md)|Beschreibt eine Liste der unterstützten XQuery-Funktionen.|  
|[XQuery-Operatoren für den xml-Datentyp](../xquery/xquery-operators-against-the-xml-data-type.md)|Beschreibt unterstützte XQuery-Operatoren.|  
|[Zusätzliches Beispiel für XQuery-Abfragen für den XML-Datentyp](../xquery/additional-sample-xqueries-against-the-xml-data-type.md)|Stellt zusätzliche XQuery-Beispiele bereit.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Daten &#40;SQL Server-&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XML-Schemasammlungen &#40;SQL Server-&#41;](../relational-databases/xml/xml-schema-collections-sql-server.md)   
 [Beispiele für den Massenimport und -export von XML-Dokumenten &#40;SQL Server&#41;](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
  
