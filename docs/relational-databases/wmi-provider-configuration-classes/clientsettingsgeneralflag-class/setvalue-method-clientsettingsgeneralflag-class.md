---
description: SetValue-Methode (ClientSettingsGeneralFlag-Klasse)
title: SetValue-Methode (ClientSettingsGeneralFlag)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetValue Method (ClientSettingsGeneralFlag Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetValue method
ms.assetid: 34443689-a0e0-4668-a811-17532c6fd271
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ceab1e91f11cdb53ed157d595260b1fb448a453f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545300"
---
# <a name="setvalue-method-clientsettingsgeneralflag-class"></a>SetValue-Methode (ClientSettingsGeneralFlag-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Legt alle Werte des Flags fest, auf das verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetValue(Value)  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein Objekt der [ClientSettingsGeneralFlag-Klasse](../../../relational-databases/wmi-provider-configuration-classes/clientsettingsgeneralflag-class/clientsettingsgeneralflag-class.md) , das ein allgemeines Flag für die Servereinstellungen darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*Wert*|Ein boleescher Wert, der den Wert des Flags angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
