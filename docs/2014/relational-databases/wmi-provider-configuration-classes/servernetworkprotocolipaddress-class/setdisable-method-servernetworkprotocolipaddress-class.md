---
title: Setdeaktiviert-Methode (ServerNetworkProtocolIPAddress-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 7a7cc8cc-9fb8-4bf5-b483-2150d633ee10
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: adaa66fd04f6e3b6f97b4e4edc75d9a21ea4e31f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62643217"
---
# <a name="setdisable-method-servernetworkprotocolipaddress-class"></a>SetDisable-Methode (ServerNetworkProtocolIPAddress-Klasse)
  Deaktiviert die IP-Adresse.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Eine [ServerNetworkProtocolIPAddress-Klasse] ServerNetworkProtocolIPAddress-Class.MD)-Objekt, das eine IP-Adresse für das Netzwerkprotokoll in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]einer Instanz von darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32-Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
