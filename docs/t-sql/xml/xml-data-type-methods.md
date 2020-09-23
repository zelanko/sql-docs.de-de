---
description: xml-Datentypmethoden
title: xml-Datentypmethoden
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], methods
- methods [XML in SQL Server]
ms.assetid: d112b9c9-be9f-435c-a9e6-d21b65778fb7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6b139187edc98242b7b4efc03ebd53a71fe415f3
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91116562"
---
# <a name="xml-data-type-methods"></a>xml-Datentypmethoden
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Sie können die **xml**-Datentypmethoden verwenden, um eine in einer Variablen oder einer Spalte vom Typ **xml** gespeicherte XML-Instanz abzufragen. In den Themen in diesem Abschnitt wird die Verwendung der **xml**-Datentypmethoden beschrieben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[query&#40; &#41;-Methode &#40;xml-Datentyp&#41;](../../t-sql/xml/query-method-xml-data-type.md)|Beschreibt das Verwenden der query()-Methode zum Ausführen einer Abfrage über eine XML-Instanz.|  
|[value&#40; &#41;-Methode &#40;xml-Datentyp&#41;](../../t-sql/xml/value-method-xml-data-type.md)|Beschreibt das Verwenden der value()-Methode zum Abrufen eines Werts eines SQL-Typs aus einer XML-Instanz.|  
|[exist&#40; &#41;-Methode &#40;xml-Datentyp&#41;](../../t-sql/xml/exist-method-xml-data-type.md)|Beschreibt das Verwenden der exist()-Methode, um zu bestimmen, ob eine Abfrage ein nicht leeres Ergebnis zurückgibt.|  
|[modify&#40; &#41;-Methode &#40;xml-Datentyp&#41;](../../t-sql/xml/modify-method-xml-data-type.md)|Beschreibt das Verwenden der modify()-Methode, um für Updates [XML Data Modification Language &#40;XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)-Anweisungen festzulegen.|  
|[nodes&#40; &#41;-Methode &#40;xml-Datentyp&#41;](../../t-sql/xml/nodes-method-xml-data-type.md)|Beschreibt das Verwenden nodes()-Methode, um XML in mehrere Zeilen aufzuteilen, wodurch Teile von XML-Dokumenten in Rowsets übertragen werden.|  
|[Binding Relational Data Inside XML Data (Einbinden relationaler Daten in XML-Daten)](../../t-sql/xml/binding-relational-data-inside-xml-data.md)|Beschreibt, wie Sie Nicht-XML-Daten in XML binden können.|  
|[Guidelines for Using xml Data Type Methods (Richtlinien zum Verwenden von Methoden des xml-Datentyps)](../../t-sql/xml/guidelines-for-using-xml-data-type-methods.md)|Enthält Richtlinien zum Verwenden der **xml**-Datentypmethoden.|  
  
 Der Aufruf dieser Methoden erfolgt mit der benutzerdefinierten Typmethodenaufrufsyntax. Beispiel:  
  
```sql
SELECT XmlCol.query(' ... ')  
FROM Table  
```  
  
> [!NOTE]  
>  Die **xml**-Datentypmethoden **query()** , **value()** und **exist()** geben NULL zurück, wenn sie für eine NULL XML-Instanz ausgeführt werden. Außerdem gibt **modify()** nichts zurück, aber **nodes()** gibt Rowsets und ein leeres Rowset mit einer NULL-Eingabe zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichen von typisiertem XML mit nicht typisiertem XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Erstellen von Instanzen der XML-Daten](../../relational-databases/xml/create-instances-of-xml-data.md)  
  
  
