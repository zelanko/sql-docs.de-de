---
description: ErrorControl-Eigenschaft (SqlService-Klasse)
title: ErrorControl-Eigenschaft (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ErrorControl Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6c0c802c236495a5de48c2617a76f4422e608fca
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545236"
---
# <a name="errorcontrol-property-sqlservice-class"></a>ErrorControl-Eigenschaft (SqlService-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft ab den Schweregrad des Fehlers ab, wenn der Dienst beim Hochfahren nicht gestartet wird, oder ruft diesen ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
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
  
 Unbekannt  
 Der Schweregrad ist unbekannt.  
  
## <a name="remarks"></a>Hinweise  
 Der Wert gibt die vom Startprogramm ausgeführte Aktion an, wenn ein Fehler auftritt. Alle Fehler werden vom Computersystem protokolliert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
