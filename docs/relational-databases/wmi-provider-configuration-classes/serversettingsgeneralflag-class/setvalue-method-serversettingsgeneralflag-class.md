---
title: SetValue-Methode (ServerSettingsGeneralFlag-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetValue Method (ServerSettingsGeneralFlag Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetValue method
ms.assetid: a889feac-c0e0-4635-b506-843863d86967
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ec0a215db84b8b1d8dbd2d12e603a365f6a54023
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68052672"
---
# <a name="setvalue-method-serversettingsgeneralflag-class"></a>SetValue-Methode (ServerSettingsGeneralFlag-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Legt alle Werte des Flags fest, auf das verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetValue(Value)  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [ServerSettingsGeneralFlag-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/serversettingsgeneralflag-class/serversettingsgeneralflag-class.md) , das ein allgemeines Flag für die Servereinstellungen darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*Wert*|Ein boleescher Wert, der den Wert des Flags angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
