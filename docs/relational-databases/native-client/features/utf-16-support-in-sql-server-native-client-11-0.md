---
title: UTF-16-Unterstützung
description: Erfahren Sie mehr über die Unterstützung für UTF-16 in einem Puffer fester Länge in SQL Server Native Client, beginnend mit SQL Server 2012.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 329749a838ff3f98ff19063eeb3e081d52a54d7f
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009826"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Unterstützung für UTF-16 in SQL Server Native Client 11.0
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]fügt **ssNoVersion** Native Client dem Puffer keinen hohen Ersatzzeichencodepunkt zu, wenn Sie beim Binden eines Spaltenergebnisses oder Ausgabeparameters einen Puffer fester Länge übergeben und das vor dem abschließenden Zeichen in den Puffer geschriebene **ssNoVersion** -Zeichen ein hoher Ersatzzeichencodepunkt eines Ersatzzeichenpaars und das nächste [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Zeichen ein niedriger Ersatzzeichencodepunkt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
