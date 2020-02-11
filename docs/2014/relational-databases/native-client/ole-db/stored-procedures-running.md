---
title: Ausführen gespeicherter Prozeduren (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0102fa66e65fa11f47eec9f49cd1fa90fb11f877
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62638765"
---
# <a name="running-stored-procedures-ole-db"></a>Ausführen von gespeicherten Prozeduren (OLE DB)
  Wenn beim Ausführen von Anweisungen eine gespeicherte Prozedur in der Datenquelle ausgeführt wird (anstelle der Ausführung oder der Vorbereitung einer Anweisung direkt in der Clientanwendung), kann dies folgende Vorteile haben:  
  
-   Bessere Leistung  
  
-   Geringere Netzwerkbelastung  
  
-   Bessere Konsistenz  
  
-   Bessere Genauigkeit.  
  
-   Zusätzliche Funktionalität  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt drei der Mechanismen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , die gespeicherte Prozeduren zum Zurückgeben von Daten verwenden:  
  
-   Jede SELECT-Anweisung in der Prozedur generiert ein Resultset.  
  
-   Die Prozedur kann Daten über Ausgabeparameter zurückgeben.  
  
-   Die Prozedur kann einen ganzzahligen Rückgabecode besitzen.  
  
 Die Anwendung muss diese Ausgaben von gespeicherten Prozeduren verwenden können.  
  
 Die Rückgabe von Ausgabeparametern und Rückgabewerten erfolgt bei verschiedenen OLE DB-Anbietern zu unterschiedlichen Zeitpunkten während der Ergebnisverarbeitung. Im Fall des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB Anbieters werden die Ausgabeparameter und Rückgabecodes erst bereitgestellt, wenn der Consumer die von der gespeicherten Prozedur zurückgegebenen Resultsets abgerufen oder abgebrochen hat. Die Rückgabecodes und die Ausgabeparameter werden im letzten TDS-Paket vom Server zurückgegeben.  
  
 Anbieter verwenden die DBPROP_OUTPUTPARAMETERAVAILABILITY-Eigenschaft, um die Rückgabe von Ausgabeparametern und Rückgabewerten zu melden. Bei dieser Eigenschaft handelt es sich um den DBPROPSET_DATASOURCEINFO-Eigenschaftensatz.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter legt die DBPROP_OUTPUTPARAMETERAVAILABILITY-Eigenschaft auf DBPROPVAL_OA_ATROWRELEASE fest, um anzugeben, dass Rückgabecodes und Ausgabeparameter erst zurückgegeben werden, wenn das Resultset verarbeitet oder freigegeben wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren](stored-procedures.md)  
  
  
