---
title: SetStartMode-Methode (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 61115113b3f710b9853f66e4437783755b886d64
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85013807"
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
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](sqlservice-class.md) , das den Dienst darstellt.  
  
#### <a name="parameters"></a>Parameter  
 *StartMode*  
 Ein `uint32`-Wert, der den Startmodus der Dienstinstanz angibt.  
  
 Die folgenden Werte sind gültig:  
  
 Wert = 0. Neustart: Der Dienst wurde durch das Betriebssystemladeprogramm gestartet. Dieses Wert ist nur für Treiberdienste gültig.  
  
 Wert = 1. System: Der Gerätetreiber wurde durch die `IoInitSystem`-Methode gestartet. Dieses Wert ist nur für Treiberdienste gültig.  
  
 Wert = 2. Automatisch: Der Dienst soll während des Systemstarts automatisch vom Dienstkontroll-Manager gestartet werden.  
  
 Wert = 3. Manuell: Der Dienst soll vom Computer-Manager gestartet werden, wenn ein Prozess die `StartService`-Methode aufruft.  
  
 Wert = 4. Deaktiviert: Der Dienst kann nicht mehr gestartet werden.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird. Jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
