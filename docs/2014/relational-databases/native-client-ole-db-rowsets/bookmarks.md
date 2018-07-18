---
title: Lesezeichen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d09cd5421d34f1f84d0b61423ed898e7249cffa9
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417139"
---
# <a name="bookmarks"></a>Lesezeichen
  Lesezeichen können Consumer schnell auf eine Zeile zurück. Mit Lesezeichen können Consumer auf der Grundlage des Lesezeichenwerts beliebig auf Zeilen zugreifen. Die Lesezeichenspalte ist die Spalte 0 (null) im Rowset. Der Consumer legt den Wert des Felds dwFlag der Bindungsstruktur auf DBCOLUMNSINFO_ISBOOKMARK fest, um anzugeben, dass die Spalte als Lesezeichen verwendet wird. Der Consumer legt zudem die Rowseteigenschaft DBPROP_BOOKMARKS auf VARIANT_TRUE fest. Mit dieser Spalte 0 sein können, die in einem Rowset dargestellt werden. Die **IRowsetLocate:: GetRowsAt** Methode anschließend zum Abrufen von Zeilen, beginnend mit der Zeile, die als in einem Lesezeichen als Offset angegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Rowsets](rowsets.md)  
  
  
