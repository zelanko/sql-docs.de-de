---
title: SetValue-Methode (ClientSettingsGeneralFlag-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetValue Method (ClientSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: 34443689-a0e0-4668-a811-17532c6fd271
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e53d7c31c702531e58f4f950e2053989d1f9de05
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067898"
---
# <a name="setvalue-method-clientsettingsgeneralflag-class"></a>SetValue-Methode (ClientSettingsGeneralFlag-Klasse)
  Legt alle Werte des Flags fest, auf das verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein Objekt der [ClientSettingsGeneralFlag-Klasse](clientsettingsgeneralflag-class.md) , das ein allgemeines Flag für die Servereinstellungen darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*Wert*|Ein boleescher Wert, der den Wert des Flags angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
