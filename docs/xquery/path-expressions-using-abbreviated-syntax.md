---
title: Abgekürzte Syntax in einem Pfadausdruck in mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- abbreviated syntax [XQuery]
ms.assetid: f83c2e41-5722-47c3-b5b8-bf0f8cbe05d3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ee9a48b4bec625e4d64caf20aa1b5c8eaefe34f3
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51660399"
---
# <a name="path-expressions---using-abbreviated-syntax"></a>Pfadausdrücke – Verwenden abgekürzter Syntax
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Alle Beispiele in [Understanding the Path Expressions in XQuery](../xquery/path-expressions-xquery.md) verwenden abgekürzte Syntax für Path-Ausdrücke. Die ungekürzte Syntax für einen Achsenschritt in einem Pfadausdruck umfasst den Achsennamen und den Knotentest, getrennt durch einen Doppelpunkt und gefolgt von null oder mehr Schrittqualifizierern.  
  
 Zum Beispiel:  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 XQuery unterstützt die folgenden Abkürzungen für die Verwendung in path-Ausdrücken:  
  
-   Die **untergeordneten** -Achse ist die Standardachse. Aus diesem Grund die **untergeordneten::** Achse in einem Schritt in einem Ausdruck ausgelassen werden kann. So kann z. B. `/child::ProductDescription/child::Summary` als `/ProductDescription/Summary` geschrieben werden.  
  
-   Ein **Attribut** -Achse kann abgekürzt werden, als @. So kann z. B. `/child::ProductDescription[attribute::ProductModelID=10]` als `/ProudctDescription[@ProductModelID=10]` geschrieben werden.  
  
-   Ein **/descendant-or-self::node()/** kann abgekürzt werden zu / /. So kann z. B. `/descendant-or-self::node()/child::act:telephoneNumber` als `//act:telephoneNumber` geschrieben werden.  
  
     Die vorherige Abfrage ruft alle Rufnummern ab, die in der AdditionalContactInfo-Spalte in der Contact-Tabelle gespeichert sind. Das Schema für AdditionalContactInfo wird so definiert, die eine \<TelephoneNumber >-Element kann an beliebiger Stelle im Dokument. Aus diesem Grund müssen Sie zum Abrufen aller Rufnummern jeden Knoten im Dokument durchsuchen. Die Suche beginnt im Stamm des Dokuments und wird dann über alle nachfolgenden Knoten fortgesetzt.  
  
     Die folgende Abfrage ruft alle Rufnummern für einen bestimmten Kundenkontakt ab:  
  
    ```  
    SELECT AdditionalContactInfo.query('             
                declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";             
                declare namespace crm="https://schemas.adventure-works.com/Contact/Record";             
                declare namespace ci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";             
                /descendant-or-self::node()/child::act:telephoneNumber             
                ') as result             
    FROM Person.Contact             
    WHERE ContactID=1             
    ```  
  
     Wenn Sie den Pfadausdruck durch die abgekürzte Syntax `//act:telephoneNumber` ersetzen, können Sie die gleichen Ergebnisse erzielen.  
  
-   Die **Self::node()** in einem Schritt kann zu einem einzelnen Punkt (.) abgekürzt werden. Der Punkt ist jedoch nicht äquivalent oder austauschbar mit der **Self::node()**.  
  
     In der folgenden Abfrage stellt die Verwendung eines Punkts z. B. einen Wert und keinen Knoten dar:  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   Die **Parent::node()** in einem Schritt kann zu zwei Punkten (.) abgekürzt werden.  
  
  
