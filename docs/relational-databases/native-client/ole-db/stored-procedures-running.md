---
title: Ausführen gespeicherter Prozeduren (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3f01c5e43d7d451cbcdca30dd66cf2ca70227541
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305343"
---
# <a name="stored-procedures---running"></a>Gespeicherte Prozeduren: Ausführen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Wenn beim Ausführen von Anweisungen eine gespeicherte Prozedur in der Datenquelle ausgeführt wird (anstelle der Ausführung oder der Vorbereitung einer Anweisung direkt in der Clientanwendung), kann dies folgende Vorteile haben:  
  
-   Bessere Leistung  
  
-   Geringere Netzwerkbelastung  
  
-   Bessere Konsistenz  
  
-   Höhere Genauigkeit  
  
-   Zusätzliche Funktionalität  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt drei der Mechanismen, die gespeicherte Prozeduren zum Zurückgeben von Daten verwenden:  
  
-   Jede SELECT-Anweisung in der Prozedur generiert ein Resultset.  
  
-   Die Prozedur kann Daten über Ausgabeparameter zurückgeben.  
  
-   Die Prozedur kann einen ganzzahligen Rückgabecode besitzen.  
  
 Die Anwendung muss diese Ausgaben von gespeicherten Prozeduren verwenden können.  
  
 Die Rückgabe von Ausgabeparametern und Rückgabewerten erfolgt bei verschiedenen OLE DB-Anbietern zu unterschiedlichen Zeitpunkten während der Ergebnisverarbeitung. Im Fall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des Native Client OLE DB-Anbieters werden die Ausgabeparameter und Rückgabecodes erst bereitgestellt, nachdem der Consumer die von der gespeicherten Prozedur zurückgegebenen Resultsets abgerufen oder abgebrochen hat. Die Rückgabecodes und die Ausgabeparameter werden im letzten TDS-Paket vom Server zurückgegeben.  
  
 Anbieter verwenden die DBPROP_OUTPUTPARAMETERAVAILABILITY-Eigenschaft, um die Rückgabe von Ausgabeparametern und Rückgabewerten zu melden. Bei dieser Eigenschaft handelt es sich um den DBPROPSET_DATASOURCEINFO-Eigenschaftensatz.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter legt die DBPROP_OUTPUTPARAMETERAVAILABILITY-Eigenschaft auf DBPROPVAL_OA_ATROWRELEASE, um anzugeben, dass Rückgabecodes und Ausgabeparameter erst zurückgegeben werden, wenn das Resultset verarbeitet oder freigegeben wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
  
