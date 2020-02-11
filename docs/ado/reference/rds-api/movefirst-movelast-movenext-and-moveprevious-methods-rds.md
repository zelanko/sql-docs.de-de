---
title: "\"Muvefirst\", \"muvelast\", \"muvenext\" und \"muveprevious\" (RDS) | Microsoft-Dokumentation"
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
ms.openlocfilehash: 8e99ff17cad2bebcfaed509788ea3721ddfeb0ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963885"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-rds"></a>MoveFirst-, MoveLast-, MoveNext- und MovePrevious-Methode (RDS)
Wechselt zum ersten, letzten, nächsten oder vorherigen Datensatz in einem angegebenen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.Recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objekt Variable, die einen [RDS darstellt. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Move** -Methoden können mit RDS verwendet werden **. DataControl** -Objekt, um durch die Datensätze in den Daten gebundenen Steuerelementen auf einer Webseite zu navigieren. Nehmen Sie beispielsweise an, dass Sie ein **Recordset** in einem Raster durch Binden an einen **RDS anzeigen. DataControl** -Objekt. Sie können dann die Schaltflächen First, Last, Next und Previous einschließen, auf die Benutzer klicken können, um zum ersten, letzten, nächsten oder vorherigen Datensatz im angezeigten **Recordset**zu wechseln. Dies erreichen Sie, indem Sie die Methoden " **muvefirst**", " **muvelast**", " **muvenext**" und " **muveprevious** " des **RDS aufrufen. DataControl** -Objekt in den OnClick-Prozeduren für die Schaltflächen First, Last, Next und Previous. Das [Adressbuch Beispiel](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md) zeigt die Vorgehensweise.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Move-Methode (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [Muvefirst-, muvelast-, muvenext-und muveprevious-Methode (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveRecord-Methode (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)


