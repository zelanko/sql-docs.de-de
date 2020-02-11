---
title: Nächste Abruf Position | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 632622f985e363d87cd820729afb6f69826c903b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73788982"
---
# <a name="fetching-rows---next-fetch-position"></a>Abrufen von Zeilen – Nächste Abrufposition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verfolgt die nächste Abruf Position nach, sodass eine Sequenz von Aufrufen der **GetNextRows** -Methode (ohne überspringen, Richtungsänderungen oder zwischengeschaltete Aufrufe der **FindNextRow**-, **Seek**-oder **RestartPosition** -Methoden) das gesamte Rowset liest, ohne eine Zeile zu überspringen oder zu wiederholen. Die nächste Abrufposition wird entweder durch Aufrufen von **IRowset::GetNextRows**, **IRowset::RestartPosition** oder **IRowsetIndex::Seek** oder durch Aufrufen von **FindNextRow** mit einem NULL-Wert für *pBookmark* geändert. Das Aufrufen von **FindNextRow** mit einem *pBookmark*-Wert ungleich NULL beeinflusst die nächste Abrufposition nicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abrufen von Zeilen](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
  
