---
title: GetCurrentCertificate-Methode (ServerSettings-Klasse) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- GetCurrentCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 450e33c6-91d4-420f-ab7c-1905111f5658
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 269a2b5d29bce201d72ee6b42730e4cb42d61b78
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162878"
---
# <a name="getcurrentcertificate-method-serversettings-class"></a>GetCurrentCertificate-Methode (ServerSettings-Klasse)
  Ruft das aktuelle Sicherheitszertifikat ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.GetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein `ServerSettings` -Objekt, das die servereinstellungen in einer Instanz von darstellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Description|  
|---------------|-----------------|  
|*SHA*|Ein Zeichenfolgen-Objektwert (Ausgabeparameter), das das aktuelle Sicherheitszertifikat nach Abschluss der Methode angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32` Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert 1, wenn die Anforderung nicht unterstützt wird, wurde, und jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  