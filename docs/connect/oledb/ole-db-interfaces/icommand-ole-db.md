---
title: ICommand (OLE DB) | Microsoft Docs
description: ICommand-Schnittstelle (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICommand [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 1fb757655c6369964822cd473a50f9633feb2ab8
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689843"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dieser Artikel beschreibt die OLE DB-Verhalten, die speziell für OLE DB-Treiber für SQL Server ist.  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 Das Einfügen von Daten, die größer als die Größe einer Spalte sind, führt in der Regel zu einem Fehler. In bestimmten Situationen wird zwar S_OK zurückgegeben, der *dwStatus* wird jedoch auf DBSTATUS_S_TRUNCATED festgelegt. Es im Allgemeinen tritt auf beim Einfügen von Daten mit Parametern, in denen die Spalte nicht groß genug zum Speichern der Daten ist, und **ICommandWithParameters:: SetParameterInfo** wurde nicht aufgerufen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)
  
  
