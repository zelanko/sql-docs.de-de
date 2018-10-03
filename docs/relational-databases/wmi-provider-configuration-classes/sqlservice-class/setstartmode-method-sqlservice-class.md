---
title: SetStartMode-Methode (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- SetStartMode Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d6513b7f6e8ef99d18d407617c998831d1a8024d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644978"
---
# <a name="setstartmode-method-sqlservice-class"></a>SetStartMode-Methode (SqlService-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ändert den Startmodus der Dienstinstanz.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetStartMode(StartMode)  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
#### <a name="parameters"></a>Parameter  
 *StartMode*  
 Ein **uint32** -Wert, der den Startmodus der Dienstinstanz angibt.  
  
 Die folgenden Werte sind gültig:  
  
 Wert = 0. Neustart: Der Dienst wurde durch das Betriebssystemladeprogramm gestartet. Dieses Wert ist nur für Treiberdienste gültig.  
  
 Wert = 1. System: Der Gerätetreiber wurde durch die **IoInitSystem** -Methode gestartet. Dieses Wert ist nur für Treiberdienste gültig.  
  
 Wert = 2. Automatisch: Der Dienst soll während des Systemstarts automatisch vom Dienstkontroll-Manager gestartet werden.  
  
 Wert = 3. Manuell: Der Dienst soll vom Computer-Manager gestartet werden, wenn ein Prozess die **StartService** -Methode aufruft.  
  
 Wert = 4. Deaktiviert: Der Dienst kann nicht mehr gestartet werden.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird. Jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
