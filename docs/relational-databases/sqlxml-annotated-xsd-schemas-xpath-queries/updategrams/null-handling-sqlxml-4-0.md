---
title: NULL-Behandlung (SQLXML)
description: 'Erfahren Sie, wie NULL-Attribute oder-Elemente in einem SQLXML 4,0-Update Gram mithilfe des updg: nullValue-Attributs angegeben werden können.'
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7944369c409975eba2331fe12b55ec873dda61fd
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84882167"
---
# <a name="null-handling-sqlxml-40"></a>Behandlung von NULL (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XML-Syntax deutet NULL als eine Abwesenheit. (Beispiel: Wenn ein Attribut-oder Elementwert NULL ist, ist dieses Attribut oder Element im XML-Dokument nicht vorhanden.) In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML ermöglicht das **updg: NullValue** -Attribut das Angeben von NULL für einen Element-oder Attribut Wert.  
  
 Das folgende Update Gram stellt z. b. sicher, dass der **Titelwert** für einen Kontakt mit der **ContactID** 64 NULL ist, und aktualisiert dann den **Title** -Wert auf "Mr." auf "Mr.".  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Wenn Parameter an ein Updategram übergeben werden, kann NULL als Parameterwert übergeben werden. Dies erfolgt durch Angabe des **NullValue** -Attributs im- **\<updg:header>** Block. Ein Beispiel finden Sie unter [übergeben von Parametern an Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberlegungen zu Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
