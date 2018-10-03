---
title: ErrorControl-Eigenschaft (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- ErrorControl Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cc70c05346bd246dc5a8b46ae1477eb65305f0b3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751695"
---
# <a name="errorcontrol-property-sqlservice-class"></a>ErrorControl-Eigenschaft (SqlService-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft ab den Schweregrad des Fehlers ab, wenn der Dienst beim Hochfahren nicht gestartet wird, oder ruft diesen ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Zeichenfolgenwert der den gemeldeten Schweregrad des Fehlers angibt, wenn der beim Hochfahren des Diensts ein Fehler auftritt. In der folgenden Tabelle sind die möglichen Werte aufgeführt.  
  
 Ignorieren  
 Der Benutzer wird nicht benachrichtigt.  
  
 Normal  
 Der Benutzer wird benachrichtigt.  
  
 Schwer  
 Das System wird mit der letzten bekannten, fehlerfreien Konfiguration neu gestartet.  
  
 Kritisch  
 Das System versucht, mit einer fehlerfreien Konfiguration zu neu starten.  
  
 Unknown  
 Der Schweregrad ist unbekannt.  
  
## <a name="remarks"></a>Hinweise  
 Der Wert gibt die vom Startprogramm ausgeführte Aktion an, wenn ein Fehler auftritt. Alle Fehler werden vom Computersystem protokolliert.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
