---
title: Erstellen eines Rowsets mit IOpenRowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cd80b90a8c40551344773ab7c5e95a539c21eefb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73788994"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Erstellen eines Rowsets mit 'IopenRowset'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die **IOpenRowset:: OPENROWSET** -Methode mit den folgenden Einschränkungen:  
  
-   Eine Basistabelle oder -sicht muss in einer Datenbank-ID-Struktur angegeben sein, auf die der *pTableID*-Parameter zeigt.  
  
-   Das DBID-Element *eKind* muss DBKIND_NAME anzeigen.  
  
-   Das DBI-Element *uName* muss den Namen einer vorhandenen Basistabelle oder einer Ansicht als Unicode-Zeichenfolge angeben.  
  
-   Der *pIndexID*-Parameter von **OpenRowset** muss NULL sein.  
  
 Das Resultset von **IOpenRowset::OpenRowset** enthält ein einzelnes Rowset. Resultsets, die ein einzelnes Rowset enthalten, können [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Cursorn unterstützt werden. Die Cursorunterstützung ermöglicht dem Entwickler die Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Parallelitätsmechanismen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
