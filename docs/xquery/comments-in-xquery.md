---
title: Kommentare in XQuery | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- comments [XQuery]
- XQuery, comments
ms.assetid: 4d977268-de9d-4bf0-b310-b63f6a0fb0db
author: rothja
ms.author: jroth
ms.openlocfilehash: a2c5adad052a33dc4d8b86b488ca1cc44737790e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039021"
---
# <a name="comments-in-xquery"></a>Kommentare in XQuery
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Sie können Kommentare zu XQuery hinzufügen. Die Kommentarzeichenfolgen werden mithilfe der Trennzeichen "`(:`" und "`:)`" hinzugefügt. Beispiel:  
  
```  
declare @x xml  
set @x=''  
SELECT @x.query('  
(: simple query to construct an element :)  
<ProductModel ProductModelID="10" />  
')  
```  
  
 Im folgenden finden Sie ein weiteres Beispiel, in dem eine Abfrage für eine Anweisungs Spalte des **XML** -Typs angegeben wird:  
  
```  
SELECT Instructions.query('  
(: declare prefix and namespace binding in the prolog. :)  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  (: Following expression retrieves the <Location> element children of the <root> element. :)  
  /AWMI:root/AWMI:Location  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
  
