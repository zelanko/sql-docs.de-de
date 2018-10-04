---
title: RemoveCertificate-Methode (SInstance-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- RemoveCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 7e5dbafa-a634-4617-9622-510514fce0ce
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d172f7e8e14eba76b066cb815f5d99b8e912ba9e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122752"
---
# <a name="removecertificate-method-sinstance-class"></a>RemoveCertificate-Methode (SInstance-Klasse)
  Entfernt das aktuelle Sicherheitszertifikat aus der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.RemoveCertificate()  
  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SInstance-Klassenobjekt](sinstance-class.md) , das die Servereinstellungen in einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32-Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
