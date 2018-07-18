---
title: 'Mithilfe von IRow:: GetColumns | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21046f1ab8c25a9f929f8e6cf95281e74c157ae6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430049"
---
# <a name="using-irowgetcolumns"></a>Verwenden von IRow::GetColumns
  Die **IRow** -Implementierung ermöglicht, vorwärts gerichtete sequenziellen Zugriff auf die Spalten. Sie können entweder alle Spalten in der Zeile mit einem einzigen Aufruf zugreifen **von IRow:: GetColumns** oder rufen Sie **von IRow:: GetColumns** mehrere Male auf, jedes Mal, wenn Sie mehrere Spalten in der Zeile zugreifen.  
  
 Die verschiedenen Aufrufe von **von IRow:: GetColumns** sollten sich nicht überschneiden. Angenommen, der erste Aufruf **von IRow:: GetColumns** Spalten 1, 2 und 3, der zweite Aufruf ruft **von IRow:: GetColumns** sollte für Spalten, 4, 5 und 6 aufrufen. Wenn spätere Aufrufe von **von IRow:: GetColumns** überlappen, ist das Statusflag (Dwstatus-Feld in der DBCOLUMNACCESS) auf DBSTATUS_E_UNAVAILABLE festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen einer einzelnen Zeile mit IRow](fetching-a-single-row-with-irow.md)  
  
  
