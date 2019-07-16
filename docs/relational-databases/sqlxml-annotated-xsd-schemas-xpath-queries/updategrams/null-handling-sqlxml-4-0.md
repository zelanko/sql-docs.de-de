---
title: NULL (SQLXML 4.0) behandeln | Microsoft-Dokumentation
ms.custom: ''
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 43d5235d8e82ff674abcaa00da8c20bdbedffa60
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018510"
---
# <a name="null-handling-sqlxml-40"></a>Behandlung von NULL (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XML-Syntax deutet NULL als eine Abwesenheit. (Z. B. wenn ein Attribut- oder Elementwert Wert NULL ist, das Attribut bzw. Element nicht vorhanden ist aus dem XML-Dokument.) In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, die **updg: NullValue** Attribut ermöglicht die Angabe von NULL für ein Element oder Attribut-Wert.  
  
 Z. B. das folgende Updategram stellt sicher, dass die **Titel** -Wert eines Kontakts mit **ContactID** von 64 NULL ist, und aktualisiert dann die **Titel** Wert auf "Mr." auf "Mr.".  
  
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
  
 Wenn Parameter an ein Updategram übergeben werden, kann NULL als Parameterwert übergeben werden. Dies erfolgt durch Angabe der **Nullvalue** -Attribut in der  **\<Updg:header >** Block. Ein Beispiel finden Sie unter [übergeben von Parametern an Updategrams &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsüberlegungen zu Updategramms &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
