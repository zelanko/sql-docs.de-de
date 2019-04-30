---
title: MoveFirst, MoveLast, MoveNext und MovePrevious-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- MoveLast method [RDS]
- MovePrevious method [RDS]
- MoveFirst method [RDS]
- MoveNext method [RDS]
ms.assetid: 45c80bb5-136f-4204-9df2-78740fa55574
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3afc55ca26a8462eb5662287288ee885f9104a8c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225834"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-rds"></a>MoveFirst-, MoveLast-, MoveNext- und MovePrevious-Methode (RDS)
Wechselt zum ersten, letzten, nächsten oder vorherigen Datensatz in einem angegebenen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.Recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objektvariable, steht ein [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Können Sie die **verschieben** Methoden mit dem **RDS. DataControl** Objekt, das durch die Datensätze in den datengebundenen Steuerelementen auf einer Webseite navigieren. Nehmen wir beispielsweise an, die Sie anzeigen, eine **Recordset** in einem Raster durch Bindung an eine **RDS. DataControl** Objekt. Sie können dann einschließen ersten, letzten, nächsten und zurück-Schaltflächen, die Benutzer, um die Umstellung auf das erste, letzte, Weiter klicken können, oder vorherigen Datensatz in die angezeigten **Recordset**. Rufen Sie dazu die **MoveFirst**, **MoveLast**, **MoveNext**, und **MovePrevious** Methoden der **RDS. DataControl** bzw. in den OnClick-Verfahren für die ersten, letzten, nächsten und zurück-Schaltflächen, Objekt. Die [Adressbuch Beispiel](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md) veranschaulicht dies.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Move-Methode (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext und MovePrevious-Methode (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveRecord-Methode (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)


