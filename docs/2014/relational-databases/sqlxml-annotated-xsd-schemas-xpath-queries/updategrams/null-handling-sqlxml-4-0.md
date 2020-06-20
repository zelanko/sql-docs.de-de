---
title: NULL-Behandlung (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 430643e8a6c9bd3dd00b2763990645c6a162ee40
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047485"
---
# <a name="null-handling-sqlxml-40"></a>Behandlung von NULL (SQLXML 4.0)
  XML-Syntax deutet NULL als eine Abwesenheit. (Beispiel: Wenn ein Attribut-oder Elementwert NULL ist, ist dieses Attribut oder Element im XML-Dokument nicht vorhanden.) In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML ermöglicht das- `updg:nullvalue` Attribut die Angabe von NULL für einen Element-oder Attribut Wert.  
  
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
  
 Wenn Parameter an ein Updategram übergeben werden, kann NULL als Parameterwert übergeben werden. Dies wird erreicht, indem das `nullvalue`-Attribut im `<updg:header>`-Block angegeben wird. Ein Beispiel finden Sie unter [übergeben von Parametern an Update grams &#40;SQLXML 4,0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberlegungen zu Update grams &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
