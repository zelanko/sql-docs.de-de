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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: aad2036f5b72f268d09092a2761f7c1d2ab73456
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75254714"
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
  
  
