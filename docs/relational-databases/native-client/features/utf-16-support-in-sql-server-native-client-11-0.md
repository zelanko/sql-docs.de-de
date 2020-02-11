---
title: UTF-16-Unterstützung in SQL Server Native Client 11,0 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 44121856f1a60d293eba5dd3ac1ae9f7f16cf357
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73788005"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Unterstützung für UTF-16 in SQL Server Native Client 11.0
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]fügt **ssNoVersion** Native Client dem Puffer keinen hohen Ersatzzeichencodepunkt zu, wenn Sie beim Binden eines Spaltenergebnisses oder Ausgabeparameters einen Puffer fester Länge übergeben und das vor dem abschließenden Zeichen in den Puffer geschriebene **ssNoVersion** -Zeichen ein hoher Ersatzzeichencodepunkt eines Ersatzzeichenpaars und das nächste [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Zeichen ein niedriger Ersatzzeichencodepunkt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
