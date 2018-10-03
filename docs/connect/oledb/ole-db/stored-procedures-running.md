---
title: Ausführen von gespeicherten Prozeduren (OLE DB) | Microsoft-Dokumentation
description: Ausführen von gespeicherten Prozeduren (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- OLE DB Driver for SQL Server, stored procedures
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: a016e7c0d6ffb59b01ab679bbe21029558f7966b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830788"
---
# <a name="stored-procedures---running"></a>Gespeicherte Prozeduren: Ausführen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Wenn beim Ausführen von Anweisungen eine gespeicherte Prozedur in der Datenquelle ausgeführt wird (anstelle der Ausführung oder der Vorbereitung einer Anweisung direkt in der Clientanwendung), kann dies folgende Vorteile haben:  
  
-   Bessere Leistung  
  
-   Geringere Netzwerkbelastung  
  
-   Bessere Konsistenz  
  
-   Eine höhere Genauigkeit.  
  
-   Zusätzliche Funktionalität  
  
 Der OLE DB-Treiber für SQL Server unterstützt drei der Mechanismen, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gespeicherte Prozeduren verwenden, um Daten zurückzugeben:  
  
-   Jede SELECT-Anweisung in der Prozedur generiert ein Resultset.  
  
-   Die Prozedur kann Daten über Ausgabeparameter zurückgeben.  
  
-   Die Prozedur kann einen ganzzahligen Rückgabecode besitzen.  
  
 Die Anwendung muss diese Ausgaben von gespeicherten Prozeduren verwenden können.  
  
 Die Rückgabe von Ausgabeparametern und Rückgabewerten erfolgt bei verschiedenen OLE DB-Anbietern zu unterschiedlichen Zeitpunkten während der Ergebnisverarbeitung. Der OLE DB-Treiber für SQL Server stellt die Ausgabeparameter und Rückgabecodes beispielsweise erst bereit, nachdem der Consumer die durch die gespeicherte Prozedur zurückgegebenen Resultsets abgerufen oder abgebrochen hat. Die Rückgabecodes und die Ausgabeparameter werden im letzten TDS-Paket vom Server zurückgegeben.  
  
 Anbieter verwenden die DBPROP_OUTPUTPARAMETERAVAILABILITY-Eigenschaft, um die Rückgabe von Ausgabeparametern und Rückgabewerten zu melden. Bei dieser Eigenschaft handelt es sich um den DBPROPSET_DATASOURCEINFO-Eigenschaftensatz.  
  
 Der OLE DB-Treiber für SQL Server legt die DBPROP_OUTPUTPARAMETERAVAILABILITY-Eigenschaft auf DBPROPVAL_OA_ATROWRELEASE fest, um anzugeben, dass Rückgabecodes und Ausgabeparameter erst zurückgegeben werden, nachdem das Resultset verarbeitet oder freigegeben wurde.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Gespeicherte Prozeduren](../../oledb/ole-db/stored-procedures.md)  
  
  
