---
title: Datenquellen-Namen und die 64-Bit-Betriebssystemen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 323f2b89ac1af42038e1f6036ed5fea36edb8265
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396517"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Datenquellennamen und 64-Bit-Betriebssysteme
  Wenn Sie eine Anwendung als 32-Bit-Anwendung entwickeln und unter einem 64-Bit-Betriebssystem ausführen möchten, müssen Sie die ODBC-Datenquelle mit dem ODBC-Administrator in %windir%\SysWOW64\odbcad32.exe erstellen.  
  
## <a name="remarks"></a>Hinweise  
 Ein 64-Bit-Windows-Betriebssystem verfügt über zwei odbcad32.exe-Dateien:  
  
-   %SystemRoot%\system32\odbcad32.exe wird verwendet, um Datenquellennamen für 64-Bit-Anwendungen zu erstellen und zu warten.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe wird verwendet, um Datenquellennamen für 32-Bit-Anwendungen, einschließlich 32-Bit-Anwendungen, die auf 64-Bit-Betriebssystemen ausgeführt werden, zu erstellen und zu warten.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
