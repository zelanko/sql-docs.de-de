---
title: Nächste Fetch-Position | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8073ae8f08ce77f5112f6f93f3ef6bdd6a276d8a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298915"
---
# <a name="fetching-rows---next-fetch-position"></a>Abrufen von Zeilen – Nächste Abrufposition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter verfolgt die nächste Abrufposition, sodass eine Sequenz von Aufrufen der **GetNextRows-Methode** (ohne Überspringen, Richtungsänderungen oder dazwischen liegende Aufrufe der **SuchNextRow-,** **Seek-** oder **RestartPosition-Methoden)** das gesamte Rowset liest, ohne eine Zeile zu überspringen oder zu wiederholen. Die nächste Abrufposition wird entweder durch Aufrufen von **IRowset::GetNextRows**, **IRowset::RestartPosition** oder **IRowsetIndex::Seek** oder durch Aufrufen von **FindNextRow** mit einem NULL-Wert für *pBookmark* geändert. Das Aufrufen von **FindNextRow** mit einem *pBookmark*-Wert ungleich NULL beeinflusst die nächste Abrufposition nicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abrufen von Zeilen](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
  
