---
title: Leistungsprofilerstellung des ODBC-Treibers
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ed94b29d03fd2b95294bed28201b3bd3b63df45
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81281930"
---
# <a name="profiling-odbc-driver-performance-odbc"></a>Profilerstellung der ODBC-Treiberleistung (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügt über zwei treiberspezifische Optionen zur Profilerstellung für die Treiberleistung.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -ODBC-Treiber kann Leistungsstatistiken in einer Datei protokollieren. Die Protokolldatei ist eine durch Tabstopps getrennte Datei, die in jeder Tabellenkalkulation analysiert werden kann, die durch Tabstopps getrennte Dateien unterstützt, beispielsweise Microsoft Excel.  
  
 Der Treiber kann auch langwierige Abfragen protokollieren (Abfragen, die innerhalb eines gewissen Zeitraums keine Antwort vom Server erhalten). Diese Abfragen können später von Programmierern und Datenbankadministratoren analysiert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Leistungsdaten des Profil Treibers &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data.md)  
  
-   [Protokollieren von Abfragen mit langer Ausführungszeit &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC How-to Topics](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
  
