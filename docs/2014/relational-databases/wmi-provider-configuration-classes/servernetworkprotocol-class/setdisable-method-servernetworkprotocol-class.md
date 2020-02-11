---
title: Setdeaktiviert-Methode (ServerNetworkProtocol-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 0ebbe0c5-07ad-4a76-a918-e379930adf71
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 37a68a1dbc3a35ba4e72b173b1785efd1108241b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63143465"
---
# <a name="setdisable-method-servernetworkprotocol-class"></a>SetDisable-Methode (ServerNetworkProtocol-Klasse)
  Deaktiviert das Server-Netzwerkprotokoll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 Ein [ServerNetworkProtocol-Klasse] ServerNetworkProtocol-Class.MD)-Objekt, das das Netzwerkprotokoll darstellt, das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]von der Instanz von verwendet wird.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32-Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
