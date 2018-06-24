---
title: PropertyNumVal-Eigenschaft (ClientNetworkProtocolProperty-Klasse) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- PropertyNumVal Property (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyNumVal property
ms.assetid: 12b02d97-702b-434f-baf6-e49a6b2cd4de
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e737aaa1d5b224e096a7ae6f3f70b81884ba9f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049407"
---
# <a name="propertynumval-property-clientnetworkprotocolproperty-class"></a>PropertyNumVal-Eigenschaft (ClientNetworkProtocolProperty-Klasse)
  Ruft den numerischen Wert der aktuellen Eigenschaft ab, auf die durch den Wert der [PropertyIdx-Eigenschaft (ClientNetworkProtocolProperty-Klasse)](clientnetworkprotocolproperty-class.md) verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.PropertyNumVal [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [ClientNetworkProtocolProperty-Klassenobjekt](clientnetworkprotocolproperty-class.md) , das ein Attribut des vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendeten Netzwerkprotokolls darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein u`int32`-Wert, der den numerischen Wert der aktuellen Eigenschaft angibt.  
  
## <a name="remarks"></a>Hinweise  
  