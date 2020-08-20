---
description: GetCurrentCertificate-Methode (SInstance-Klasse)
title: GetCurrentCertificate-Methode (SInstance)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- GetCurrentCertificate Method (SInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 9d2b72df-cb21-414a-abef-917f13d4de62
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 28f413d6869fde5eb62f7ab9d1f8ef6e8b28cac4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472794"
---
# <a name="getcurrentcertificate-method-sinstance-class"></a>GetCurrentCertificate-Methode (SInstance-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft das aktuelle Sicherheitszertifikat ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.GetCurrentCertificate(SHA)  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SInstance-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sinstance-class/sinstance-class.md) , das die Servereinstellungen in einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*SHA*|Ein Zeichenfolgen-Objektwert (Ausgabeparameter), das das aktuelle Sicherheitszertifikat nach Abschluss der Methode angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
