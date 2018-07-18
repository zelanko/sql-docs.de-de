---
title: SetStartMode-Methode (SqlService-Klasse) | Microsoft-Dokumentation
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
- SetStartMode Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
caps.latest.revision: 35
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7213e488b13b5b756e8632a55314c0fbbb5a8268
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278806"
---
# <a name="setstartmode-method-sqlservice-class"></a>SetStartMode-Methode (SqlService-Klasse)
  Ändert den Startmodus der Dienstinstanz.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetStartMode(  
StartMode  
)  
  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlService-Klassenobjekt](sqlservice-class.md) , das den Dienst darstellt.  
  
#### <a name="parameters"></a>Parameter  
 *StartMode*  
 Ein `uint32`-Wert, der den Startmodus der Dienstinstanz angibt.  
  
 Die folgenden Werte sind gültig:  
  
 Wert = 0. Neustart: Der Dienst wurde durch das Betriebssystemladeprogramm gestartet. Dieses Wert ist nur für Treiberdienste gültig.  
  
 Wert = 1. System: Der Gerätetreiber wurde durch die `IoInitSystem`-Methode gestartet. Dieses Wert ist nur für Treiberdienste gültig.  
  
 Wert = 2. Automatisch: Der Dienst soll während des Systemstarts automatisch vom Dienstkontroll-Manager gestartet werden.  
  
 Wert = 3. Manuell: der Dienst vom Computer-Manager gestartet werden soll, wenn ein Prozess Ruft die `StartService` Methode.  
  
 Wert = 4. Deaktiviert: Der Dienst kann nicht mehr gestartet werden.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird. Jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
