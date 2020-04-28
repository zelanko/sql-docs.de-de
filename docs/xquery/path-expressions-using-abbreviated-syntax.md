---
title: Verwenden von abgekürzten Syntax in einem Pfad Ausdruck | Microsoft-Dokumentation
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
ms.openlocfilehash: 8e75db08f283631cf9b5daf064790786a1abc10f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67946418"
---
# <a name="path-expressions---using-abbreviated-syntax"></a>Pfadausdrücke – Verwenden abgekürzter Syntax
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Alle Beispiele zum [Verständnis der Pfad Ausdrücke in XQuery](../xquery/path-expressions-xquery.md) verwenden eine nicht abgekürzte Syntax für Pfad Ausdrücke. Die ungekürzte Syntax für einen Achsenschritt in einem Pfadausdruck umfasst den Achsennamen und den Knotentest, getrennt durch einen Doppelpunkt und gefolgt von null oder mehr Schrittqualifizierern.  
  
 Beispiel:  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 XQuery unterstützt die folgenden Abkürzungen für die Verwendung in path-Ausdrücken:  
  
-   Die unter **geordnete Achse ist die Standard Achse.** Daher kann die **Child::** -Achse in einem Schritt in einem Ausdruck ausgelassen werden. So kann z. B. `/child::ProductDescription/child::Summary` als `/ProductDescription/Summary` geschrieben werden.  
  
-   Eine **Attribut** Achse kann als @abgekürzt werden. So kann z. B. `/child::ProductDescription[attribute::ProductModelID=10]` als `/ProudctDescription[@ProductModelID=10]` geschrieben werden.  
  
-   Ein **/descendant-or-self:: node ()/** kann als//abgekürzt werden. So kann z. B. `/descendant-or-self::node()/child::act:telephoneNumber` als `//act:telephoneNumber` geschrieben werden.  
  
     Die vorherige Abfrage ruft alle Rufnummern ab, die in der AdditionalContactInfo-Spalte in der Contact-Tabelle gespeichert sind. Das Schema für AdditionalContactInfo wird so definiert, dass ein \<telefonienumber-> Element an beliebiger Stelle im Dokument angezeigt werden kann. Aus diesem Grund müssen Sie zum Abrufen aller Rufnummern jeden Knoten im Dokument durchsuchen. Die Suche beginnt im Stamm des Dokuments und wird dann über alle nachfolgenden Knoten fortgesetzt.  
  
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
  
-   Der **Self:: node ()-Knoten** in einem Schritt kann zu einem einzelnen Punkt (.) abgekürzt werden. Der Punkt ist jedoch nicht äquivalent oder austauschbar mit dem **Self:: node ()**.  
  
     In der folgenden Abfrage stellt die Verwendung eines Punkts z. B. einen Wert und keinen Knoten dar:  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   Der über **geordnete:: node ()** in einem Schritt kann zu einem doppelten Punkt (..) abgekürzt werden.  
  
  
