---
title: ErrorControl-Eigenschaft (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- ErrorControl Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 83955510a18a2fbc77be5aeb7005704852f0e4a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135880"
---
# <a name="errorcontrol-property-sqlservice-class"></a>ErrorControl-Eigenschaft (SqlService-Klasse)
  Ruft ab den Schweregrad des Fehlers ab, wenn der Dienst beim Hochfahren nicht gestartet wird, oder ruft diesen ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlService-Klassenobjekt](sqlservice-class.md) , das den Dienst darstellt.  
  
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
  
  
